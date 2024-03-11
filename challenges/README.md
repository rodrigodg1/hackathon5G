## Challenges

> This folder contains the challenges proposed for the _Hackathon SMARTNESS / 5G Dataset Challenge_

> 📚 Auxiliary Notebooks
> - Submission template: ./submission-template.ipynb for the challenges
> - Getting started: ./get-started.ipynb in Machine Learning and using the datasets

The most recent edition of the Ericsson Mobility Report: [https://www.ericsson.com/en/reports-and-papers/mobility-report/dataforecasts/traffic-by-application](https://www.ericsson.com/en/reports-and-papers/mobility-report/dataforecasts/traffic-by-application) pointed out that, in 2022, 71% of the world's mobile network traffic was video streaming, and by 2028 this demand is expected to increase by 9%. In this scenario, mobile network management and analysis are fundamental elements to promote a better user experience for this type of service, which tends to provide new business and research opportunities as the use of the 5G network expands.

Therefore, the SMARTNESS Hackathon presents the following challenges that can contribute to the development of new mobile network management and analysis solutions, aiming to meet the growing demand for video traffic and optimize the user experience.

---
- **#1 Visualization using PathsViewer**
  \
  🔍📊

  **The tool**: PathsViewer: [https://github.com/intrig-unicamp/paths-viewer](https://github.com/intrig-unicamp/paths-viewer) is an interface for visualizing space-time data in real time or post-event. This tool seeks to meet the demand for visualization tools for object trajectories, given the great interest in research in this type of data.

  It is possible to use varied datasets, with different structures, such as georeferenced 5G traces and vehicle trajectories.

  **The challenge**: This challenge aims to use the PathsViewer tool to present the datasets provided (it is not necessary to use all of them).

  Teams should explore the functionalities of PathsViewer, such as zoom adjustment, visualization in 2D or satellite map, sending multiple datasets, among others. With this, it is possible to generate clear and informative visualizations that help users to visualize the information contained in the object trajectory data.

  **The delivery**: Since this specific challenge does not involve the application of machine learning techniques (as do the others), the submission of a Jupyter Notebook is not required. Instead, it is expected that the submission of this challenge will consist of a description of what was done by the team, the insights obtained, suggestions for improvements to the tool, any codes produced for data processing accompanied by a video or screenshots that show the PathsViewer interface with the datasets provided. It is important that the delivery shows the functionalities used by the tool.

---
- **#2 Signal quality prediction**
  \
  🔮📶

  The objective of this challenge is to infer the signal quality based on the attributes provided in the `g-nettrack` database. Teams can combine the provided data with information present in other datasets in order to complement and enrich the available data. For example, it is possible to combine the data from the `g-nettrack` database with those from the `mosaico` database to provide information about the antennas in the vicinity, such as location, azimuth, antenna density, frequency and technology.

  Teams will be able to use statistical models and/or machine learning techniques, such as mono and multivariate prediction models, to infer the values of a signal quality indicator of choice, such as QUAL, CQI and SNNR.

---


- **#3: Mobility Type Prediction**

🔮🚗

This challenge involves using unsupervised machine learning methods to predict the mobility type (pedestrian, vehicle, metro/train) of a mobile device based on the unlabeled location data provided in the `g-nettrack` dataset. This task can be approached in various ways, such as through a clustering-based classification problem (unsupervised classification), where the machine learning model must classify each dataset record into one of the possible mobility classes.

- #**4: Video Streaming Quality of Experience (QoE) Prediction**

🔮🎬

The video streaming Quality of Experience (QoE) prediction challenge involves using machine learning techniques to predict the QoE of video streaming on mobile devices. The `youtube-qoe` dataset provides the video streaming metrics. The goal is to create two prediction models that consider information such as cell phone coordinates, network characteristics, and technology used, among other variables, to estimate the transmission QoE. This can improve the user experience by ensuring that video streaming is performed with the best possible quality, considering the network conditions and the region where the user is located.

The developed models must predict the transmission QoE based on different inputs:

- Model 1: Makes the prediction based on location data obtained from the `g-nettrack` dataset correlated with the `mosaic` dataset to obtain nearby antennas.
- Model 2: Makes the prediction based on network metrics (such as signal quality and technology) obtained from the `g-nettrack` dataset.

In summary, Model 1 should only consider the availability of antennas near the user (such as the technology, power, and other factors of the ERBs that can influence the best network quality in a specific region) to infer the QoE. In contrast, Model 2 only considers network conditions (network metrics).

In addition to working on developing the models, teams must create a function to define QoE. A simplistic alternative is to directly relate QoE to video resolution. However, it is evident that a high-resolution video with constant buffering does not have good QoE. Conversely, a completely smooth and buffer-free video does not have good QoE if it is transmitted at a very low resolution.

- **#5: Inferring which Cell/Base Radio Station a Mobile Phone is Connected to**

🔮📡 

The proposed challenge is to infer which Cell/Base Radio Station (ERB) the mobile device is connected to, based on the cell phone coordinates, using the `g-nettrack` dataset correlated with the `mosaic` dataset to obtain nearby antennas. This involves using data processing and machine learning techniques to analyze location data and nearby antennas, as well as basic knowledge of the physical architecture of mobile networks.

It should be considered that the antennas of an ERB can be directional (Azimuth > 0) or omnidirectional (Azimuth = 0), that is, they can direct the transmitted signal to a specific direction or transmit signal to all directions around them, respectively.

## Evaluation Criteria:

- Participants must solve as many of the provided challenges as possible;
- Data preprocessing;
- Data representation and attribute composition strategy;
- Selection strategy of the chosen model;
- Validation strategy;
- Model quality regarding quality metrics (such as accuracy, precision, recall, and F1-score);
- Interpretability of the suggested model;
- Data storytelling, including conclusions;
- Potential impact and feasibility of the presented solution; and
- Creativity of the solution and presentation.
