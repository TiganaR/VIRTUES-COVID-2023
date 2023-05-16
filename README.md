# VIRTUES-COVID-2023
### Summary:
The COVID-19 pandemic has exposed significant gaps in our healthcare system, particularly when COVID-19 positive individuals with less severe symptoms are asked to self-isolate at home but are not provided with a care plan. Discharging COVID-19 patients from the hospital without a future care plan illustrates a serious lack of continuity of care from hospital to the community, and we must find a way to bridge these gaps in care.

Over the last 4 years the Cardiovascular Network of Canada has developed a secured, cloud-based patient-centred virtual care platform, VIRTUES (Virtual, Integrated, Reliable, Transformative, User-driven, E-health System), that integrates personal health records and biosensor data with data output and feedback to patients and caregivers. 

VIRTUES was designed to provide virtual care for patients with cardiac implantable electrical devices (pacemaker, implantable cardioverter-defibrillator, cardiac resynchronization therapy), atrial fibrillation and other heart rhythm disorders. Due to the public health emergency VIRTUES was repurposed for the management of COVID-19 positive patients isolating at home. We postulated that using VIRTUES, which integrates data from frequent symptoms reporting, vital data assessment, and feedback to patients and the regional COVID-19 care teams, will meet patient satisfaction, alleviate their anxiety, and improve efficiency of care by avoiding unnecessary emergency department visits. 

### Questions:
In this analysis we are interested in answering the following questions:
1.	What is the level of patient satisfaction with virtues?
2.	What patient demographics are related to patient satisfaction?
  a.	Are satisfaction levels the same for marginalized groups such as ethnic minorities or those who identify as women?
  b.	Is satisfaction dependent on patient outcomes?
3. What was patients QOL during covid infection
  a. Did virtues resolve patient anxiety?
  b. How does QoL vary by Sex?

### Data:
The original dataset (pre collected) contains 807 observations on 72 variables with 13.5% overall missingness. Multiple imputation (by chained equations) was conducted to eliminate missing data.

Many variables of interest are 5-point Likert scales. The following three scales were utilized:


1. [no problem], 2 [slight problem], 3 [moderate problem], 4 [severe problem], 5[unable]
2. [Strongly agree], 2 [agree], 3 [not sure], 4 [disagree], 5 [strongly disagree] 
3. [none], 2 [slight], 3 [moderate], 4 [severe], 5 [extreme]
  
  
Variables of most interest:

*Demographics:*

`Sex`: patient biological sex (M/F)
  
`Gender`: patient identified gender (M/F/2/O)
  
`Race`: patient race (Asian/Black/White/Latin/Indigenous/PI/Other)
  
`Immigrant`: (Y/N)
  
`Immigrant_5Yrs`: did the individual immigrate within the last 5 years (Y/N)

`wave`: wave of covid 
  
*QOL: Quality of Life survey (data available for days 1, 14, 28)*

`mobility`: patients’ ability to move around. Likert scale A

`self_care`: patients’ ability to wash or dress. Likert scale A

`pain`: patient experiencing pain or discomfort. Likert scale C

`Axiety/depression`: patient experiencing anxiety or depression. Likert scale C

`usual_activities`: patients’ ability to perform usual activities. Likert scale A

`health_today`: Patients self reported health on specific day (0 to 100)

`total_qol`:  1-(mobility+self care+pain+sad+usual activities)/25. (0 to 1, higher is better)
  
*PSS: Patient satisfaction survey (data available for days 14 and 28):*

`satisfied`: patient was satisfied with virtues. Likert B

`reduced`: patient experienced a reduction in anxiety due to virtues. Likert B

`easy`: patient found VIRTUES easy to use. Likert B

`connected`: patient felt more connected using VIRTUES. Likert B

`fixed`: helped resolve patients’ urgent health care problem resulting from COVID. Likert B

`total_pss`:  1-(reduced+easy+connected+fixed+reduced)/25  (0.0-1.0, note higher is better)
  
*FUS: Follow up survey (data available for days 14 and 28)*

`o2`: did the patient require at home oxygen? (Y/N)

`med_att`: did the patient need unscheduled medical attention? (Y/N)
  
`ERvisit`: number of ER visits
  
`GPvisit`: number of GP visits
  
`any_visit`: did the patient require a medical visit at any time during follow up? (Y/N)


### Methods Used:

**MMRM**: Mixed models repeated meausres used to model patient satisfaction by QoL and demographics
**GEE**: Genderalized estimating equations were also utilized to analyize satisfaction, MMRM and GEE results were compared to reduce risk of model misspecification.
**EMD**: A modified earth movers distance was utilized to compare distributions, ex QoL over time.
**Wilcoxon**: All EMD values were compared to wilcoxon results to strengthen confidence in results.
