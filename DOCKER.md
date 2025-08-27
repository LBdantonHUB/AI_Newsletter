# Scalable Docker Setup with AI Models and Add-ons

## Overview

This is a comprehensive, scalable, Docker-based local development and hosting setup for web applications with integrated AI models and extensible add-ons. The system features automated installation and image management through a central agent that can dynamically create and manage new containers.

## 🏗️ Architecture

The setup consists of several key components:

1. **Image Manager Agent** - Central Flask-based service that manages Docker images and orchestrates deployments
2. **Core Services** - Essential services like frontend, n8n, Grafana, Redis
3. **AI Models** - Pluggable AI model containers (Ollama, Stable Diffusion, etc.)
4. **Add-ons** - Extensible additional services (databases, monitoring tools, etc.)

## 🚀 Quick Start

1. **Extract and Navigate**
   ```bash
   unzip scalable-docker-setup.zip
   cd scalable-docker-setup
   ```

2. **Install Dependencies**
   ```bash
   ./install.sh
   ```

3. **Start All Services**
   ```bash
   ./start.sh
   ```

4. **Access Services**
   - **Image Manager**: http://localhost:8080
   - **Frontend**: http://localhost:3000
   - **n8n**: http://localhost:5678 (admin/password)
   - **Grafana**: http://localhost:3001 (admin/admin)

## 📋 Services Overview

| Service | Port | Description | Credentials |
|---------|------|-------------|-------------|
| Image Manager | 8080 | Central management interface | - |
| Frontend | 3000 | Main web application | - |
| n8n | 5678 | Workflow automation | admin/password |
| Grafana | 3001 | Monitoring dashboards | admin/admin |
| Redis | 6379 | Caching and session storage | - |

## 🤖 AI Models & Add-ons

### Available AI Models
- **Ollama**: Local LLM server (supports Llama, Mistral, etc.)
- **Stable Diffusion**: Text-to-image generation
- **Whisper**: Speech-to-text transcription
- **Text Generation WebUI**: Web interface for various models

### Available Add-ons
- **PostgreSQL**: Relational database
- **MongoDB**: Document database
- **Prometheus**: Metrics collection
- **Code Server**: VS Code in browser
- **Jupyter**: Interactive notebooks
- **Nextcloud**: File sync and share

## 🎛️ Management Interface

The Image Manager provides a web-based interface to:

- **View System Status**: Monitor running containers, images, and system resources
- **Install Services**: One-click installation of AI models and add-ons
- **Manage Containers**: Start, stop, and remove containers
- **Monitor Resources**: Track CPU, memory, and storage usage

### Key Features:
- **Dynamic Service Discovery**: Automatically detects available services
- **One-Click Installation**: Install complex AI models with a single click
- **Resource Monitoring**: Real-time system and container metrics
- **Scalable Architecture**: Easily add new services and models

## 📁 Directory Structure

```
scalable-docker-setup/
├── image-manager/          # Central management service
│   └── image-manager-app/  # Flask application
├── core-services/          # Essential services
│   └── frontend/           # React frontend application
├── models/                 # AI model definitions
├── addons/                 # Additional service definitions
├── scripts/                # Utility scripts
├── docker-compose.yml      # Main orchestration file
├── install.sh             # One-click installation script
├── start.sh               # Start all services
├── stop.sh                # Stop all services
└── README.md              # This file
```

## 🔧 Advanced Usage

### Adding Custom Models

1. Create a new directory in `models/`
2. Add a `docker-compose.yml` with your model configuration
3. Update the Image Manager's service list
4. The model will appear in the web interface

### Adding Custom Add-ons

1. Create a new directory in `addons/`
2. Add service configuration files
3. Update the available services list
4. Install through the web interface

### Environment Configuration

Edit `.env` file to customize:
- Port mappings
- Service credentials
- Network settings
- Resource limits

### Scaling Services

Use Docker Compose scaling:
```bash
docker compose up -d --scale service-name=3
```

## 🛠️ Development

### Local Development

1. **Image Manager Development**
   ```bash
   cd image-manager/image-manager-app
   source venv/bin/activate
   python src/main.py
   ```

2. **Frontend Development**
   ```bash
   cd core-services/frontend/frontend-app
   pnpm run dev
   ```

### Adding New Features

1. **Backend API**: Add routes to `image-manager/image-manager-app/src/routes/`
2. **Frontend UI**: Modify React components in `core-services/frontend/frontend-app/src/`
3. **Services**: Add new service definitions to `models/` or `addons/`

## 🔒 Security Considerations

- **Network Isolation**: Services run in isolated Docker networks
- **Access Control**: Configure authentication for sensitive services
- **Data Persistence**: Volumes are used for data that should persist
- **Resource Limits**: Set appropriate CPU and memory limits

## 📊 Monitoring & Logging

### Built-in Monitoring
- **Grafana**: Pre-configured dashboards for system metrics
- **Container Logs**: Access via `docker compose logs -f [service]`
- **System Metrics**: Real-time monitoring through the Image Manager

### Log Management
```bash
# View all logs
docker compose logs -f

# View specific service logs
docker compose logs -f image-manager

# Follow logs in real-time
docker compose logs -f --tail=100
```

## 🚨 Troubleshooting

### Common Issues

1. **Docker Not Running**
   ```bash
   sudo systemctl start docker
   ```

2. **Port Conflicts**
   - Check `.env` file for port configurations
   - Use `netstat -tulpn` to find conflicting services

3. **Permission Issues**
   ```bash
   sudo chown -R $USER:$USER data/
   ```

4. **Service Won't Start**
   ```bash
   docker compose logs [service-name]
   ```

### Reset Everything
```bash
docker compose down -v  # Removes all data
./install.sh           # Reinstall
./start.sh             # Restart
```

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Add your improvements
4. Test thoroughly
5. Submit a pull request

### Adding New Services

1. Create service definition in appropriate directory
2. Update the Image Manager's service catalog
3. Add documentation
4. Test installation and removal

## 📄 License

This project is open source and available under the MIT License.

## 🆘 Support

For issues and questions:
1. Check the troubleshooting section
2. Review Docker and service logs
3. Consult individual service documentation
4. Create an issue with detailed information

## 🔄 Updates

To update the system:
```bash
git pull                    # Get latest changes
docker compose pull         # Update images
docker compose up -d        # Restart with updates
```

---

**Built with ❤️ for the developer community**



live
