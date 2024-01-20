# Energy A.I. Hackathon 2024

## Hosts: [Prof. Michael Pyrcz](https://twitter.com/GeostatsGuy) and [Prof. John T. Foster](https://twitter.com/johntfoster)

### Architects: [Elnara Rustamzade](https://www.linkedin.com/in/elnara-rustamzade-779396162/) and [Fehmi Ozbayrak](https://www.linkedin.com/in/fozbayrak/)

### Home Department Chair and Hackathon Supporter: [Prof. Matthew Balhoff](https://www.linkedin.com/in/matthew-balhoff-4297b247/)

### Sponsors 

Platinum:
[Pioneer Oil Company Inc.](https://pioneeroil.net/), [Phillips66](https://www.phillips66.com/)

Silver:
[Chevron](https://www.chevron.com), [Shell](https://www.shell.us/), [ExxonMobil](https://corporate.exxonmobil.com/), Elizabeth Huth CoatesCharitable Foundation of 1992

Bronze:
[ComboCurve Inc.](https://www.combocurve.com/), [General Electric](https://www.ge.com/)

### Coordination and Student Engagement: Rowan Halliday, Heba Abdel-Rahim, Gabby Banales


___

### Energy A.I. Hackathon 2024 Problem Description 

**Goal**: Develop a data analytics and machine learning workflow in Python to:

* Predict **average pump difference** during drillout based many possible predictor features for 15 wells. This includes single estimates and an uncertainty model represented by 100 realizations for each well.
 
#### Background

When a well is completed, plugs are set to isolate stages. After the well has been hydraulically fractured, those plugs need to be drilled out. For lower-pressure formations, there is an increased uncertainty in bottom hole pressure experienced during drillout. This uncertainty makes it difficult to decide what fluid system to use and makes planning, scheduling, and budgeting post-stimulation operations more difficult.
Pump difference is defined as the difference between fluid pumped into the well and fluid returning to the surface.
In order to prevent fluid loss we challenge the Energy A.I. Hackathon 2024 teams of The University of Texas at Austin to build a data analytics and machine learning workflow to predict average pump difference with uncertainty.

This will require:

* data analytics and evaluation of multiple data sources over a variety of features
* feature engineering including feature selection, feature transformations, and feature imputation to address missing data
* integration of domain expertise at every step
* selection, training and tuning of robust machine learning prediction models  

Your model will be applied to support determination of optimum fluid type to prevent loss.  
___

### Available Data Files Inventory

You have the following available data:

#### Well Data

* **[HackathonData2024.csv](HackathonData2024.csv)** - data on 348 unique wells information.
  
The features include:
| Features  | Description |
| ------------- | ------------- |
| **Well ID** | Unique number assigned to each well as identifier |
| **Avg Pump Difference** | Pump difference (gal/min) is the fluid pumped into the well minus the fluid that is returning to surface |
| **Area** | The field is divided into smaller areas and wells in the same area are near one-another |
| **Lateral Length** | Length of the lateral section of the well in feet |
| **Fluid System** | A fluid system represents what type of fluid that was used to drill the well out |
| **TVD** | True vertical depth |
| **Development Strategy** | How to locate the next well in the reservoir |
| **DELAYED** | Whether offset wells exist near the wellbore, from a gun barrel view |
| **BOUND_CODE** | Whether offset wells exist near the wellbore, from a gun barrel view  |
| **CODEV_POSITION** | Within the co-development, the edge wells are the wells that do not have other wells on one side when viewed from above (formation does not matter) |
| **CODEV_FORMATION_POSITION** | Within the co-development, the edge wells are the wells that do not have other wells on one side when viewed from above (formation does matter)|
| **PARENT_CODEV_1050_WELL_COUNT** | The number of wells that were either put on production (POP’d) more than 60 days before the subject well was POP’d (parent wells) or were POP’d within 60 days of the subject well (codev wells) and have a hypotenuse distance of 1050ft or less |
| **PARENT_IN_ZONE_MIN_HYPOT** | The hypotenuse distance to the nearest parent well in the same formation |
| **PARENT_OUT_ZONE_MIN_HYPOT** | The hypotenuse distance to the nearest parent well in a different formation |
| **PARENT_IN_ZONE_MIN_MAP_DIST** | The map distance to the nearest parent well in the same formation |
| **PARENT_OUT_ZONE_MIN_MAP_DIST** | The map distance to the nearest parent well in a different formation |
| **PARENT_1050_AVG_WELL_AGE** | Average age (in days) of the wells that were POP’d more than 60 days before the subject well was POP’d and have a hypotenuse distance of 1050ft or less |
| **PARENT_1050_MEDIAN_WELL_AGE** | Median age (in days) of the wells that were POP’d more than 60 days before the subject well was POP’d and have a hypotenuse distance of 1050ft or less |
| **PARENT_1050_WELL_COUNT** | The number of wells that were put on production (POP’d) more than 60 days before the subject well was POP’d and have a hypotenuse distance of 1050ft or less|
| **PARENT_3000_AVG_HYPOT_DIST** | Average hypotenuse distance of the wells that were POP’d more than 60 days before the subject well and are within a 3000ft buffer around the well
| **PARENT_3000_AVG_MAP_DIST** | Average map distance of the wells that were POP’d more than 60 days before the subject well and are within a 3000ft buffer around the well |
| **PARENT_3000_AVG_TVD_DIST** | Average TVD distance of the wells that were POP’d more than 60 days before the subject well and are within a 3000ft buffer around the well |
| **PARENT_3000_AVG_WELL_AGE** | Average age (in days) of the wells that were POP’d more than 60 days before the subject well was POP’d and have a hypotenuse distance of 3000ft or less |
| **PARENT_3000_MEDIAN_WELL_AGE** | Median age (in days) of the wells that were POP’d more than 60 days before the subject well was POP’d and have a hypotenuse distance of 3000ft or less |
| **PARENT_3000_WELL_COUNT** | The number of wells that were put on production (POP’d) more than 60 days before the subject well was POP’d and have a hypotenuse distance of 3000ft or less |
| **CODEV_IN_ZONE_MIN_HYPOT** | The hypotenuse distance to the nearest well in the same formation (within the same codevelopment) |
| **CODEV_OUT_ZONE_MIN_HYPOT** | The hypotenuse distance to the nearest well in a different formation (within the same codevelopment) |
| **CODEV_IN_ZONE_MIN_MAP_DIST** | The map distance to the nearest well in the same formation (within the same codevelopment) |
| **CODEV_1050_WELL_COUNT** | The number of wells that were put on production (POP’d) within 60 days of when the subject well was POP’d and have a hypotenuse distance of 1050ft or less |
| **CODEV_3000_AVG_HYPOT_DIST** | Average hypotenuse distance of the wells that were POP’d within 60 days of the subject well and are within a 3000ft buffer around the well |
| **CODEV_3000_AVG_MAP_DIST** | Average map distance of the wells that were POP’d within 60 days of the subject well and are within a 3000ft buffer around the well |
| **CODEV_3000_AVG_TVD_DIST** | Average TVD distance of the wells that were POP’d within 60 days of the subject well and are within a 3000ft buffer around the well |
| **CODEV_3000_AVG_WELL_AGE** | Average age (in days) of the wells that were POP’d within 60 days of the subject well and have a hypotenuse distance of 3000ft or less|
| **CODEV_3000_MEDIAN_WELL_AGE** | Median age (in days) of the wells that were POP’d within 60 days of the subject well and have a hypotenuse distance of 3000ft or less |
| **CODEV_3000_WELL_COUNT** | The number of wells that were put on production (POP’d) within 60 days of when the subject well was POP’d and have a hypotenuse distance of 3000ft or less |
| **Pressure Gradient (psi/ft)** | Average change in pressure per unit of depth |
| **Soak Time** | Hours between the end of the stimulation phase (hydraulic frac) and the start of the drillout |
| **Avg Open Pressure** | Pressure at the wellhead right before the frac pumps are turned on at the start of a stage |
| **SD Open Pressure** | Standard deviation of average open pressure |
| **Avg Close Pressure** | Pressure at the wellhead taken after the frac pumps shut down at the end of a stage |
| **SD Close Pressure** | Standard deviation of average close pressure |


#### Problem Set

* **[solution.csv](solution.csv)**

The features include:

* **Well_ID** - anonymized, unique well identifier
* **Est Pump Difference** - hackathon solution to be entered by the team, indicating average pump difference for each well
* **R_** - 100 realizations for average pump difference for each well 
  
Comments: 

* all the well names are anonymized (replaced with simple indices).
* NaN in the file indicate missing data.
* the source of the data is confidential. Do not attempt to determine the source of the data.

___

### Required Hackathon Submissions

By January 21 at 12:00 noon each team must submit:

* **Solution Table** - a .csv file with your predictions (estimates and uncertainty) for the 15 wells using the template given in [solution.csv](solution.csv) in this directory.

    * the file must be named `solution.csv` with final values in a commit and then pushed to Github for automated scoring.


* **Python Workflow and Associated Files** - committed to this repository with the workflow as a Jupyter Notebook `.ipynb` file along with all data files required to reproduce your team's solutions. The submitted workflow Jupyter Notebook should follow the format of the provided template [Hackathon_ProjectTemplate](https://github.com/PGEHackathon/resources/blob/main/Hackathon_ProjectTemplate.ipynb) for enhanced workflow communication and code readibility.

    * the file must be named `xxxx.ipynb` and pushed to GitHub for review and scoring (for code readability) by the hackathon architects, where **xxxx** is your team name.


* **Presentation** - a PowerPoint slide deck .PPTX file for your team's final presentation to our judges. The submitted presentation should follow the format of the provided example presentation [Hackathon_PresentationTemplate](https://github.com/PGEHackathon/resources/blob/master/Hackathon_PresentationTemplate.pptx).

    * the file must be named `xxxx.pptx` and pushed to GitHub for review by the judges, where **xxxx** is your team name.

The Workflow, and Presentation templates are in the [PGEHackathon/resources](https://github.com/PGEHackathon/resources) repository. Use the [solution.csv](solution.csv) file (in this directory) to record your solution.
