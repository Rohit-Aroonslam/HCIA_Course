# HCIA-AI-Course

Practical labs completed as part of the **Huawei HCIA-AI V4.0** certification course (Experiment Guide, section 7). All credit for the lab guides, datasets, and course materials belongs to Huawei — this repo holds my completed work and notes.

## Machine Learning Lab 7.1
`Machine Learning Lab 7.1/`

Five experiments in Google Colab using scikit-learn and NumPy:
- **Linear regression** — house area vs price, then again from scratch with gradient descent
- **Logistic regression** — predicting whether a room is rented from its rent and area
- **Decision tree** — the tennis dataset
- **K-means clustering** — 3 and 4 clusters, plus K-means built from scratch

## Deep Learning Lab 7.2
`Deep Learning Lab 7.2/`

A fully connected neural network built with NumPy only and trained on MNIST. Compares four optimizers (SGD, Momentum, AdaGrad, Adam) using loss curves and test accuracy.

## AI Development Framework 7.3
`AI Development Framework 7.3/`

PyTorch basics (tensors, `Dataset` and `DataLoader`) and three models:
- **LeNet** on CIFAR-10 — 59.52% test accuracy after 20 epochs (the guide trains 50)
- **ResNet-50** on a flower photo dataset (5 classes) — 57.69% test accuracy, trained from scratch for 5 epochs
- **TextCNN** on IMDB movie reviews (sentiment analysis) — 84.28% test accuracy

Changes from the guide: ResNet-50 uses batch size 32 and learning rate 0.01 (instead of batch size 1 and 0.1) so that it trains properly on a GPU.

## Model Deployment and Application 7.4
`Model Deployment Lab 7.4/`

Runs the quantized DeepSeek-R1-Distill-Qwen-1.5B model locally with llama.cpp on a Windows laptop (CPU only):
- **Experiment 1** — chat with the model in the command line and compare parameters such as `--temp`
- **Experiment 2** — start `llama-server` and call it from Python with `requests` (original and OpenAI-compatible endpoints) and with the `openai` library

As an extra, the server was protected with an API key (`--api-key`) and briefly shared through a free Cloudflare quick tunnel. The key and the link are not included in this repo.

## Datasets and downloads
Large files are not stored in this repo. Download them from the sources below.
- ML and DL datasets (`Dataset.zip`): https://certification-data.obs.cn-north-4.myhuaweicloud.com/ENG/HCIA-AI/V4.0/Dataset.zip
- Flower photos (7.3): https://ascend-professional-construction-dataset.obs.myhuaweicloud.com/deep-learning/flower_photos_train.zip and https://ascend-professional-construction-dataset.obs.myhuaweicloud.com/deep-learning/flower_photos_test.zip
- llama.cpp for Windows (7.4): https://certification-data.obs.cn-north-4.myhuaweicloud.com/CHS/HCIA-AI/V4.0/chapter5/llama_cpp.zip
- Model file (7.4, about 1.5 GB): https://huggingface.co/bartowski/DeepSeek-R1-Distill-Qwen-1.5B-GGUF/resolve/main/DeepSeek-R1-Distill-Qwen-1.5B-Q6_K_L.gguf

MNIST, CIFAR-10, and IMDB are downloaded automatically by the notebooks.

## Setup
- **Labs 7.1 to 7.3** run in Google Colab (a T4 GPU is recommended for 7.3). Colab deletes files when a session ends, so upload `Dataset.zip` again in each new session. 7.3 downloads its own data partway through, so run the cells one at a time from top to bottom.
- **Lab 7.4** runs on a local machine. Extract `llama_cpp.zip`, put the model file in the same folder, and install the Python libraries with `pip install requests openai notebook`. Call the server from a local Jupyter notebook, since Colab cannot reach `localhost` on your computer.
