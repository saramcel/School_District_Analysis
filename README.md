# School_District_Analysis
Re-analyzing PyCity School District data after removing scores due to suspicion of academic dishonesty.

## Overview of the school district analysis

The purpose of this analysis was to examine how removing the 9th graders from Thompson High School changed the outputs. We would expect that the outputs for Thompson High School (and any categories containing Thompson High School) would be lower after the removal of the 9th graders because academic dishonesty is suspected. Most likely, they cheated to make their scores higher, which would inflate the scores in the original analysis. However, it is possible that academic dishonesty occurred that would not have necessarily increased scores for 9th graders (e.g. swapping tests, pulling the fire alarm, or using an outdated answer key). We will discover how the removal of these cases affects the overall results.

## Methods

The scores for Thomas High School 9th graders were replaced with NaNs, then the 10th - 12th grade scores were recalculated so that the proportions would be correct. We used this code to replace the math scores with NaNs:

```
student_data_df.loc[(student_data_df["school_name"]=="Thomas High School") & (student_data_df["grade"]=="9th"),["math_score"]]=np.nan
```

This was easy to replicate for the reading scores to enter NaNs for these. 

The following code pulled the 10th - 12th graders and put them in their own data frame, then counted the entries in the "student name" column in the new dataframe. This output 1174 students in 10th, 11th, and 12th grade attending Thomas High School. 

```
non_cheaters_df = student_data_df.loc[(student_data_df["school_name"]=="Thomas High School")]
non_cheaters_df = non_cheaters_df.loc[(non_cheaters_df["grade"]=="10th")|(non_cheaters_df["grade"]=="11th")|(non_cheaters_df["grade"]=="12th")]
non_cheater_total = non_cheaters_df.count()['student_name']
non_cheater_total
```


## Results

  ### How is the district summary affected?
  - Original Analysis:

  ![Original results 1](/Resources/O1.png)
  
  - New Analysis:

  ![New results 1](/Resources/N1.png)
  
  - The school district analysis overall are not very different after the removal of the Thompson High School 9th graders. The average scores and the percentages of students passing math and reading did not change very much.
  
  ### How is the school summary affected?
  
  - Original Analysis:
  
  ![Original results 2](/Resources/O2.png)
  
  - New Analysis:
  
  ![New results 2](/Resources/N2.png)
  
  - The removal of the Thompson High School 9th graders resulted in ___ scores for the Thompson High School. This is curious, because these scores vastly improved, and one would expect the scores to have lowered after cheating students had been removed. 
    
  ### How does replacing the ninth graders’ math and reading scores affect Thomas High School’s performance relative to the other schools?
  
  - Original Analysis:
 
   ![Original results 3](/Resources/O3.png)
  
  - New Analysis:
  
  ![New results 3](/Resources/N3.png)
  
  -
   
  ### How does replacing the ninth-grade scores affect math and reading scores by grade
  
  - Original Analysis:
  
  ![Original results 4](/Resources/O4.png)
  
  - New Analysis:
  
  ![New results 4](/Resources/N4.png)

  -

  ### How does replacing the ninth-grade scores affect scores by school spending
  
  - Original Analysis:
  
  ![Original results 5](/Resources/O5.png)
  
  - New Analysis:
  
  ![New results 5](/Resources/N5.png)
  
  -
  
  ### How does replacing the ninth-grade scores affect scores by school size
  
  - Original Analysis:
  
  ![Original results 6](/Resources/O6.png)
  
  - New Analysis:
  
  ![New results 6](/Resources/N6.png)
  
  -
  
  ### Scores by school type
  
    - Original Analysis:
  
  ![Original results 7](/Resources/O7.png)
  
  - New Analysis:
  
  ![New results 7](/Resources/N7.png)
   
   -
  
## Summary
Summarize four changes in the updated school district analysis after reading and math scores for the ninth grade at Thomas High School have been replaced with NaNs.

