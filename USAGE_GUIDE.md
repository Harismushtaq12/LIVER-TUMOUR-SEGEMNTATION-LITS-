# Usage Guide - Liver Tumor Segmentation

This guide explains how to use the liver tumor segmentation pipeline effectively.

## 🚀 Quick Start

### Prerequisites
```bash
pip install tensorflow nibabel SimpleITK numpy matplotlib scikit-learn pillow scipy
```

### Basic Workflow

1. **Prepare Your Data**
   - Obtain CT scan data in NIfTI (.nii) format from the LITS Challenge
   - Convert to PNG slices (handled by the preprocessing functions)
   - Organize data in training and testing directories

2. **Run the Pipeline**
   - Open `lits.ipynb` in Jupyter Notebook
   - Execute cells sequentially to:
     - Load and preprocess data
     - Train the segmentation model
     - Evaluate performance
     - Visualize results

## 📝 Step-by-Step Instructions

### Data Preparation
```python
# The notebook includes functions to:
# 1. Load PNG files from directories
training_files = list_png_files("path/to/training/data")
testing_files = list_png_files("path/to/testing/data")

# 2. Preprocess images
X_train, y_train = load_and_preprocess_png(training_files)
X_test = load_and_preprocess_png(testing_files, is_training=False)
```

### Model Training
```python
# 1. Create the hybrid U-Net transformer model
model = create_hybrid_unet_transformer_2d(input_shape=(128, 128, 1))

# 2. Set up training callbacks
early_stopping = EarlyStopping(patience=5, restore_best_weights=True)
lr_scheduler = LearningRateScheduler(lr_schedule)

# 3. Train the model
history = model.fit(
    X_train, y_train,
    validation_split=0.2,
    epochs=50,
    batch_size=16,
    callbacks=[early_stopping, lr_scheduler]
)
```

### Model Evaluation
```python
# 1. Make predictions
predictions = model.predict(X_test)

# 2. Calculate metrics
dice_score = dice_coefficient(y_true, y_pred)
iou_score = jaccard_index(y_true, y_pred)

# 3. Visualize results
visualize_2d_predictions(X_test, predictions, num_samples=6)
```

## 🔧 Key Functions Reference

### Data Processing Functions
- `list_png_files(directory)` - List all PNG files in a directory
- `load_and_preprocess_png(file_paths)` - Load and preprocess PNG images
- `normalize_image(image)` - Normalize image intensity values
- `resize_image(image, target_size)` - Resize image to target dimensions

### Model Functions
- `create_hybrid_unet_transformer_2d(input_shape)` - Create the segmentation model
- `transformer_block_2d(inputs, num_heads, ff_dim)` - Transformer block component

### Evaluation Functions
- `dice_coefficient(y_true, y_pred)` - Calculate Dice coefficient
- `jaccard_index(y_true, y_pred)` - Calculate IoU score
- `precision(y_true, y_pred)` - Calculate precision
- `recall(y_true, y_pred)` - Calculate recall
- `f1_score(y_true, y_pred)` - Calculate F1 score
- `specificity(y_true, y_pred)` - Calculate specificity

### Visualization Functions
- `plot_random_images_training(volumes, masks)` - Show training samples
- `plot_random_images_testing(volumes)` - Show test samples
- `visualize_2d_predictions(images, predictions)` - Compare predictions

## 📊 Expected Results

### Performance Metrics
- **Dice Coefficient**: 0.7-0.9 (typical range for medical segmentation)
- **IoU Score**: 0.6-0.8 (Intersection over Union)
- **Precision/Recall**: Balanced scores indicating model reliability

### Training Characteristics
- **Convergence**: Model typically converges within 20-30 epochs
- **Training Time**: ~24-25 hours per epoch on CPU, much faster on GPU
- **Memory Usage**: Depends on batch size and image dimensions

## 🎯 Customization Options

### Modify Model Architecture
```python
# Adjust model parameters
model = create_hybrid_unet_transformer_2d(
    input_shape=(256, 256, 1),  # Different image size
    num_classes=3               # Background, liver, tumor
)
```

### Training Parameters
```python
# Customize training
model.compile(
    optimizer=Adam(learning_rate=0.001),
    loss='sparse_categorical_crossentropy',
    metrics=['accuracy', dice_coefficient]
)
```

### Data Augmentation
Consider adding data augmentation for improved model generalization:
- Rotation, flipping, scaling
- Brightness/contrast adjustments
- Elastic deformations

## 🔍 Troubleshooting

### Common Issues
1. **Memory Errors**: Reduce batch size or image dimensions
2. **Slow Training**: Use GPU acceleration or reduce dataset size
3. **Poor Performance**: Check data quality and preprocessing steps
4. **File Loading Errors**: Verify file paths and formats

### Performance Optimization
- Use mixed precision training for faster computation
- Implement data generators for large datasets
- Consider 3D models for better spatial understanding
- Apply transfer learning from pre-trained models

## 📈 Advanced Usage

### Ensemble Methods
Combine multiple models for improved accuracy:
```python
# Train multiple models with different initializations
models = [create_hybrid_unet_transformer_2d() for _ in range(3)]
# Average predictions for final result
```

### Cross-Validation
Implement k-fold cross-validation for robust evaluation:
```python
from sklearn.model_selection import KFold
kf = KFold(n_splits=5, shuffle=True, random_state=42)
# Train and evaluate on different data splits
```

This pipeline provides a solid foundation for liver tumor segmentation research and can be adapted for various medical imaging applications.