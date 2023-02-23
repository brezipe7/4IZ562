FROM jupyter/datascience-notebook:python-3.8.4

USER root

# Install the required packages
RUN apt-get update && apt-get install -y python3-pip 

USER jovyan

RUN pip install mysql-kernel

RUN python3 -m mysql_kernel.install

RUN pip install sqlalchemy==1.4.35

RUN mkdir ~/notebooks

ENV PORT 8888
EXPOSE 8888

# Configure container startup
ENTRYPOINT ["tini", "-g", "--"]
CMD ["start-notebook.sh"]