FROM jupyter/scipy-notebook:307ad2bb5fce

LABEL maintainer="Serge Rey <sjsrey@gmail.com>"

RUN conda config --add channels conda-forge --force
RUN conda config --set channel_priority strict
RUN conda config --set safety_checks disabled
ADD requirements.txt requirements.txt
RUN conda install --file requirements.txt
ADD requirements_dev.txt requirements_dev.txt
RUN conda install --file requirements_dev.txt
ADD requirements_docs.txt requirements_docs.txt
RUN conda install --file requirements_docs.txt
ADD requirements_plus_conda.txt requirements_plus_conda.txt
RUN conda install --file requirements_plus_conda.txt
ADD requirements_tests.txt requirements_tests.txt
RUN conda install --file requirements_tests.txt
ADD requirements_plus_pip.txt requirements_plus_pip.txt
RUN pip install -r requirements_plus_pip.txt
RUN pip install -U pyproj==2.3.1

#---- Jupyter config ----

RUN echo "c.NotebookApp.default_url = '/lab'" \
 >> /home/$NB_USER/.jupyter/jupyter_notebook_config.py

# Switch back to jovyan to avoid accidental container runs as root
USER $NB_UID
