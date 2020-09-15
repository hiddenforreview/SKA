# SKA
Anonymous repository for <i>Semi-Supervised Knowledge Amalgamation for Sequence Classification</i>.
This repository contains the implementation for the first solution for SKA, named <i>Teacher Coordinator (TC)</i>. 

## File listing

+ __main.py__ : Main code for TC training
+ __model.py__ : Supporting models
+ __utils.py__ : Supporting functions
+ __requirements.txt__ : Library requirements

## Instructions on training TC

Prepared folders:

+ __data__ : contains training data
+ __teachers__ : contains teacher models
+ __output__ : directory for training logs and the final student model if saved
    + __plot__ : directory for training loss plots

Note that all datasets and the teacher models used in the paper can be found here: https://drive.google.com/drive/folders/1guPbiUawDvVrkhZXQvMZPS4blGosZiWW?usp=sharing

Run script as:

    python main.py -expname syn_exp1 -t_model ./teachers/exp1_syn_t1.sav ./teachers/exp1_syn_t2.sav \
    -t_numclass 4 4 -t_class 1 2 3 4 3 4 5 6 -s_class 1 2 3 4 5 6 -data ./data/SYN/syn_test.txt
  
<!-- data_label ./data/labeled_data.txt -data_unlabel ./data/unlabeled_data.txt -expname 'test'-->
  
<b>Parameters:</b>

+ __Required:__
  + __-t_model__ : a list of paths of teacher models 
  + __-t_numclass__ : the number of classes corresponding to t_model
  + __-t_class__ : a list of specialized classes of each teacher, concatenated in correspond to t_model , e.g., t1_class: 1 2 3 4 and t2_class: 3 4 5 6, then t_class: 1 2 3 4 3 4 5 6
  + __-s_class__ : a list of comprehensive classes of the student
  + __-data__ : the path of student training data file
  + __-expname__ : experiment name
  <!-- + __-data_label__ the student training data file with labels
  + __-data_unlabel__ the student training data file with no label -->

+ __Student network:__
  + __-lr__ : learning rate, default 0.01
  + __-ep__ : epochs, default 200
  + __-bs__ : batch size, default 8
  + __-layers__ : #layers, default 2
  + __-hiddim__ : #hidden units, default 8

+ __TTL network:__
  + __-lrTTL__ : learning rate, default 0.01
  + __-epTTL__ : epochs, default 500
  + __-bsTTL__ : batch size, default 8
  + __-layersTTL__ : #layers, default 2
  + __-hiddimTTL__ : #hidden units, default 8

+ __Others:__
  + __-inputsize__ : #features, default 1
  + __-seed__ : set seed for reproduction, default 0
  + __-plabel__ : proportion of available labeled data (range = [0,1]), default 0.02
  + __--save__ : boolean parameters, whether to save the student model, default false
