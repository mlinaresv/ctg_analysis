# ctg_analysis
Python library for the automatic cardiotocogram (CTG) analysis and interpretation. Cardiotocography is defined as the recording of the fetal heart rate and the mother's uterine pressure and is normally used during labour as a screening tool to determine fetal's wellbeing. The type of data is called *cardiotocogram* and consists of both:
1. Fetal Heart Rate (FHR) signal.
2. Tocometry (uterine pressure) signal.

This library proposes different functions to extract the most important features that characterize the CTG signals. According to FIGO's guidelines, these are:
- **Baseline**: the mean level of the most horizontal and less oscillatory FHR segments. This feature is the most important one as accelerations and decelerations depend on it. In this library, the baseline can be computed following different algorithms found in literature. (See references) 
- **Accelerations**: *increases* in FHR above the baseline, of more than 15bpm in amplitude, and lasting more than 15 seconds but less than 10 minutes.
- **Decelerations**: *decreases* in the FHR below the baseline, of more than 15bpm in amplitude, and lasting more than 15 seconds.
- **Short-Term Variability**: average of the absolute difference between FHR values of consecutive epochs for each minute (16 epochs).
- **Long-Term Variability**: average of the absolute difference between the maximum and minimum FHR value for each minute (16 epochs).

In relation to the type of decelerations, a function capable of discriminating between early, late and variable decelerations is also available:
- **Variable Decelerations**: decelerations in where the distance between the initial point of the deceleration and the peak is smaller than 30 seconds.
- **Early Decelerations**: decelerations in where the distance between the initial point of the deceleration and the peak is greater than 30 seconds and the distance between the previous tocometry peak and the deceleration peak is smaller than 30 seconds.
- **Late Decelerations**: decelerations in where the distance between the initial point of the deceleration and the peak is greater than 30 seconds and the distance between the previous tocometry peak and the deceleration peak is greater than 30 seconds.

## An analysis example
It must be taken into account that FHR and tocometry preprocessing techniques are required for the analysis. Therefore, preprocessing functions are also included in the repository. In our example, the initial length of the sequences was 120 minutes with a sampling frequency of 4Hz. After having processed the signals and resampled them by epochs, this is how the feature extraction analysis looks like each 10 minutes:
![CTG Analysis 1](https://github.com/mlinaresv/ctg_analysis/blob/main/example1.png)
![CTG Analysis 2](https://github.com/mlinaresv/ctg_analysis/blob/main/example2.png)
![CTG Analysis 3](https://github.com/mlinaresv/ctg_analysis/blob/main/example3.png)

## References
- **Baseline Algorithms**
  1. D.A. de Campos, J. Bernardes, A. Garrido, J.M. de Sá, and L. Pereira-Leite. SisPorto2.0: A program for automated analysis of cardiotocograms. *The Journal of Maternal-Fetal Medicine*, 9:311-318, 2000.
  2. S. Cazares. Automated identification of abnormal patterns in the intrapartum cardiotocogram. *Ph.D. Thesis at University of Oxford*, 2002.
  3. R. Mantel, HP. van Geijn, JM. Swartjes, EE. van Woerden, HW. Jongsma. Computer analysis of antepartum fetal heart rate: 1. Baseline determination. *Int J Biomed Comput.*, 25(4):261-72, 1990. 
- **Baseline Removal for the Tocometry Signal**. Z.-M. Zhang, S.Chen, and Y.-Z. Liang. Baseline correction using adaptive iteratively reweighted penalized least squares. *Analyst*, 135:1138-1146, 2010.
- **Definition of features**. D. Ayres-de-Campos, C. Y. Spong, E. Chandraharan, for the FIGO Intrapartum Fetal Monitoring Expert Consensus Panel. FIGO consensus guidelines on intrapartum fetal monitoring: Cardiotocography. *International Journal of Gynecology and Obstetrics*, 131:13-24, 2015. 
- **Linear Preprocessing**. Z. Zhao, Y. Deng, Y. Zhang, Y. Zhang, X. Zhang, and L. Shao. DeepFHR: intelligent prediction of fetal acidemia using fetal heart rate signals based on convolutional neural network. *BMC Medical Informatics and Decision Making*, 19:286, 2019.
