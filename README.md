# Laboratory-Work-5-Activity

https://drive.google.com/drive/folders/1qWRfwrAkRGwY1DyItX0mTxAXM5JxtdGY?usp=drive_link

## PART 12: Performance Comparison Table

| Model | Train Acc | Train Loss | Val Acc | Val Loss | Precision | Recall | F1 | AUC |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| **LW3 Baseline CNN** | 0.9520 | 0.0828 | 0.6080 | 1.9856 | 0.6232 | 0.6080 | 0.6056 | 0.9423 |
| **LW4 Improved CNN** | 0.7985 | 1.6977 | 0.7450 | 0.9295 | 0.7598 | 0.7450 | 0.7467 | 0.9051 |
| **Teachable Machine** | 0.9859 | 0.0052 | 0.9750 | 0.1910 | 0.0000 | 0.0000 | 0.0000 | 0.0000 |
| **MobileNetV2** | **0.7855** | **0.7165** | **0.8070** | **0.6073** | **8042** | **8047 ** | **8015 ** | **9779** |
| **EfficientNetB0** | 0.5893 | 1.5909 | 0.7730 | 1.1901 | 5560  | 5289 | 4924 | 9160 |
| **ResNet50** | 0.6375 | 1.2740 | 0.7660 | 0.8902 | 6049 | 5855 | 5693 | 9057 |

---

## GUIDE QUESTIONS (FINAL REFLECTION)

### A. Model Performance

**1. Which pre-trained model achieved the highest accuracy? Why?**
> **Answer:** MobileNetV2 achieved the highest validation accuracy at **80.70%**. It trained for the full 10 epochs and steadily improved each epoch, showing that its lightweight depthwise separable convolution design allowed it to learn the dataset's features more effectively within the same training setup compared to the other two models.

**2. Which model had the lowest performance? What could be the reason?**
> **Answer:** ResNet50 had the lowest validation accuracy at **76.60%**. It stopped early after only 3 epochs due to early stopping, and its deeper architecture requires significantly more training time and data to converge properly. With only 4,000 training images across 20 classes, ResNet50 did not have enough exposure to fully utilize its depth.

**3. How did loss values compare across models?**
> **Answer:** MobileNetV2 had the best final training loss at **0.7165** and validation loss of **0.6073** after 10 epochs. EfficientNetB0 ended with training loss **1.5909** and val loss **1.1901** after only 3 epochs. ResNet50 ended at training loss **1.2740** and val loss **0.8902** also after 3 epochs. MobileNetV2 clearly had the lowest and most stable loss values overall.

---

### B. Evaluation Metrics

**4. Why is accuracy not enough to evaluate a model?**
> **Answer:** Accuracy only tells you the total percentage of correct predictions, but it does not show how the model performs per class. Since this dataset has 20 herbal plant classes with 250 images each, a model could still miss specific classes entirely and still appear decent in accuracy. Precision, Recall, and F1-score are needed to see whether the model is consistently correct across all 20 classes.

**5. Which model had the best F1-score? What does it indicate?**
> **Answer:** Based on the training results, MobileNetV2 is expected to have the best F1-score since it had the highest validation accuracy at **80.70%** and the most stable loss. A higher F1-score means the model has a good balance between Precision and Recall, indicating it correctly identifies most herbal plant classes like **Sambong**, **Yerba Buena**, and **Mayana** without many false positives or missed detections.

---

### C. Confusion Matrix Analysis

**7. Which classes were frequently misclassified?**
> **Answer:** Classes with very similar leaf shapes and textures such as **lemon_balm**, **lemon_basil**, and **lemon_grass** are most likely to be misclassified since they share similar visual features. Lower-performing models like ResNet50 and EfficientNetB0, which stopped at only 3 epochs, would have more misclassifications across these visually similar classes.

**8. What patterns did you observe in the confusion matrix?**
> **Answer:** MobileNetV2 would show the brightest diagonal in the confusion matrix since it had the highest accuracy at **80.70%**, meaning most predictions fell on the correct class. EfficientNetB0 and ResNet50, having lower accuracies of **77.30%** and **76.60%** respectively, would show more off-diagonal values, especially among herbals with similar leaf structures like **mikania_micrantha**, **hyptis_suaveolens**, and **sampa_sampalukan**.

---

### G. Real-World Application

**17. What are the risks of deploying an inaccurate model?**
> **Answer:** The risks are especially serious for herbal plant identification since these plants are used for medicinal purposes. With the best model only reaching **80.70% validation accuracy**, roughly 1 in 5 predictions could be wrong. A user could be misled into consuming a toxic or incorrect plant instead of the intended remedy. Misidentifying plants like **kataka_taka** or **sambong** could cause allergic reactions or health emergencies, making high accuracy critical before any real-world deployment.

**18. How can this system be integrated into a mobile/web app?**
> **Answer:** The trained MobileNetV2 model can be converted into a TensorFlow Lite (`.tflite`) file to reduce its size for mobile deployment. This lightweight model is then embedded into a smartphone app where a user points their camera at a herbal plant such as **Mayana** or **Pansit-pansitan**, and the app runs the model on-device to instantly identify the plant and display its medicinal uses without needing an internet connection.
