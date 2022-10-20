FROM fedora

WORKDIR /development

RUN dnf update -y && \
    dnf install -y git python3-devel maven gcc python3-pip java-17-openjdk

COPY requirements.txt requirements.txt

RUN python3 -m pip install --upgrade pip && \
    python3 -m pip install -r requirements.txt
    
RUN ansible-galaxy collection install community.general ansible.eda

CMD export JDK_HOME=/usr/lib/jvm/java-17-openjdk && \
    export JAVA_HOME=$JDK_HOME && \
    export PIP_NO_BINARY=jpy
