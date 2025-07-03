# Liver Tumor Segmentation – LITS Challenge

A comprehensive deep learning pipeline for liver tumor segmentation using hybrid U-Net Transformer architecture, developed for the LITS (Liver Tumor Segmentation) Challenge.

## 🎯 What This Repository Can Do

This project provides a complete end-to-end solution for medical image segmentation with the following key capabilities:

- **🔬 Medical Image Processing**: Convert NIfTI (.nii) to PNG, normalize intensity, resize images
- **🧠 Advanced Deep Learning**: Hybrid U-Net Transformer model for precise segmentation
- **📊 Comprehensive Evaluation**: Multiple medical imaging metrics (Dice, IoU, F1, etc.)
- **📈 Visualization Tools**: Training progress, data exploration, and prediction analysis
- **⚡ Production Ready**: Model saving, loading, and inference capabilities

📖 **[View Complete Capabilities →](CAPABILITIES.md)**

## 🚀 Quick Start

1. **Install Dependencies**
   ```bash
   pip install -r requirements.txt
   ```
   Or manually:
   ```bash
   pip install tensorflow nibabel SimpleITK numpy matplotlib scikit-learn pillow scipy
   ```

2. **Get the Dataset**
   - Download from [LITS Challenge on CodaLab](https://competitions.codalab.org/competitions/17094)
   - ⚠️ Account registration and access request required

3. **Run the Pipeline**
   - Open `lits.ipynb` in Jupyter Notebook
   - Execute cells sequentially for complete workflow

📋 **[Detailed Usage Guide →](USAGE_GUIDE.md)**

## 🏗️ Architecture

### Hybrid U-Net Transformer Model
- **U-Net Backbone**: Proven architecture for medical image segmentation
- **Transformer Blocks**: Enhanced feature representation and long-range dependencies
- **Multi-Scale Features**: Skip connections preserve fine-grained details
- **2D Approach**: Efficient processing of 3D volumetric data as 2D slices

### Key Features
- **Multi-class Segmentation**: Background, liver tissue, and tumor regions
- **Advanced Training**: Learning rate scheduling, early stopping, custom callbacks
- **Robust Evaluation**: Medical imaging specific metrics and visualizations

## 📊 Performance

- **Training Time**: ~24-25 hours per epoch (CPU), significantly faster on GPU
- **Model Size**: Optimized for 128x128 input images
- **Metrics**: Dice coefficient, IoU, precision, recall, F1-score, specificity
- **Scalability**: Batch processing for multiple patients

## 📁 Project Structure

```
├── lits.ipynb           # Main pipeline notebook
├── README.md            # This file
├── CAPABILITIES.md      # Detailed feature overview
├── USAGE_GUIDE.md       # Step-by-step instructions
├── QUICK_REFERENCE.md   # Quick overview and setup
└── requirements.txt     # Python dependencies
```

## 🔧 Technical Details

### Data Pipeline
1. **Input**: NIfTI (.nii) 3D volumetric CT scans
2. **Preprocessing**: Conversion to PNG slices, normalization, resizing
3. **Training**: 2D model training with advanced callbacks
4. **Output**: Segmentation masks and performance metrics

### Model Components
- **Encoder-Decoder Architecture**: U-Net style with skip connections
- **Transformer Integration**: Self-attention mechanisms for better feature learning
- **Custom Loss Functions**: Optimized for medical segmentation tasks
- **Evaluation Suite**: Comprehensive metrics for medical image analysis

## 🎓 Educational Value

Perfect for learning:
- **Medical Image Processing**: Real-world healthcare AI application
- **Deep Learning**: Advanced CNN architectures and training strategies
- **Computer Vision**: Segmentation techniques and evaluation methods
- **Data Science**: End-to-end ML pipeline development

## 🤝 Use Cases

- **Research**: Medical imaging studies and algorithm development
- **Clinical**: Radiologist decision support (research use)
- **Education**: Learning medical AI and segmentation techniques
- **Benchmarking**: Compare different segmentation approaches

## 🚧 Development Notes

This project was developed as a learning experience focusing on:
- Building complete ML pipelines from scratch
- Understanding medical imaging data workflows
- Implementing state-of-the-art segmentation architectures
- Creating comprehensive evaluation and visualization tools

**Hardware Requirements**: GPU recommended for training, though CPU training is supported (longer duration).

