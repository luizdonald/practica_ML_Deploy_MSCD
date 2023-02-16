FROM python:3.11

# Create the user that will run the app
RUN adduser --disabled-password --gecos '' ml-api-user

#WORKDIR /opt/house-prices-api
WORKDIR /opt

ARG PIP_EXTRA_INDEX_URL

# Install requirements, including from Gemfury
#ADD ./house-prices-api /opt/house-prices-api/

#RUN apt-get update
RUN apt-get install -y git

#RUN cd /opt
RUN git clone https://github.com/luizdonald/practica_ML_Deploy_MSCD.git /opt/practica_ML_Deploy_MSCD

#COPY /ML_Deploy_MSCD/section-08-deploying-with-containers /opt/practica_ML_Deploy_MSCD
WORKDIR /opt/practica_ML_Deploy_MSCD/section-08-deploying-with-containers
RUN git checkout practica


WORKDIR /opt/practica_ML_Deploy_MSCD/section-08-deploying-with-containers/house-prices-api

RUN pip install --upgrade pip
RUN pip install -r /opt/practica_ML_Deploy_MSCD/section-08-deploying-with-containers/house-prices-api/requirements.txt

#WORKDIR /opt/practica_ML_Deploy_MSCD/section-08-deploying-with-containers/house-prices-api

RUN chmod +x /opt/practica_ML_Deploy_MSCD/section-08-deploying-with-containers/house-prices-api/run.sh
RUN chown -R ml-api-user:ml-api-user ./

USER ml-api-user

EXPOSE 8001

CMD ["bash", "./run.sh"]
