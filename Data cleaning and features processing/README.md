

FILE : Model - Build_features_final_features

## Data cleaning of raw dataset (  ~ 100 M rows of data )
Filtering Outliers, dupplicates

## Data features processing
    1. Creating previous timestamp question answer for same question already previously viewed ( Using numpy to be more efficient considering the huge amount of data and the low number of CPUs)
    2. Using this previous timestamp, calculating following features: 
        'previous_false_answer',
        'previous_correct_answer',
        'nb_previous_questions_answered',
        'previous_answer'
     3. Processing user statistical features
     4. Processing questions statistical features
     5. Processing user answer statistical features ( Prob distribution to answer A, B, C, or D for each user)
     6. Processing Bundle statistical features
     7. Processing Lagtime statistical features
     8. Processing first question statistical features
     9. Processing progress question statistical features

  ## Merging final data and calculating specific aggregated metrics such Harmonic mean between average answered correctly mean per user and per question

  ## Unique content by user part aims to create features max values to predict as this competition is timeseries based.

FILE : Model - Build_features_final_features

## Data specific feature historical perf per question
	1. The idea is to create dummy data for each user historical answer.
	2. Then create cumulated Kpi of this perf to know if a question at t time as been answered or not for a specicic user.
	3. Aggregate these Kpis in bundle of 0-1 combination to avoid to retrieve 13 000 dummies features x 100 M row of data.
	4. Label encode these dummies to avoid bad memory performance due to long string concatenation
