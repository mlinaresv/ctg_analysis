# ctg_analysis
Python library for the automatic cardiotocogram (CTG) analysis and interpretation. Cardiotocography is defined as the recording of the fetal heart rate and the mother's uterine pressure and is normally used during labour as a screening tool to determine fetal's wellbeing. The type of data is called *cardiotocogram* and consists of both:
1. Fetal Heart Rate (FHR) signal.
2. Tocometry (uterine pressure) signal.

This library proposes different functions to extract the most important features that characterize the CTG signals. According to FIGO's guidelines, these are:
- Baseline:
- Accelerations:
- Decelerations:
- Short-Term Variability:
- Long-Term Variability:

In relation to the type of decelerations, a function capable of discriminating between early, late and variable decelerations is also available.
- Early Decelerations:
- Late Decelerations:
- Variable Decelerations:

A complete analysis example.
