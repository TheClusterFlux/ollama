# Ollama Server Deployment

This repository contains the Kubernetes configuration to deploy an Ollama instance running the Phi-3 Mini language model. This setup provides a lightweight yet effective LLM serving capability.

## Features

- **Phi-3 Mini Model**: A lightweight, efficient model from Microsoft that balances performance and resource requirements
- **Persistent Storage**: Automatically saves downloaded models to avoid re-downloading
- **Kubernetes-Ready**: Complete deployment setup with health checks and resource limits
- **Auto-initialization**: Automatically downloads the Phi-3 Mini model during deployment
- **Secure Access**: HTTPS access via custom domain with TLS encryption

## Deployment Information

The Ollama server runs on port 11434 and exposes API endpoints for managing and using language models.

### Access Information

- **Domain**: ollama.theclusterflux.com
- **Protocol**: HTTPS (SSL enforced)
- **API Base URL**: https://ollama.theclusterflux.com

### Resource Requirements

- Memory: 2-4 GB
- CPU: 1-2 cores
- Storage: 10 GB persistent volume

## How to Use

### API Usage

Once deployed, you can interact with the Ollama API at the secure endpoint `https://ollama.theclusterflux.com`. Common API endpoints:

- `/api/generate` - Generate text from a prompt
- `/api/chat` - Chat with the model
- `/api/tags` - List available models

### Example API Call

```bash
curl -X POST https://ollama.theclusterflux.com/api/generate -d '{
  "model": "phi3:mini",
  "prompt": "Explain quantum computing in simple terms:",
  "stream": false
}'
```

## Model Information

**Phi-3 Mini** is an efficient, lightweight model developed by Microsoft. It offers:

- 3.8 billion parameters
- Good performance on reasoning tasks
- Low resource requirements compared to larger models
- Trained on high-quality data

## Deployment Components

The deployment includes:

1. **Ollama Server**: Running the official Ollama image
2. **Persistent Storage**: A 10Gi persistent volume at `/data/ollama-models` on the host
3. **Model Initialization Job**: Automatically downloads the Phi-3 Mini model
4. **Ingress Configuration**: Provides secure HTTPS access via domain name

For more information about Ollama, visit the [official documentation](https://github.com/ollama/ollama).