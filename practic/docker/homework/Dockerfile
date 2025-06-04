FROM continuumio/miniconda3:latest

WORKDIR /homework

COPY 13.sh .

RUN chmod +x 13.sh

RUN pip install mlflow boto3 pymysql

CMD ["./13.sh"]
