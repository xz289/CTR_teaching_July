# CTR_teaching_July
CTR RNA-seq teaching
This course is going to happen in 5th July, 2018. And we will generally teach the undergraduate RNA-seq data analysis.
The data we would like to use is from the following publication
     https://bsd.biomedcentral.com/articles/10.1186/s13293-018-0165-y.
There are 39 RNA-seq data, which ones will we plan to use for teaching? (Not decided yet)
We will teach from general quality control for RNA-seq to the differential gene expression analysis. <br>
## Problems

Problem is existing for running "sleuth_live",  ("sleuth"-0.30.0 and "kallisto"-version 0.44.0). The "so" object from sleuth has been run using as following, but the open window from sleuth_live for the analysis part the MA and volcano plot can not being produced. <br>

        so <- sleuth_prep(s2c, ~condition, target_mapping = t2g_sleuth, aggregation_column = 'ens_gene',
        extra_bootstrap_summary = T, read_bootstrap_tpm = T, pval_aggregate = F) <br>
        so <- sleuth_fit(so) <br>
        so <- sleuth_wt(so, which_beta= 'conditionYolkSac')  <br>
        models(so)  <br>
        results_sleuth <- sleuth_results(so, 'conditionYolkSac', pval_aggregate = F) <br>
The shiny window when you try to get MA plot, the error messge is <br>

                  Error: object 'b' can not find
and volcano plot give the error is <br>

                Error: object 'sigma_sq' can not find
which you can definitely see the object 'b' and 'sigma_sq' in the results_sleuth data frame. And also it worked in the old version of 'sleuth 0.28.0' and kallisto 0.43.1. There is no such question being asked in sleuth discussion weblink. The possibilities I have tried is change the aggregation_column='target_id', then the MA plot give the error is <br>

      Error: 'by' can't contain join column 'target_id' which is missing from LHS
I wonder whether it is because the new version of "sleuth" are more defined by command_line running, such as plot_bootstrap, plot_MA et al. But the 'so' object is the same as we load to sleuth_live. It may have a rerun using the new version kallisto for all the files? Strange error! Leave it for now, solve it later! <br>

In the teaching I will stick with the old version. 
