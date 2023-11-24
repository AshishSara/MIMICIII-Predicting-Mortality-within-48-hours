This project aims to predict whether a patient will experience mortality (death) within 48 hours of their hospital admission or at some point during their ICU stay, based on the data available in their electronic health records (EHR) up to that time. The original EHR data used for this project is from MIMIC-III (linked below in the reference list) (1). This project uses the preprocessed data obtained from applying the FIDDLE protocol (2). Please see the reference section for the citation and a link to the description of the protocol. I have provided a brief summary of the preprocessed data below, but to confirm, the preprocessed data strategy is directly from the FIDDLE protocol and I claim no credit for the preprocessing strategy (2). 

Data: The protocol obtained data from MIMIC-III (1) dataset and focused on 17,710 patients (23,620 ICU visits) monitored 
using the iMDSoft MetaVision system (2008–2012) for its relative recency over the Philips CareVue system (2001–2008), 
thus representing more up-to-date clinical practices (2). Each ICU visit is identified by a unique ICUSTAY_ID (2).


**Extracted data from the following tables provided from the MIMIC III datset (1,2):**

PATIENTS, ADMISSIONS, ICUSTAYS, CHARTEVENTS, LABEVENTS, INPUTEVENTS_MV, OUTPUTEVENTS, PROCEDUREEVENT_MV, MICROBIOLOGYEVENTS, DATETIMEEVENTS


**Preprocessing (1):**
The data was then formatted into a table with 4 columns: [ID, t, variable_name, variable_value] and then applied FIDDLE 
(using the default settings) on the processed data tables for the prediction tasks to convert them into the required 
feature matrices.


**Cohort Numbers and Dimensionalities of Extracted Features are Summairzed Below:**


- Number of Instances (N): 8,577 ICU stays.

- Number of Time-Invariant Features (d): 96.

- Number of Time-Dependent Features (D): 7,307.


Features Used (D): The dataset includes high-dimensional feature representations (up to ~7,500 features), encompassing a wide 
range of clinical data such as vital signs, lab results, treatment information, and other relevant patient metrics.

Output of the Models: The models output a binary prediction:

Class 0: Represents patients who are not expected to experience mortality within 48 hours.
Class 1: Represents patients who are at risk of mortality within 48 hours.
Clinical Significance: This prediction is crucial in a healthcare setting as it helps in identifying patients who are at
high risk and might require more intensive care or intervention.

Implications:
Model Performance: In this context, it's particularly important to focus not just on overall accuracy but also on the model's ability to correctly identify the high-risk patients (Class 1). This is why metrics like recall, precision, ROC AUC, and F1-score for the mortality class are essential.

Model Interpretation: The feature importance analysis from these models can provide insights into which factors are most predictive of near-term mortality, helping clinicians understand key risk factors.

Use in Clinical Settings: Such models, if deployed in clinical settings, can assist healthcare professionals in making informed decisions, but they should be used as a supplement to, not a replacement for, clinical judgment and expertise.


**Reference:**
(1)**FIDDLE Publication Source:**
 https://academic.oup.com/jamia/article/27/12/1921/5920826
**FIDDLE Preprocessed Data Source:**
https://physionet.org/content/mimic-eicu-fiddle-feature/1.0.0/

(2) **MIMIC-III original publication:**
Johnson, A. E. W., Pollard, T. J., Shen, L., Lehman, L. H., Feng, M., Ghassemi, M., Moody, B., Szolovits, P., Celi, L. A., & Mark, R. G. (2016). MIMIC-III, a freely accessible critical care database. Scientific Data, 3, 160035.
**MIMIC-III Database:**
Johnson, A., Pollard, T., & Mark, R. (2016). MIMIC-III Clinical Database (version 1.4). PhysioNet. https://doi.org/10.13026/C2XW26.


**Standard Physionet Citation**
Goldberger, A., Amaral, L., Glass, L., Hausdorff, J., Ivanov, P. C., Mark, R., ... & Stanley, H. E. (2000). PhysioBank, PhysioToolkit, and PhysioNet: Components of a new research resource for complex physiologic signals. Circulation [Online]. 101 (23), pp. e215–e220.


