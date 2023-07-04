# ctg_analysis
Python library for the automatic cardiotocogram (CTG) analysis and interpretation. Cardiotocography is defined as the recording of the fetal heart rate and the mother's uterine pressure and is normally used during labour as a screening tool to determine fetal's wellbeing. The type of data is called *cardiotocogram* and consists of both:
- Fetal Heart Rate (FHR) signal.
- Tocometry (uterine pressure) signal.
This library proposes different functions to extract the most important features that characterize the CTG signals. According to FIGO's guidelines, these are:
- Baseline:
- Accelerations:
- Decelerations:
- Short-Term Variability:
- Long-Term Variability:
