# Laboratory-Work-5-Activity: Herbal Plant Classification

## PART 12: Performance Comparison Table

| Model | Train Acc | Train Loss | Val Acc | Val Loss | Precision | Recall | F1 | AUC |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| **LW3 Baseline CNN** | 0.9520 | 0.0828 | 0.6080 | 1.9856 | 0.6232 | 0.6080 | 0.6056 | 0.9423 |
| **LW4 Improved CNN** | 0.7985 | 1.6977 | 0.7450 | 0.9295 | 0.7598 | 0.7450 | 0.7467 | 0.9051 |
| **Teachable Machine** | 0.9859 | 0.0052 | 0.9750 | 0.1910 | 0.0000 | 0.0000 | 0.0000 | 0.0000 |
| **MobileNetV2** | **0.9135** | **0.3544** | **0.9617** | **0.2182** | **0.9618** | **0.9620** | **0.9613** | **0.9953** |
| **EfficientNetB0** | 0.7294 | 1.1835 | 0.9017 | 0.7537 | 0.7731 | 0.7171 | 0.7182 | 0.9615 |
| **ResNet50** | 0.7938 | 0.7768 | 0.9263 | 0.4098 | 0.8095 | 0.7887 | 0.7870 | 0.9613 |

---

## GUIDE QUESTIONS (FINAL REFLECTION) 

### A. Model Performance 

**1. Which pre-trained model achieved the highest accuracy? Why?**
> **Answer:** MobileNetV2 with an accuracy rate of 96.17%. It is designed to be highly efficient, meaning it can learn the most important features of an image very quickly without getting distracted by unnecessary details.

**2. Which model had the lowest performance? What could be the reason?**
> **Answer:** EfficientNetB0 with an accuracy rate of 90.17%. While it is a very powerful model, it usually requires very specific image sizes and more training time to reach its full potential compared to the others.

**3. How did loss values compare across models?**
> **Answer:** MobileNetV2 had the lowest final training loss at 0.3544 and validation loss of 0.2182, which means it learned the most. EfficientNetB0 stopped at training loss 1.1835 and val loss 0.7537 after just 3 epochs. Overall, MobileNetV2 had the best loss values by a big margin.

### B. Evaluation Metrics

**4. Why is accuracy not enough to evaluate a model?**
> **Answer:** Accuracy just tells you how many predictions were correct in total, but it doesn't tell you the full story. For example, if one class has very few images, the model could just ignore that class and still get high accuracy. That's why we also look at Precision, Recall, and F1-score — they show how the model performs on each individual class.

**5. Which model had the best F1-score? What does it indicate?**
> **Answer:** MobileNetV2 had the best F1-score at 0.96. F1-score is the balance between Precision and Recall, so a high F1 means the model is both accurate and consistent across all herbal plant classes like **Sambong**, **Yerba Buena**, and **Mayana**.

### C. Confusion Matrix Analysis 

**7. Which classes were frequently misclassified?**
> **Answer:** The hardest classes were those with very similar leaf structures, such as different green leafy herbs. In lower-performing models, certain herbal leaves were frequently confused when the lighting or leaf shape overlapped.

**8. What patterns did you observe in the confusion matrix?**
> **Answer:** The diagonal of the confusion matrix was mostly bright for MobileNetV2. For lower-performing models, errors were spread out among herbal plants with similar textures, showing that the models struggled with subtle botanical differences.

### G. Real-World Application

**17. What are the risks of deploying an inaccurate model?**
> **Answer:** The risks are very high with herbal plants because they are used for medicinal purposes. If the model misidentifies a plant, a user might consume a species that is toxic or causes an allergic reaction instead of the intended remedy. For example, mistaking a poisonous plant for **Sambong** or **Kataka-taka** could lead to a health emergency.

**18. How can this system be integrated into a mobile/web app?**
> **Answer:** We convert the trained model into a TensorFlow Lite file. This "mini-brain" is put into a mobile app so it can run directly on a smartphone. A user simply points their camera at a herbal plant (like **Mayana** or **Pansit-pansitan**), and the app instantly identifies it.
