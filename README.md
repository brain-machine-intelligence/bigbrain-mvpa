# bigbrain-mvpa

### Building multi-modal datasets to predict individual differences in  decision-making and psychiatric disorders with behavioral modeling and AI technology development
 - This work has supported by the National Research Foundation of Korea(NRF) grant funded by the Korea government(MSIT)(No. 2021M3E5D2A0102249311).

## Multi-voxel pattern analysis

### SPM preprocessing (recommended)
 - Slice-time correction
 - Motion correction
 - (Coregistration)
 - Spatial normalization

### Multi-voxel pattern (ROI)
* main function: arbMBMF_boldpat.m

    - To read the neuroimaging files and save/load them as a multi-dimensional array
    - requirements
        - nii file directory path
        - SBJ_structure.mat (recorded timepoint)
    - input
        - experiment name
        - ROI name
        - participant ID
        - varargin
            - z-scoring / percent signal
            - preprocessing prefix
    - output
        - bold activity array (N_voxel x N_event x N_trial)

### Shattering dimensionality analysis [1, 2]. 
 To assess the amount of information associated with the task variables in multi-voxel patterns of brain regions, we computed the shattering dimensionality (SD) by averaging test accuracies of all linear support vector machines (SVM) trained to classify goal and uncertainty conditions. Accordingly, the SD quantiﬁes the separability of neural embeddings associated with each task condition. Since it is based on binary classiﬁers, the chance level is 0.5.

* main function: arbMBMF_shattering.m

    - 5 steps
        1. variable setting 
        2. label loading 
            - arbMBMF_load_var.m
        3. BOLD pattern loading 
            - arbMBMF_boldpat.m
        4. linear shattering 
            - linear_shattering.m
        5. result saving
    - requirements: 
        - parameter setting in the script
            - experiment name
            - ROI
            - label
            - result save path
    - input
        - participant ID
    - output
        - run_info, save_info (save them to the designated path)

### Cross-condition generalization analysis [2]
 To investigate the eﬀect of one task variable (A) on another variable(B)'s representation, we performed another SD analysis, in which SVMs were trained in one condition of variable 'A' and tested in the other conditions of it to decode variable 'B'. The average test accuracy is called the CCGP score.

## References
[1] Rigotti, M., Barak, O., Warden, M. R., Wang, X. J., Daw, N. D., Miller, E. K., & Fusi, S. The importance of mixed selectivity in complex cognitive tasks. Nature, 497(7451), 585-590 (2013).

[2] Bernardi, S., Benna, M. K., Rigotti, M., Munuera, J., Fusi, S., & Salzman, C. D. The geometry of abstraction in the hippocampus and prefrontal cortex. Cell, 183(4), 954-967 (2020).


