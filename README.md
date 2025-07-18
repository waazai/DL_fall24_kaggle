# Math Answer Verification

This repository contains Jupyter notebooks used for a Kaggle style math-answer verification project.
The notebooks fine-tune Meta's Llama 3.1–8B model with LoRA using the [unsloth](https://github.com/unslothai/unsloth) library.
Our goal is to check whether a proposed solution to a math question is correct.

## Contents

- `DL_Midterm_promptWithSolution.ipynb` – Baseline notebook that trains on the provided dataset including question, answer and solution.
- `DL_Midterm_hyperparameter.ipynb` – Hyperparameter tuning with Optuna to find better training settings.
- `DL_Midterm_finalPrompt.ipynb` – Final training notebook with the prompt refined for better accuracy.
- `DL_inference.ipynb` – Shows how to load a saved LoRA adapter and run inference.

## Dataset

All notebooks download the `ad6398/nyu-dl-teach-maths-comp` dataset from Hugging Face. Each record contains a math question, an answer, a step-by-step solution and a label (`True` or `False`) indicating whether the answer is correct. The code converts these records into prompts for supervised fine-tuning.

## Pretrained Models

We host checkpoints on Google Drive:

- [Prompt with solution](https://drive.google.com/drive/folders/13FB1UYpm7dncr148TCRBpBvX1NzG5OiW?usp=sharing)
- [Hyperparameter tuning](https://drive.google.com/drive/folders/10VLgVilh9pRCuzBXnsK2k4E4YUG4i620?usp=sharing)
- [Final prompt](https://drive.google.com/drive/folders/19YsUjP9oKQqYIX2f5drThPc3dl-MCeVk?usp=drive_link)

## Usage

The notebooks were developed for Google Colab. Each notebook mounts Google Drive and installs the dependencies using pip.
Run the cells sequentially to reproduce the fine-tuning or to generate answers with the trained model. When training finishes, the LoRA adapter weights are saved back to Drive.

## Inference Example

`DL_inference.ipynb` demonstrates how to load the LoRA weights and generate predictions using `transformers.TextGenerationPipeline`.
Adjust the `model_path` variable to point to your saved checkpoint and run the final cell to see the predicted `True`/`False` output for a sample question.

---

These materials were created for a university deep learning course and are made available for educational purposes.
