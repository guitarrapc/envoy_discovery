FROM python:3.7
EXPOSE 8081

WORKDIR /app
COPY . .
RUN pip install -r requirements.txt

CMD ["python", "server.py", "-p", "8081"]