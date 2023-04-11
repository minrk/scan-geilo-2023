FROM ghcr.io/mamba-org/micromamba:jammy

# USER root
# RUN apt-get update \
#  && apt-get upgrade -y \
#  && apt-get install -y --no-install-recommends \
#     vim \
#     emacs \
#  && rm -rf /var/lib/apt/lists/*
#
# USER mambauser

COPY environment/ /tmp/
RUN arch=$(uname -m); \
 test "$arch" = "x86_64"  && arch="64"; \
 micromamba install -y -n base -c conda-forge --file /tmp/conda-linux-${arch}.lock \
 && micromamba clean -pity

ENV SHELL=/bin/bash \
    HOME=/home/mambauser
WORKDIR /home/mambauser
COPY quick-mpi.ipynb ./
EXPOSE 8888
CMD ["jupyter", "lab", "--ip=0.0.0.0"]
LABEL org.opencontainers.image.source=https://github.com/minrk/scan-geilo-2023 \
      org.opencontainers.image.title="SCAN Geilo 2023 MPI image" \
      org.opencontainers.image.description="Image for SCAN Geilo hackathon 2023 MPI project"
