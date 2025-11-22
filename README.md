# Cultural Design Image Classification Dataset

This repository contains a curated dataset of cultural and creative design images for the task of distinguishing AI-generated vs. human-created patterns. It was used to train and evaluate the VOLO-based classification framework in “Data Analysis of AI-Generated and Human-Created Images Leveraging Deep Learning Visual Converter.”

---

## 📦 Dataset Contents

- **images/**  
  ├─ train/  
  │   ├─ ai_generated/ (350 images)  
  │   └─ human_created/ (350 images)  
  └─ test/  
      ├─ ai_generated/ (150 images)  
      └─ human_created/ (150 images)  

- **labels.csv**  
  A CSV file with columns:  
  ```csv
  filename,label,split
  train/ai_generated/img_001.jpg,ai_generated,train
  test/human_created/img_851.jpg,human_created,test
  ```

- **LICENSE.txt**  
  Terms of use and redistribution.

- **README.md**  
  This file.

---

## 📖 Description

The dataset comprises **1,000** high-resolution (~224×224 px) images, evenly split between:

- **AI-Generated:** Artistic designs synthesized via advanced prompt-engineering and diffusion/GAN pipelines.
- **Human-Created:** Aesthetic patterns crafted by designers, vetted by domain experts.

Images cover a variety of cultural motifs—textiles, architectural ornamentation, folk art, and more—under diverse lighting, pose, and style conditions.

---

## 🔄 Preprocessing & Splits

1. **Resizing & Normalization**  
   All images were resized to 224×224 px and normalized (zero mean, unit variance per channel).

2. **Data Augmentation**  
   Applied random flips, rotations (±15°), crops, brightness/contrast jitter, and Gaussian noise during training.

3. **Train/Test Split**  
   - **70%** training (700 images: 350 AI-generated, 350 human-created)  
   - **30%** testing  (300 images: 150 AI-generated, 150 human-created)

---

## 🚀 Usage

Clone the repo and load images via your favorite framework:

```bash
git clone https://github.com/your-org/cultural-design-dataset.git
```

Example in PyTorch:

```python
from torchvision import datasets, transforms

transform = transforms.Compose([
    transforms.Resize((224,224)),
    transforms.ToTensor(),
    transforms.Normalize(mean=[0.485,0.456,0.406],
                         std =[0.229,0.224,0.225])
])

train_ds = datasets.ImageFolder("images/train", transform=transform)
test_ds  = datasets.ImageFolder("images/test",  transform=transform)
```

---

## 📬 Contact

For questions or contributions, please open an issue or contact the author at visionlangai@gmail.com
