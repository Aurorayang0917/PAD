## Readme
**PAD：An information resource for drug repurposing by propagation in a heterogeneous multi-level network**

PAD (Predictive Database for Drug Repurposing) is a public database for efficient and reliable drug repurposing. The predicted ranking results for drug repurposing should be useful for discovering new therapeutic effects for existing drugs. 

This text you see here includes supplementary codes and sample data. We will show you :

  - Description of sample data
  - Explanation on parameters
  - Implementation

**Description of sample data**


| Txt | Description |
| ------ | ------ |
|disease_list.txt|encoding of disease|
|protein_list.txt|encoding of protein|
|drug_list.txt|encoding of drug|
|disease_disease_similarity.txt | disease similarity|
| drug_disease.txt  | relation between drug and disease|
|drug_drug_similarity.txt|drug similarity|
|drug-target.txt|interaction between drug and target|
|gene_disease.txt|relation between gene and disease|
|protein_protein.txt|interaction beween proteins|

**Explanation on parameters**
There are four parameters in our model: restart probability *r*, weighting parameters of disease, target protein and drug *a*, *b* and *c* (the sum of *a*, *b* and *c* shall be 1), which control the impact of disease, protein and drug nodes in both initial and transmission process.

**Implementation**

  - **Protocal**
  
   You can implement the code as follows:
   
    ```sh
    python calculate_predict_all.py [a] [b] [c] [r]
    ```
    
    It should be noticed that `a+b+c=1, r<1`.
    For instance:
    
    ```sh
    python calculate_predict_all.py 0.5 0.4 0.1 0.7
    ```
    
    where `a=0.5 b=0.4 c=0.1 r=0.7`
  - **Output**   
    The output includes following documents:  
    *---Final_matrix_a_b_c_r.txt* which contains the main result
    
    *---process_a_b_c_r.txt*   which records the process
    
   The *Final_matrix_a_b_c_r.txt* contains the resulting probability matrix, in which rows and columns follow the sorted order of disease, protein and durg which are sorted in input files.Based on this matrix, the probability that the drug will appraoch corresponding disease could be obtained.

It should be mentioned that if you want to change the absolute path of input data,it should be correctly specified in original file.

**If you have problems using PAD, please contact biostat_sjtu@163.com**
