# Analysis of Temporal Network Architectures for Phase Detection

Dissertation submission for Project module while studying BSc Computer Science for second semester of academic year 2020–2021 at University of West London. The artefact is split into three stages as can be seen from the figure below.

<p align="center">
  <img width="850" src="https://user-images.githubusercontent.com/26774196/122645811-309bcc80-d114-11eb-8c2d-c3c2b49147af.png">
</p>

<p align="center">
  <table align="center">
    <tr>
      <th>
        <a href="https://github.com/dropcmd/Temporal-Neural-Network-Analysis/raw/master/docs/dissertation.pdf">
          Download Report 📃
        </a>
      </th>
      <th>
        <a href="https://github.com/dropcmd/Temporal-Neural-Network-Analysis/raw/master/docs/poster.pdf">
          Download Poster 📊
        </a>
      </th>
      <th>
        <a href="https://downgit.github.io/#/home?url=https://github.com/dropcmd/Temporal-Neural-Network-Analysis/tree/master/artefact">
          Download Artefact 🎯
        </a>
      </th>
      <th>
        <a href="https://github.com/dropcmd/Temporal-Neural-Network-Analysis/archive/refs/heads/master.zip">
          Download All 📦
        </a>
      </th>
  </table>
</p>



## Abstract

<img src="https://user-images.githubusercontent.com/26774196/122442823-e2ad8a00-cf96-11eb-86eb-4d9e76c79e8c.png" align="right"  alt="drawing" height="200"/>

Computer-assisted identification of end-diastolic (ED) and end- systolic (ES) heart phases within echocardiography (echo) scan enables a level of automation, a process previously only achievable by qualified medical staff members. This research focuses on the possible improvements using variations of neural network architectures, primarily focusing on the temporal aspect. A CNN and RNN model architecture usability applies to heart-phase detection, where expertly annotated ED and ES echo scans are the ground truth for model training. Results show that variates tested have the ability to outperform some existing solutions, falling behind architectures with more comprehensive spatial capturing characteristics. Additionally, performance analysis between variates suggests networks with bidirectional architectures increase computation time significantly, compared to their counterparts, while providing sub-optimal results.

## Methodology

<p align="center">
  <img width="850" src="https://user-images.githubusercontent.com/26774196/122645396-5a53f400-d112-11eb-8454-ca034bbb1013.png">
</p>
  
To ready the network for real-world usage, a subsection of the dataset will be used for training. The model will determine what features to pay attention to in the cine scan by knowing which are through available expert annotations. Using transfer learning for capturing spatial characteristics, the CNN used in this research is the InceptionV3.

<p align="center">
  <img width="700" src="https://user-images.githubusercontent.com/26774196/122443993-032a1400-cf98-11eb-8892-2224c5fc1361.png">
</p>

RNNs handle the temporal network section which depends on the variate. The model formation consists of a regression-based approach which establishes a gradual relation between the ED and ES phases, recognising the structure of the data. The model benefits from gradual changes in heart phase labels, potentially recognising the dependencies before, during, or after a phase. To calculate the error of the model during training and otherwise, Keras provides various loss functions. MSE and MAE is captured throughout the training and validation process, however the aaFD is the important metric which the custom testing process will calculate on the test dataset.

## Results

<img align="right" height="600" src="https://user-images.githubusercontent.com/26774196/122645438-80799400-d112-11eb-986c-360753a02103.png">

Reviewing test results on a comprehensive test at the end of training (50 epochs) may not be adequate. Over-fitting is a critical problem plaguing machine learning models. The model begins to confine in the memorisation of the data instead of providing more general prediction with higher accuracy for unseen data. Instead, each variate is evaluated on their accuracy on the epoch that achieved the lowest validation error. Variate E performs the best from all variates in 22 epochs and represents the absolute best possible heart phase detection model version of all tested instances, as seen from table seen on the right hand side.

Figures on the right-hand side show aaFD ED and ES error frequency, and the information appears to be in line with 2.5 and 2.4 mae values for ED and ES, respectively. The frequency of ED and ES errors falls largely within 5, with very few entries for greater values. The model seems to be attempting to learn relevant patterns. Additionally, even though the large error values are infrequent, there is a hypothesis for their occurrence. Error values of 20 or higher could be predicting the phases heart beats before or after the EchoNet annotation. Regarding efficiency, there is a correlation evident surrounding the trainable model parameters, and the computation time. It is observed that variates with bidirectional LSTM increase computation time considerably.

## Motivation

A key driver for this research is the investigation and potentially proposition of alternative neural network architectures to aid the accuracy and performance of self- driven heart assessments. Within the analysis stage of the self-driven heart exam, ML can assist with phase detection.

A standalone echocardiogram (echo) can help identify damage from a heart attack, heart failure, congenital heart disease, problems with the heart valves, and cardiomyopathy. The previously mentioned automated heart assessment focuses on heart phase detection in an echo scan. The subject of this research is the find the time step of end-diastolic (ED) and end-systolic (ES) heart phases within an echo scan. The analysis of ED and ES heart phases could provide information on ejection fraction (EF). EF references the amount of blood pumped from the left ventricle per heart contraction and is one of the various aspects that identifying ED and ES heart phases can help with heart assessment.

The aspect of no standardised dataset prompts the issue in the comparison of performance. While studies focus to provide metric for comparison (e.g., aaFD), differing data for each of the tested models trigger the issue of unfair testing as more than one variables differ. In the case of phase detection, various models are subject to comparison, yet they are tested on varying datasets.
