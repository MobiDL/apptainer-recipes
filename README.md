# 🐳 Apptainer Recipes

**A collection of Apptainer container recipes for reproducible, portable, and high-performance computing environments.**

This repository hosts **production-ready Apptainer container recipes** for bioinformatics tools and workflows.

## 📦 Available Containers

| Tool       | Version | Description                                     | Recipe File    |
| ---------- | ------- | ----------------------------------------------- | -------------- |
| `bwa`      | 0.7.19  | Burrow-Wheeler Aligner for short-read alignment | `bwa.def`      |
| `bwa-mem2` | 2.3     | The next version of bwa-mem                     | `bwa-mem2.def` |
| `fastp`    | 1.3.6   | Fastq pre-processing tool                       | `fastp.def`    |

## 🚀 Quick Start

### 1. Clone the Repository

```bash
git clone https://github.com/MobiDL/apptainer-recipes
cd apptainer-recipes
```

### 2. Build a Container

Use Apptainer to build a container from a recipe file:

```bash
apptainer build container_VERSION.sif recipe.def
```

### 3. Run the Container

```bash
apptainer run container_VERSION.sif [command]
```

---

## 📜 Best Practices

### Container Design

- **Minimal Base Images**: Use lightweight base images (e.g., `ubuntu:22.04` or `debian:stable-slim`) to reduce container size.
- **Explicit Dependencies**: List all dependencies explicitly in the recipe to ensure reproducibility.

### Usage Guidelines

- **Bind Directories**: Mount only necessary directories to avoid security risks:
  ```bash
  apptainer run --bind /host/data:/data container.sif
  ```
- **Immutable Containers**: Treat containers as immutable. Rebuild them if changes are needed.
- **Versioning**: Tag your containers with versions (e.g., `fastp_1.3.6.sif`) for traceability.

### Performance Tips

- **Cache Directory**: Set `SINGULARITY_CACHEDIR` to a fast storage location to speed up builds:
  ```bash
  export SINGULARITY_CACHEDIR=/scratch/.singularity/cache
  ```

## 🤝 Contributing

### Adding a New Container

1. **Create a Recipe file**: Create a new `.def` with the Apptainer recipe (e.g., `my-tool.def`).
2. **Update the Table**: Add your container to the [Available Containers](#available-containers) table.

### Pull Requests

- Ensure your recipe builds successfully.
- Test the container with real data.
- Follow the [Best Practices](#best-practices) guidelines.

## 🛠️ Requirements

- **Apptainer ≥ 1.1.0** (recommended for `--fakeroot` support)
- **Linux Kernel ≥ 3.18** (for full Apptainer functionality)
- **Root or Fakeroot Access** (for building containers)

## 🆘 Support

For questions or issues, please open an [issue](https://github.com/MobiDL/apptainer-recipes/issues) or contact the maintainers.
