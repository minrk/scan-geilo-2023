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

COPY quick-mpi.ipynb $HOME/
ENV SHELL=/bin/bash
EXPOSE 8888
CMD ["jupyter", "lab", "--ip=0.0.0.0"]
LABEL org.opencontainers.image.source https://github.com/minrk/scan-geilo-2023
