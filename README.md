# OmniGen Dockerized

This project provides a Dockerized setup for running the [OmniGen-v1](https://huggingface.co/Shitao/OmniGen-v1) model using Gradio. It handles all dependencies, model downloading, and starts a web UI on port `7860`.

---

## 🚀 Features

- 🐳 Dockerized for easy deployment
- 🤖 Loads OmniGen-v1 automatically
- 💾 HuggingFace model caching support
- 🌐 Gradio web UI

---

## 🏗️ Folder Structure

```
project-root/
├── Dockerfile
├── docker-compose.yml
├── omnigen/                # Cloned OmniGen repository (not part of this repo)
├── huggingface_cache/      # Local volume for persisting models
├── README.md
```

---

## 🛠️ Requirements

- Docker
- Docker Compose
- Git (for cloning OmniGen repo)
- Optional: NVIDIA GPU + drivers (if running with CUDA)

---

## ⚙️ Setup

1. Clone this repo:

```bash
git clone https://github.com/arshad-munir/omnigen-docker.git
cd omnigen-docker
```

2. Clone the OmniGen repo inside this directory:

```bash
git clone https://github.com/Shitao/OmniGen.git omnigen
```

3. Run the container:

```bash
docker compose up --build
```

> ℹ️ The model (~11GB) will be downloaded on first run. It will be cached in `huggingface_cache/`.

4. Open your browser at:  
   👉 http://localhost:7860

---

## 🧠 Troubleshooting

- **Model re-downloads every time**: Make sure `huggingface_cache` volume is mounted correctly in `docker-compose.yml`.

- **Permission errors pushing to GitHub**: See SSH vs HTTPS notes in the repo.

- **Gradio not responding**: Check logs with  
  ```bash
  docker logs -f omnigen_container
  ```

---

## 🗂️ TODO

- [ ] Add GPU support (uncomment `NVIDIA_VISIBLE_DEVICES` and `deploy:` in `docker-compose.yml`)
- [ ] Add custom inputs for inference
- [ ] Create lightweight base image

---

## 📄 License

MIT License (add actual license if required)

---

## 🙌 Credits

- [OmniGen by Shitao](https://huggingface.co/Shitao/OmniGen-v1)
- [Gradio](https://gradio.app/)
- [HuggingFace Transformers](https://huggingface.co/transformers/)
