# OpenFaaS Platform Research

This repository contains research and documentation for building a modern serverless platform using OpenFaaS Pro, k3s, and Supabase.

## Project Overview

We're exploring **OpenFaaS Pro** as the foundation for a scalable serverless platform, combined with:
- **k3s** - Lightweight Kubernetes for efficient resource usage
- **Supabase** - Backend-as-a-Service for authentication, database, and storage
- **AI Stack** - GPU-powered functions for intelligent features

## Documentation

| Document | Purpose | Status |
|----------|---------|--------|
| [Architecture Overview](01-architecture.md) | System design and component relationships | Complete |
| [Setup Roadmap](02-setup-roadmap.md) | Roadmap setup instructions | Complete |
| [Scaling Strategy](03-scaling.md) | Growth from single node to multi-node cluster | Complete |
| [Edition Comparison](04-comparison.md) | OpenFaaS Community vs Pro features | Complete |
| [Alternative Analysis](05-alternatives.md) | OpenFaaS Pro vs Knative comparison | Complete |

## Quick Start

1. **Review the architecture** → [01-architecture.md](01-architecture.md)
2. **Follow the setup roadmap** → [02-setup-roadmap.md](02-setup-roadmap.md)
3. **Understand scaling options** → [03-scaling.md](03-scaling.md)

## Key Insights

### OpenFaaS Edition Choice
- **Community Edition (CE)**: Free but limited to personal use or 60-day commercial trial
- **Pro Standard**: ~$1,200/month - Recommended for commercial environments
- **Pro Enterprise**: Custom pricing - For advanced compliance and multi-tenancy needs

**Recommendation**: Use Pro Standard for any commercial development beyond 60 days.

### Why This Stack?
- **Cost-effective**: k3s reduces resource overhead
- **Scalable**: OpenFaaS handles traffic spikes automatically
- **Modern**: Serverless functions with AI capabilities
- **Developer-friendly**: Supabase provides ready-to-use backend services

## Technology Stack

| Component | Purpose | Link |
|-----------|---------|------|
| **OpenFaaS Pro** | Serverless function platform | [openfaas.com/pro](https://www.openfaas.com/pro) |
| **k3s** | Lightweight Kubernetes | [k3s.io](https://k3s.io/) |
| **Supabase** | Backend services (Auth, DB, Storage) | [supabase.com](https://supabase.com/) |
| **AI Functions** | GPU-enabled serverless inference | [openfaas.com/blog](https://openfaas.com/blog/) |

## Documentation Site

This repository includes a complete documentation site built with MkDocs and Material theme. To view the documentation:

1. **Local Development**:
   ```bash
   cd openfaas-research
   pip install mkdocs mkdocs-material
   mkdocs serve
   ```

2. **Deploy to GitHub Pages**:
   - Follow the [Deployment Guide](DEPLOYMENT.md)
   - Or use the included GitHub Actions workflow

## Contributing

This is a research repository. Feel free to:
- Add diagrams and visualizations
- Improve installation instructions
- Document lessons learned
- Share performance benchmarks

## Support

For questions about this research or implementation guidance, please refer to the individual documentation files or create an issue in this repository.