## Conclusion

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
