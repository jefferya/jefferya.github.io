# Studying Policy Documents at Scale with AI

DSC March 6, 2026

* Mohamed Abdalla, Assistant Professor, Department of Medicine
* Peter Binkley, Digital Scholarship Technologies Librarian, U of A Library Digital Scholarship Centre
* Michael B. McNally, Professor, Faculty of Education - School of Library and Information Studies
* Geoffrey Rockwell, Professor, Philosophy and Media Tech Studies (MTS); Canada CIFAR AI Chair and Amii Fellow

Public consultation is important in policy. How well is gov listening to consultation when crafting policy?

## Methodogical approach

LLM

* who participating
* what arguments are being made?
* GRA vs. professor vs. LLM
* theme versus verbatum extraction

## Tools and tech

* data conversion and cleaning
* LLaMA 3.3 70B Instruct model for concern extraction
* cluster extracted themes: sentence BERT('all-mpnet-base-v2)

## Results (Toronto AI & policing)

* precision/recall uneven for themes: classification quality depends on theme, worse when inferences needed when reading consultation documentations
  * over-labeling
  * thematic conflation
  * intent blindness

## Copyright in the Age of Gen AI

* Gen AI to extract text on a given consultation question. 
  * compare 2 humans and AI on extractions:
    * metrics - directional exact match and token sort ratio
    * Researchers Michael & Faith evaluate extractions who did best job (randomized blind)

## Summary

* off-the-shelf LLMs not ready for automated policy analysis
* theme extraction is poo
* theme assignment

## Future

* what trips up LLMs (points of failure) classification and extraction

## Q & A

* Auditing? Compare theme extraction to final policy