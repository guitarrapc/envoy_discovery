FROM python:3.7
EXPOSE 8080

WORKDIR /app
COPY . .
RUN pip install -r requirements.txt
RUN pip install enum34

CMD ["python", "main.py"]