# Jupyter for Asset Allocation

# Use centos7.2 from Aliyun's registry
FROM w6wy7kfr.mirror.aliyuncs.com/library/centos:centos7.2.1511

MAINTAINER Da Wei, xichuanglian@gmail.com

RUN yum -y update
RUN yum -y install epel-release
RUN yum -y install python34 python34-setuptools
RUN easy_install-3.4 -i http://mirrors.aliyun.com/pypi/simple/ pip
ADD pip.conf /root/.pip/pip.conf
RUN pip3 install pymongo jupyter numpy matplotlib

RUN useradd -m jupyter
USER jupyter
ADD jupyter_notebook_config.py /home/jupyter/.jupyter/jupyter_notebook_config.py
VOLUME ["/home/jupyter/asset_alloc"]
WORKDIR /home/jupyter/

EXPOSE 8080

# Jupyter has problem to be run directly. Wrap it in a shell script.
ADD run_jupyter.sh /home/jupyter/run_jupyter.sh
ENTRYPOINT ["bash", "run_jupyter.sh"]