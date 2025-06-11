Liver Tumor Segmentation – LITS Challenge (CodaLab)
This project is a liver tumor segmentation pipeline built for the LITS (Liver Tumor Segmentation) Challenge. It was part of an exploratory effort to understand medical imaging, specifically how 3D volumetric CT scan data is processed and used to train deep learning models for medical segmentation tasks.

📁 Dataset
The dataset used in this project comes from the LITS Challenge hosted on CodaLab.

🔗 Dataset access link: https://competitions.codalab.org/competitions/17094

⚠️ You will need to create an account and request access to download the dataset from CodaLab.

🧪 Preprocessing
The original dataset is provided in NIfTI (.nii) format, which contains 3D volumetric data (CT scans and segmentation labels).

To simplify and enable training on 2D models, we:

Converted the NIfTI files into individual PNG slices

Saved both image and corresponding mask slices

Structured the data into a format suitable for training using common deep learning libraries

⚙️ Project Overview
Data preprocessing from .nii to .png

2D segmentation model for liver and tumor detection

Training loop and visualization tools

Local training setup (note: a single epoch can take ~24–25 hours locally)

🚧 Notes
This project was developed and run locally on limited hardware and trained for only one epoch, primarily as a learning experience. The focus was on building the pipeline from scratch and understanding the data processing workflow in medical imaging.

