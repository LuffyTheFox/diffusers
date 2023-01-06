Fork from ShivamShirao diffusers repo https://github.com/ShivamShrirao/diffusers optimized for Anything v3.0 and Genshin Impact characters

This fork will use training and class images from your Google Drive. Everything is preconfigured for 36 training pictures.

Training pictures located here: https://drive.google.com/drive/folders/1eYmoi_ukumAsvOf9M7-0rWYFjPyoed1r?usp=share_link
Class pictures located here: https://drive.google.com/drive/folders/1XGfyLeqTcF4CMplcC1atxR0CtFHeVfGA?usp=share_link

You can now convert to ckpt format using this script to use in UIs like AUTOMATIC1111. https://github.com/LuffyTheFox/diffusers/raw/main/scripts/convert_diffusers_to_original_stable_diffusion.py Check colab notebook for example usage.

[![DreamBooth Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/LuffyThefox/diffusers/blob/main/examples/dreambooth/DreamBooth_Anything.ipynb)

Use the table below to choose the best flags based on your memory and speed requirements. Tested on Tesla T4 GPU.

| `fp16` | `train_batch_size` | `gradient_accumulation_steps` | `gradient_checkpointing` | `use_8bit_adam` | GB VRAM usage | Speed (it/s) |
| ---- | ------------------ | ----------------------------- | ----------------------- | --------------- | ---------- | ------------ |
| fp16 | 1                  | 1                             | TRUE                    | TRUE            | 9.92       | 0.93         |
| no   | 1                  | 1                             | TRUE                    | TRUE            | 10.08      | 0.42         |
| fp16 | 2                  | 1                             | TRUE                    | TRUE            | 10.4       | 0.66         |
| fp16 | 1                  | 1                             | FALSE                   | TRUE            | 11.17      | 1.14         |
| no   | 1                  | 1                             | FALSE                   | TRUE            | 11.17      | 0.49         |
| fp16 | 1                  | 2                             | TRUE                    | TRUE            | 11.56      | 1            |
| fp16 | 2                  | 1                             | FALSE                   | TRUE            | 13.67      | 0.82         |
| fp16 | 1                  | 2                             | FALSE                   | TRUE            | 13.7       | 0.83         |
| fp16 | 1                  | 1                             | TRUE                    | FALSE           | 15.79      | 0.77         |
