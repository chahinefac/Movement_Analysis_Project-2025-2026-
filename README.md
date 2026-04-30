# Movement_Analysis_Project 2025-2026

# Comparison of Jump Height between Squat Jump (SJ) and Countermovement Jump (CMJ)

# 1. Scientific Problem
## 1.1 Context

The **stretch-shortening cycle** (SSC) is a is a fundamental component of force production in dynamic movements. It consists of a rapid eccentric phase immediately followed by a concentric contraction, allowing the storage and reutilization of elastic energy and improving force production.
In vertical jumping, the SSC contributes to performance by increasing jump height when a countermovement is performed before take-off. This explains why the Countermovement Jump (CMJ) generally produces greater jump height than the Squat Jump (SJ), which is performed from a static position and relies mainly on concentric force production.

However, in pathological conditions affecting the lower limb, such as patellar tendinopathy, movement strategies may be altered. Previous work from *Ben Zaki and al. (2025)* has shown that athletes with patellar tendinopathy can modify their jumping and landing mechanics, particularly at the knee, suggesting adaptations in the way force is produced and absorbed during explosive tasks.

**What we are looking for:** Assess whether the gain in jump height between Squat Jump and Countermovement Jump is preserved in patients with patellar tendinopathy.

## 1.2 Aim

The aim of this study is to quantify the difference in jump height between Squat Jump and Countermovement Jump in individuals with patellar tendinopathy, as an indirect measure of stretch-shortening cycle contribution.

## 1.3 Method 

Each participant wore  17 IMUs (MTw Awinda, XsensTechnologies, Enschede, Netherlands) with a sampling rate of 60 Hz and placed according to the full body Xsens guidelines. The participants were requested to perform a series of vertical jump tests, each of which was to be completed on three occasions, with 30-s of rest between each jump type.

## 1.4 Participants

Twelve high-level athletes diagnosed with patellar tendinopathy participated in this study.

## 1.5 Primary Outcome Measure

Jump Height (Flight Time) [cm] ​

Where Jump height (flight time) is defined as *the vertical displacement of the center of mass estimated from the flight duration, assuming identical center of mass position at take-off and landing and ballistic motion during the airborne phase (Nicholas P. Linthorne, 2001).*

# 2. Python Project
## 2.1 Aim 

The objective of this project is to check that all jump files are present, extract the Jump Height (Flight Time) [cm] mean value from the Squat Jump and Countermovement Jump files, and create a cleaned dataset allowing visual comparison between both jump conditions for each patient.

## 2.2. Data organization

### 2.2.1. Participants data

The data are organized in one main folder named `data`.

This folder contains one subfolder per patient:

- each subfolder corresponds to one participant;
- each participant performed both Squat Jump and Countermovement Jump tests;
- each jump condition is stored in a separate Excel file.

## 2.3 Data Processing

A Python script was used to:

- Browse all patient folders
- Read each Excel and CSV file
- Check the presence of SJ.xlsx and CMJ.xslx files
- Detect the correct header row
- Identify the row corresponding to Jump Height (Flight Time)
- Extract the Mean value
- Store the results in a structured dataset

The resulting dataset contains:
| Patient      | SJ_Mean       | CMJ_M     |
| :---        | :---:        | ---:       |
| x       | y        | z        |

The cleaned dataset is saved as : 
 `Global_Jump_Height.xlsx`


## 2.4 Visualization

Two visualizations were generated:

- Boxplot: comparison of SJ and CMJ distributions
- Paired plot: visualization of individual differences


# 3. R Project
## 3.1 Aim

The objective of the R analysis is to statistically compare Jump Height (Flight Time) [cm] between the Squat Jump (SJ) and Countermovement Jump (CMJ) conditions.

## 3.2 Statistical Analysis

The statistical analysis was performed on the cleaned dataset generated with Python (`Global_Jump_Height.xlsx`). Because the same participants performed both jump conditions, the comparison between SJ and CMJ was treated as a within-subject comparison.

First, a new variable was calculated :
- $CMJ_SJ_Difference = CMJ_ Mean - SJ_ Mean$ 

This variable represents the individual gain in jump height from SJ to CMJ. 

Normality of the paired differences was assessed using the Shapiro-Wilk test. This step was necessary because the paired t-test assumes that the distribution of the differences between paired observations is approximately normal. If the normality assumption was satisfied, a paired t-test was used to determine whether the mean Jump Height differed significantly between SJ and CMJ.

The significance level was set at p < 0.05.

The statistical analysis provided:

- mean SJ jump height;
- mean CMJ jump height;
- mean difference between CMJ and SJ;
- t-value;
- p-value;
- interpretation of statistical significance.

  
# 4. Conclusion

The comparison between Squat Jump (SJ) and Countermovement Jump (CMJ) showed that jump height was systematically higher in the CMJ condition. This result is consistent with the expected contribution of the stretch-shortening cycle, which enhances force production during dynamic movements.

At the individual level, most participants demonstrated an increase in jump height from SJ to CMJ, suggesting that the ability to utilize the stretch-shortening cycle is preserved despite the presence of patellar tendinopathy.

These findings indicate that, in this population, jump performance follows the same general pattern observed in healthy individuals, with a clear advantage of CMJ over SJ.

# 5. References

Linthorne, N. P. (2001). Analysis of standing vertical jumps using a force platform. American Journal of Physics, 69(11), 1198–1204.

Ben Zaki, B., Julia, M., Desmyttere, G., Perrey, S., & Dusfour, G. (2025). Altered landing strategy during vertical jump tasks in elite volleyball players with patellar tendinopathy.

Bisseling, R. W., Hof, A. L., Bredeweg, S. W., Zwerver, J., & Mulder, T. (2007). Relationship between landing strategy and patellar tendinopathy in volleyball. British Journal of Sports Medicine, 41(7), e8.

Butler, R. J., Crowell, H. P., & Davis, I. M. (2003). Lower extremity stiffness: Implications for performance and injury. Clinical Biomechanics, 18(6), 511–517.

DeVita, P., & Skelly, W. A. (1992). Effect of landing stiffness on joint kinetics and energetics in the lower extremity. Medicine & Science in Sports & Exercise, 24(1), 108–115.
