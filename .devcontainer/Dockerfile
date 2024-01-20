FROM mcr.microsoft.com/devcontainers/miniconda:0-3

# Copy environment.yml (if found) to a temp location so we update the environment. Also
# copy "noop.txt" so the COPY instruction does not fail if no environment.yml exists.
COPY environment.yml* .devcontainer/conda_init.txt /tmp/conda-tmp/
RUN conda install mamba -c conda-forge -y; \
    mamba install anaconda; \
    pip install pyOpenSSL --upgrade; \
    mamba install jupyterlab jupyterlab-git pandas matplotlib scikit-learn bokeh seaborn r-base r-essentials keras tensorflow pytorch cpuonly -c conda-forge -c pytorch -y; \
    if [ -f "/tmp/conda-tmp/environment.yml" ]; then umask 0002 && mamba env update -n base -f /tmp/conda-tmp/environment.yml; fi \
    && cat /tmp/conda-tmp/conda_init.txt >> /home/vscode/.bashrc

# Install Julia and Julia kernel
RUN wget https://julialang-s3.julialang.org/bin/linux/x64/1.8/julia-1.8.5-linux-x86_64.tar.gz; \
    tar -xvzf julia-1.8.5-linux-x86_64.tar.gz; \
    cp -r julia-1.8.5 /opt/; \
    ln -s /opt/julia-1.8.5/bin/julia /usr/local/bin/julia; \
    julia -e 'ENV["JUPYTER"]="/opt/conda/bin/jupyter"; using Pkg; Pkg.add("IJulia"); Pkg.add("LanguageServer")'

# Install R kernel
RUN Rscript -e 'install.packages("IRkernel", repos="https://cloud.r-project.org"); IRkernel::installspec(user = FALSE); install.packages("languageserver", repos="https://cloud.r-project.org")' \
    && rm -rf /tmp/conda-tmp

# [Optional] Uncomment this section to install additional OS packages.
# RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
#     && apt-get -y install --no-install-recommends <your-package-list-here>
