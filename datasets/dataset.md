Dataset Title: RSICD (Remote Sensing Image Captioning Dataset)

Usage of Dataset:
Used for training, validating, and benchmarking remote sensing image captioning models. It serves as the primary data source for learning the mapping between aerial imagery and natural language descriptions.


Dataset Information


Dataset Name: RSICD (Remote Sensing Image Captioning Dataset)


Source: Lu et al. (2017), available via Hugging Face


Domain: Remote Sensing / Aerial Imagery


Task: Image Captioning, Text-Image Retrieval


Problem Type: Multimodal Learning (Computer Vision + Natural Language Processing)


File Format: Images (JPG), Annotations (JSON/Text)


Dataset Link: https://huggingface.co/datasets/rsicd
Kaggle Link: https://www.kaggle.com/datasets/arampacha/rsicd-image-captioning


**Dataset Overview**


Total Records: 10,921 Images


Labeled Records: Yes, 5 captions per image (Total >50,000 sentences)


Classes: ~30 Scene Classes (e.g., Airport, Bridge, Beach, Center, Church, Farmland, Forest, Industrial, Meadow, Mountain, Park, Parking, Playground, Pond, Port, Railway Station, Resort, River, School, Sparse Residential, Square, Stadium, Storage Tanks, Viaduct)


Annotation Type: Manual Human Annotation


Why This Dataset?
RSICD is chosen because it is one of the largest and most widely used datasets for remote sensing captioning. It presents unique challenges compared to natural image datasets (like COCO) due to the overhead perspective, scale variation, and specific remote sensing objects. It allows for robust evaluation of the model's ability to understand complex aerial scenes.


Features Used


Feature 1: Remote Sensing Imagery (Standardized to 224x224 pixels) - The visual input for the model.


Feature 2: Natural Language Captions - Five ground-truth sentences per image describing the scene content and relationships.


Feature 3: Scene Categories - High-level labels used for optional classification or conditioning tasks.


Summary
The RSICD dataset provides a comprehensive collection of annotated aerial images, enabling the development and testing of the fusion-based image captioning system. It ensures the model is capable of accurately describing diverse geographical features and man-made structures from an overhead perspective.
