ARG BASE_IMAGE=inseefrlab/onyxia-r-minimal
FROM $BASE_IMAGE

LABEL maintainer="InseeFrLab <innovation@insee.fr>"

ARG PYTHON_VERSION="3.12.9"
ENV PYTHON_VERSION=${PYTHON_VERSION}

USER root

COPY --chmod='+x' scripts/ /opt/
COPY requirements.txt .

RUN /opt/install-python.sh && \
    /opt/install-julia.sh && \
    # Install common Python packages
    uv pip install --system --no-cache -r requirements.txt && \
    # Fix user permissions
    /opt/fix-user-permissions.sh && \
    # Clean
    /opt/clean.sh requirements.txt

USER 1000

CMD ["/bin/bash"]
