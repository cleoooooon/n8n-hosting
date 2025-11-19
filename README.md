# n8n Hosting Setup

This repository provides an easy way to host n8n (workflow automation tool) using Docker Compose.

## Prerequisites

- Docker and Docker Compose installed on your system
- A domain name (for production use)
- Basic knowledge of command line

## Quick Start

1. **Clone this repository**
   ```bash
   git clone https://github.com/cleoooooon/n8n-hosting.git
   cd n8n-hosting
   ```

2. **Configure environment variables**
   ```bash
   cp .env.example .env
   ```
   Edit `.env` and update the following variables:
   - `N8N_HOST`: Your domain or IP address
   - `N8N_PROTOCOL`: `http` or `https`
   - `WEBHOOK_URL`: Your webhook URL (usually https://your-domain.com/)
   - `GENERIC_TIMEZONE`: Your timezone

3. **Start n8n**
   ```bash
   docker-compose up -d
   ```

4. **Access n8n**
   Open your browser and navigate to:
   - Local: `http://localhost:5678`
   - Production: `https://your-domain.com:5678`

## Configuration

### Environment Variables

All configuration is done through environment variables in the `.env` file. See `.env.example` for all available options.

### Data Persistence

Your n8n data is stored in a Docker volume named `n8n_data`. This ensures your workflows and credentials persist across container restarts.

### File Storage

Files are stored in the `./local-files` directory, which is mounted into the container.

## Deployment Options

This setup can be deployed on:
- **Local Development**: Docker Desktop
- **Cloud Providers**: AWS, DigitalOcean, Google Cloud, Azure
- **PaaS**: Railway, Render, Heroku
- **VPS**: Any VPS with Docker support

## Production Recommendations

1. **Use HTTPS**: Set up SSL/TLS certificates (Let's Encrypt recommended)
2. **Enable Authentication**: Configure basic auth or OAuth
3. **Set Encryption Key**: Generate a secure encryption key
4. **Regular Backups**: Back up the `n8n_data` volume regularly
5. **Reverse Proxy**: Use Nginx or Caddy for SSL termination

## Useful Commands

```bash
# Start n8n
docker-compose up -d

# Stop n8n
docker-compose down

# View logs
docker-compose logs -f

# Restart n8n
docker-compose restart

# Update to latest version
docker-compose pull
docker-compose up -d
```

## Troubleshooting

- **Port already in use**: Change the port mapping in `docker-compose.yml`
- **Permission issues**: Ensure Docker has proper permissions
- **Data not persisting**: Check Docker volume configuration

## Resources

- [n8n Documentation](https://docs.n8n.io/)
- [n8n Community Forum](https://community.n8n.io/)
- [Docker Documentation](https://docs.docker.com/)

## License

MIT License - feel free to use this setup for your projects!

## Support

For issues specific to this setup, please open an issue on GitHub.
For n8n-specific questions, visit the [n8n community](https://community.n8n.io/).
