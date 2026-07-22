***Q1: Choosing the Right Approach***
-----
You are tasked with identifying whether a product is missing its label on an assembly line. The products are visually similar except for the label.

 ```text
Q: Would you use classification, detection, or segmentation? Why? What would be your fallback if the first approach doesn’t work?
```

Answer: Detection would work better for these kind of task because it would light-weight in comparision with ohters such as classification and segmentation. As this application is for real-time detection so the light-weight approach will lead good results.I used yolov8 here, it beats all other options in this range for real-time tasks.
Why the classification and Segmenatation doesn't works well here?
becuase in the case of classification the we need to go with the two-stage approach as first we need to propose our intereset then classifying it into the lables.And segmentation is useless here as we dont need any pixel lavel opreation.
 
***Q2: Debugging a Poorly Performing Model***
---
You trained a model on 1000 images, but it performs poorly on new images from the factory.
 
```text
Q: Design a small experiment or checklist to debug the issue. What would you test or visualize?
```
Answer: There are so-many problems which can occur in such kind of applications.In brief i classified these in two parts.
- Data Set Problems
- Archetecture problems
- Model Accuracy Problems

**Dataset Problems:** We need vary diverse dataset for these kind of PPE models. Becuase most of the input images are from CCTV camera. And the
angle of input images are not straight-forward. Class imbalances may lead to the problems. Glaves and hand may blurry due to the movements.

**Archetecture problems:** There is very high complexity for the model to detect the gloves in such a big region. The quality of images will decrease over the layers. The poolong and padding layers will be the crusial part , may lead to the problems.

**Model Accuracy Problems:** model accuracy, over fitting under fitting may lead to the poor performance.

---
  
***Q3: Accuracy vs Real Risk***
---
Your model has 98% accuracy but still misses 1 out of 10 defective products.
 
```text
Q: Is accuracy the right metric in this case? What would you look at instead and why?
```
Answer: Accuracy solely never is a  good metrics. Combined the f1-score and confusion metrics would be a good practice always.
In such case, if we dont want to false alerts we need to have good Precision. and if we want to minimise the False Negatives.
---
***Q4: Annotation Edge Cases***
---
You’re labeling data, but many images contain blurry or partially visible objects.

```text
Q: Should these be kept in the dataset? Why or why not? What trade-offs are you considering?
```
Answer:Yes in a limit it will be good for the training. Because it will worked as datagumentation our model will learn to fight the real-word conditions and escaped from overfitting. In this project i got a file in validation which didn't have any label present i keep it there.

