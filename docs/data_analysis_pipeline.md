# Data Survey Analysis Pipeline

## Introduction

Fundamentally, the data survey analysis pipeline is split into the following phases:

1) Calling the Google Forms API to retrieve the metadata for a particular year's form

2) Updating the rename (i.e. "common name") configuration file

3) Rebuilding the data tidying config

4) Applying the data tidying config to all the survey data files to generate a single longitudinal dataframe

5) Doing your specific analyses

## Calling the Google Forms API

The Google Forms API is called using the `google-forms-api` package. The metadata that is retrieved looks akin the following example for a particular field:

```json
        {
            "itemId": "3c5cb287",
            "title": "If you did not (or will not) transfer into a PhD, what specifically impacted your decision?",
            "questionItem": {
                "question": {
                    "questionId": "6cbc03ed",
                    "choiceQuestion": {
                        "type": "CHECKBOX",
                        "options": [
                            {
                                "value": "Have dependents to take care of"
                            },
                            {
                                "value": "Can't afford to live in Toronto"
                            },
                            {
                                "value": "Proceeding to professional school"
                            },
                            {
                                "value": "Long duration of PhD program in combination with the current level of funding"
                            },
                            {
                                "isOther": true
                            }
                        ]
                    }
                }
            }
        },
```

These are saved in the `data/google` directory as `Form_Metadata_YYYY_YY.json` where `YYYY_YY` is the academic years that the form was active for.


## Updating the Rename Configuration File

The next step is to make sense of which fields are common between the years. This is accomplished using a rename configuration file located at `/config/GRC_Rename_Config.yaml`. Here is what a typical entry looks like:

```yaml
  - name: scholarshipsMotive
    history:
      2017: null
      2018: null
      2019: What is your motivation to apply for scholarships/awards? (select all that apply)
      2020: What is your motivation to apply for scholarships/awards?
      2021: What is your motivation to apply for scholarships/awards?
      2022: What is your motivation to apply for scholarships/awards?
      2023: What is your motivation to apply for scholarships/awards?
```

The `name` field is the common name that will be used in the final longitudinal dataframe. The `history` field is a dictionary where the keys are the years and the values are the corresponding field names in the Google Form metadata. If the field was not present in a particular year, the value is `null`.

There will be specific service functions prepared in `/src/services/update_rename.py` that will auto-update the rename config file with the newest year pre-populated with a `null` value.

**THIS SHOULD BE UPDATED IN REAL-TIME AS NEW SURVERYS ARE BEING DEVELOPED BY THE TEAM. ASSIGN A PARTICULAR PERSON TO BE RESPONSIBLE FOR THIS TASK.**

## Rebuilding the Data Tidying Config

Using the metadata from the Google Forms API and the rename configuration file, the data tidying config can be rebuilt. Like the rename configuration file, this is located at `/config/GRC_Tidy_Config.yaml` . Here is what a typical entry looks like:

TODO

There are multiple operations that can be specified on the data. These are applied in the order that they are specified in the config file. The operations are:

- `PASSTHROUGH`: This operation does nothing. It is used to pass the data through to the next operation.
- `RENAME`: This operation renames the column to the common name specified in the rename configuration file.
- `REPLACE`: This operation replaces the values in the column with the specified values.
- `SPLIT_TO_WIDE`: This operation splits the column into multiple columns based on the specified delimiter. This is particularly used for checkbox fields, as the separator that Google uses is `", "`.
- `REGEX_EXTRACT_AND_REPLACE`: This operation extracts a series of text values from text fields using a regular expression and replaces the original text field with the extracted values. This is useful for syncing up data that used to be in text fields but are now in radio/dropdown fields.
- `ONE_HOT_ENCODE`: This operation one-hot encodes the column. This is useful for syncing up radio/dropdown fields that have changed over the years to become checkbox fields.
- `RENAME_ROWS`: This is a unique operation to grid-based fields. It renames the rows to the specified values. Note that this specifically targets the row names as they appear in the raw excel output, typically in the format `Main_Quesiton [Row_Name]`. The `Main_Question ` part is unaffected and should be handled by the `RENAME` operation. To avoid bugs **it is recommended to run this first and prior to the RENAME operation**

There will be specific service functions in `/src/services/build_tidy.py` prepared that will auto-update the tidy config file with the "best guess" series of operations that should be applied to the data for a particular year.

**IT SHOULD BE THE COLLECTIVE RESPONSIBILITY OF THE DATA ANALYSTS TO ENSURE THAT THE "BEST GUESS" OPERATIONS ARE APPROPRIATE TO THE DATA ANALYSIS AND TO ADJUST THE CONFIG AS NECESSARY MANUALLY. MANUAL CHANGES ALWAYS SUPERIMPOSE AUTOMATIC ONES.**

## Applying the Data Tidying Config

Once the data tidying config is set up, the data can be tidied using the `src/services/apply_tidy` service functions. The output will be a single longitudinal dataframe that can be used for analysis located in the `/data/cleaned/survey` directory.


## Doing Your Specific Analyses

This will be up to you, dear data analyst. Godspeed.
