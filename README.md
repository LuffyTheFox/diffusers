Introduction:

Fork from ShivamShirao diffusers repo https://github.com/ShivamShrirao/diffusers optimized for Anything v3.0 

This fork will use training and class images from your Google Drive. Quick and easy usage. 

Everything is preconfigured for 36 (N) training pictures via following formula:

Number of subject images (instance) = N

Number of class images (regularization) = N x 12

Maximum number of Steps = N x 80 (this is what I'm tweaking right now but between 80 and 100 should be enough)

Learning rate = 1e-6

Learning rate schedule = polynomial

Learning rate warmup steps = Steps / 10

Quick start guide:

1) Download training pictures from here: https://drive.google.com/drive/folders/1eYmoi_ukumAsvOf9M7-0rWYFjPyoed1r?usp=share_link
And save them to: (GoogleDrive\SD\genshin) directory
2) Download class pictures from here: https://drive.google.com/drive/folders/1XGfyLeqTcF4CMplcC1atxR0CtFHeVfGA?usp=share_link
And save them to: (GoogleDrive\SD\waifu) directory

Open this Google Colab and start training:

[![DreamBooth Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/LuffyThefox/diffusers/blob/main/examples/dreambooth/DreamBooth_Anything.ipynb)

After training model.ckpt file for AUTOMATIC1111 Web UI will be saved to (GoogleDrive\SD\ckpt\(number of steps)\model.ckpt) directory

Use the table below to choose the best flags based on your memory and speed requirements. Tested on Tesla T4 GPU.
Everything is already preconfigured for free version of Google Colab.

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
