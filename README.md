# KORIE
KORIE: Korean Receipt Dataset for Detection, OCR, and Information Extraction

KORIE is an expanding benchmark dataset of Korean retail receipts designed for research in:

- Text Detection

- Optical Character Recognition (OCR)

- Information Extraction (IE)

The dataset contains scanned and mobile-captured thermal receipts exhibiting real-world degradation such as fading, banding, blur, skew, glare, and physical creases. KORIE includes fine-grained annotations for bounding boxes, OCR transcriptions, and structured item-level fields.

This repository hosts the dataset, dataset splits, annotation files, baseline results, and evaluation scripts used in the accompanying manuscript.

## Samples
Two sample image/label pairs are provided in `Samples/` to demonstrate the dataset format.

📌 Key Features
✓ Expanding Real-World Dataset

- 774 receipts in the initial release
- Includes both flatbed-scanned and mobile-captured receipts
- Mobile images introduce authentic in-the-wild artifacts (perspective distortion, shadows, glare, motion blur)
- Dataset will continue to expand with additional stores, imaging conditions, and geographic diversity

✓ Multi-Task Benchmark

KORIE supports three research tracks:
1. Text Detection

  - YOLOv9, YOLOv10, YOLOv11
  - DINO-DETR (ResNet-50, Swin-L)
  - Weakly Supervised Object Localization (WSOL) baselines

2. OCR

  - Tesseract / pytesseract
  - EasyOCR
  - PaddleOCR
  - Attention-based BiGRU (trained on KORIE OCR crops)

3. Information Extraction (IE)

  - Zero-shot LLM extraction using Llama-3.x and Qwen-2.5 models
  - Structured outputs: merchant fields, dates, totals, item tables

📊 Dataset Statistics (v1.0)

- 774 receipts
- 17,587 word-level OCR crops
- 2,886 structured IE annotations
- Rich fields include:
  - Merchant name, date, time, receipt number
  - Item name, brand, category
  - Quantity, unit, unit price, line total
  - Subtotals, taxes, and total amounts


🧪 Baseline Results
Detection
| Model   | mAP@0.50  | mAP@0.50:0.95 |
| ------- | --------- | ------------- |
| YOLOv11 | **0.888** | **0.762**     |
| YOLOv10 | 0.860     | 0.751         |
| YOLOv9  | 0.856     | 0.747         |

OCR

| Model     | CER (%)   | WER (%)   |
| --------- | --------- | --------- |
| PaddleOCR | **15.84** | **26.73** |
| EasyOCR   | 17.36     | 31.43     |
| Tesseract | 25.43     | 35.26     |


Information Extraction (Zero-shot LLMs)

Best model: Qwen2.5-3B-Instruct

- Overall Accuracy: 23.16%
- Overall F1: 25%

IE remains challenging due to noisy OCR, thermal artifacts, and domain mismatch in Korean text.

YAML configuration file should contain the entity schema for the receipt IE task. It is used by the data loader/training pipeline to map extracted labels to the predefined entity set:
Description, Quantity, TotalPrice, Price, Item, MerchantName, Total, Subtotal, TotalTax, TransactionDate, TransactionTime, Tip, MerchantPhoneNumber, ReceiptNumber, MerchantAddress, Item_barcode, ProductCode.


📥 Download

🎯 Key Information Detection

| Split | Size | Link |
|-------|-------|------|
| Train | ~1 GB | [Download from Google Drive](https://drive.google.com/file/d/1M3C_xG8Vg47DIbPP2fYpXs6mv5t6YOVq/view?usp=sharing) |
| Val   | ~346 MB | [Download from Google Drive](https://drive.google.com/file/d/15wXqZUzWaYEJu-rWZwCPuMvHFMZgWQOD/view?usp=sharing) |
| Test  | ~332 MB | [Download from Google Drive](https://drive.google.com/file/d/1UJZIcTX38FnMa8PZHYj--5OJ8-deSMRI/view?usp=sharing) |

🔍 OCR Dataset

| Split | Size | Link |
|-------|-------|------|
| Train | ~58.4 MB | [Download from Google Drive](https://drive.google.com/file/d/1I4BzOqKgF7zbNPlNeood4f7g8pi2xh26/view?usp=sharing) |
| Val   | ~19.1 MB | [Download from Google Drive](https://drive.google.com/file/d/1v_0iGpBjB5WdWOeKI4C903eeqkRBjTsM/view?usp=sharing) |
| Test  | ~18.6 MB | [Download from Google Drive](https://drive.google.com/file/d/1GtEzSUA2wTNfOujO67-JEZ_PLpJOdBhg/view?usp=sharing) |



📝 Item Information Extraction

📬 Contact

For questions, collaboration, or dataset contributions, please contact:
Mahmoud SalahEldin Kasem
📧 mahmoud.salah@aun.edu.eg

