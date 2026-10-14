Dataset
---
URL: https://zenodo.org/records/7711810

About dataset: A novel dataset based on Sentinel-2 satellite images covering 13 different spectral bands and consisting of 10 classes with in total 27,000 labeled images.
The dataset provides images in two formats: a multispectral version containing 13 spectral bands and an RGB-only version. In this work, the EuroSAT_RGB subset was used, which includes the optical Red, Green, and Blue bands encoded as JPEG images.

citation/attribution: https://zenodo.org/records/7711810

Data split strategy
---

**Keras**

A total of 2000 images from each class is used to make the data balanced across all classes.
1600 for training and 400 for validation test.
remaining images(unseen images) are used for model evaluation.

**PyTorch**

Stratified Data is used to train the baseline model.
The augmentation is performed to increase the data and improve the model.

## Conclusion

**PyTorch**

Here also similar model from Keras implemented as baseline model to train on stratified dataset which gave good results. Then I performed the data augmentation to balance the number of images in classes which is 3000. two models one again baseline model and other improved model with Early stopping, Batch normalization, dropout, gradient clipping and LRscheduler were used to improve the models performance trained on augmented dataset.

- Best metrics on test data evaluation:
    - test loss: 0.357 - stratified
    - test accuracy: 0.874 - stratified
    - test loss: 0.3619 - augmentation
    - test accuracy: 0.872 - augmentation
    - test loss: 0.1673 - augmentation + model improvement
    - test accuracy: 0.9431 - augmentation + model improvement

  model trained using pytorch performed well on data augmentation and model improvement. I reached this reduction in test loss in many trials / training. tweaking the parameters such as patience, LR, dropout, epochs, etc.

**Keras**

The custom CNN trained model shows good performance on the EuroSAT_RGB multiclass dataset consisting of 10 land cover classes, with the following best metrics achieved at epoch 18.
- Best metrics:
  - train_accuracy: 0.9081 
  - train_loss: 0.2549 
  - val_accuracy: 0.8547 
  - val_loss: 0.4643

- strengths:
  - The model shows good generalization across most of the land cover classes.
  - The model is evaluated with both test/validation data and unseen images indicating reasonable robustness.
  - The architecture is compact and efficient, with approximately 680k+ parameters.
- Challenges:
  - the model exhibits class confusion among Vegetation related categories, such as AnnualCrop, HerbaceousVegetation, and River likely due to their visual similarity.
  - The observed gap between training and validation accuracy suggests mild overfitting, which can be improved by regularization or augmentation.
