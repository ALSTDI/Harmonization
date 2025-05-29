# Release Notes: Version 0.1.0

The first release of the ALS TDI-Answer ALS harmonized data focused on restructuring the data into the proper OMOP CDM structure and mapping a subset to standardized vocabularies. 

Each data set individually contributed to additional fields.  This file represents shared fields.

Final dataset version location:  

## Initial Mappings Shared Between the Two Data Sets:
- Demographics: YOB, sex, ethnic_category,racial_categories
- ALSFRS-R (ALSF dataset): all variables
- ALS Diagnosis: all variables, especially El Escorial critera
- Medical History: Family and personal history, genetic mutation (self-report), site of onset, date of symptom onset and diagnosis
- Drug Exposure: Medications and select supplements
- Mortality: date_death
- Measurements: labs including XXX
- Observation:  military service, industry, injury

## Timing

INSERT ANYTHING NOTEWORTHY ABOUT DATES, TIMINGS, AGES

For the Observation_period OMOP domain the observation_period_start_date is the first event date of the subject. The observation_period_end_date is the last event date of the subject, or the death date.
## CDM Summary Counts 
NEED TO BE UPDATED

|cdm_domain | Number of Person IDs  |Number of Records  |Primary Concept ID Field |# of <br> Unique Concepts |
|--------------------|:---------------:|:---------:|-------------------------------|:------------------------:|
|person              |              513|        513|N/A                            |                          |
|death               |                0|          0|N/A                            |                          |
|observation_period  |              513|        513|N/A                            |                          |
|visit_occurrence    |                0|          0|visit_occurrence_concept_id    |                         0|
|visit_detail        |                0|          0|visit_detail_concept_id        |                         0|
|condition_occurrence|              513|       1026|condition_occurrence_concept_id|                         2|
|procedure_occurrence|              374|       1049|procedure_occurrence_concept_id|                         4|
|measurement         |              513|     348128|measurement_concept_id         |                        14|
|observation         |              513|     273570|observation_concept_id         |                       100|
|specimen            |                0|          0|specimen_concept_id            |                         0|
|drug_exposure       |              366|        444|drug_exposure_concept_id       |                         1|
|device_exposure     |                0|          0|device_exposure_concept_id     |                         0|


## Summary of Source Data Mapped 
NEED TO BE UPDATED WITH SURVEY NAMES

|load_table_id           |Number of Person IDs |Number of Rows   |# Unique Concepts |# of Records <br> with Standard Concepts|
|------------------------|:---------------:|:-----------------:|:-----------------:|:----------------:|
|als                     |              513|               8221|                 16|             8,221|
|alsf                    |              513|             73,614|                 16|            68,373|
|asvt                    |              504|                504|                  2|               504|
|cm                      |              366|                444|                  1|               444|
|dsfl                    |              139|              1,110|                  2|             1,110|
|gst                     |              513|             12,714|                  3|            12,714|
|hhd                     |              513|            270,720|                  2|           270,720|
|mhas                    |              513|              8,208|                 10|             8,208|
|mort                    |              506|                506|                  1|               506|
|nippv                   |              496|              2,496|                  4|             2,496|
|pfvc                    |              513|             12,988|                  3|            12,988|
|qsql                    |              513|            179,163|                 61|           179,163|
|sgft                    |              504|                504|                  2|               504|
|sgtr                    |              502|                502|                  2|               502|
|vs                      |              513|             52,523|                  7|            52,523|


## Mapping Decisions

This section will provide detail on mapping decisions specific to the dataset(s) listed above.

DO WE WANT TO DO THIS?
If a test was not done, the record was mapped as a "No history of" record in the Observation domain with the test in the value_as_concept_id variable.

### DEMO dataset - Demographics

When ethnicity is Unknown, the concept_id = 0. When race is unknown or more than one race, the concept_id = 0.

### ALSFRS-R

Each of the ALSFRS-R questions went into Observation since they all have OMOP terms available.

### ALS dataset - El escorial criteria

Medical History

All variables were mapped as question/answer pairs in Observation except for date of diagnosis and date of symptom onset. Date of diagnosis was mapped to the Condition domain for the ALS OMOP term. The date of symptom onset is in Observation along with site of onset.

Custom concepts were created for ALS Symptom Onset and ALS anatomical site of symptom onset within this dataset.

### Mortality

Date of death is located in the Death domain. 

### Measurements (lab values)

INSERT WHAT WE CAN HERE

#### Medications 

Medications were mapped to ingredient level wherever possible.
Dose was not calculated. 
All source was included in the source values.
If the drug or supplement is unmapped, the concept_id was set to 0 and the source data included in the appropriate source column.

### Site of Onset
UPDATE HERE XXX

## Military

## Industry

## Genetics

## Injury
