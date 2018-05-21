# PICRUSt_database_update
This repo contains updated precalculated files to be used with PICRUSt for prediction of metagenomes from 16S rRNA amplicon sequencing data.

Current databases for PICRUSt (PICRUSt v1.1.3) are outdated and contain KEGG Ortholog identifiers for upto ~K15000. However, KEGG presently houses nearly 20,000 KEGG ortholog definitions that are mapped to KEGG pathways/KEGG modules. Updation of the KEGG ortholog prediction database is thus critical to the holistic mapping of KOs to KEGG modules/Pathways. 

These databases are meant for mapping with the May 2013 release of Greengenes and NOT the 2012 release. The 16S precalculated files are also provided. The databases provided are updated to 4th April, 2016 Integrated Microbial Genomes (IMG) data and contain annotations against KEGG v77.1 for ~34,000 bacterial and archaeal genomes, which is more than double that of the original PICRUSt databases.

The precalculated database for KEGG orthologs can be found here:
https://www.dropbox.com/s/i3intevnp05wm4r/ko_13_5_precalculated.tab.gz?dl=0

In a shift from the original, users will have to append KEGG Pathways metadata manually to the predicted metagenome as the databases do not output the same. This can be done using the provided KEGG_metadata file:
1. Predict the metagenome: predict_metagenomes.py -i OTU_table_norm.biom -o predicted_metagenome.biom
2. Add metadata: biom add-metadata -i predicted_metagenome.biom -o predicted_metagenome_md1.biom --observation-metadata-fp KEGG_metadata.txt --sc-pipe-separated KEGG_Pathways --output-as-json
3. Check your new metadata added predicted metagenome: biom convert -i predicted_metagenome_md1.biom -o predicted_metagenome_md.tab --observation-metadata-fp KEGG_metadata.txt --header-key KEGG_Description --to-tsv --table-type "OTU table" --tsv-metadata-formatter naive

Taxonomy metadata is added as in the original PICRUSt databases under the "taxonomy" header.

If you are using these databases please cite our work:
Mukherjee, A., Chettri, B., Langpoklakpam, J. S., Basak, P., Prasad, A., Mukherjee, A. K., Bhattacharyya, M., Singh, A. K. & Chattopadhyay, D. Bioinformatic Approaches Including Predictive Metagenomic Profiling Reveal Characteristics of Bacterial Response to Petroleum Hydrocarbon Contamination in Diverse Environments. Sci Rep 7, 1108, doi:10.1038/s41598-017-01126-3 (2017).

Happy hunting!!
