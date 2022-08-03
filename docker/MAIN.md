# Docker Postgre Django

## The first step:
### Install docker:
```
sudo apt-get update && apt-get upgrade
```
```
sudo apt install apt-transport-https ca-certificates curl software-properties-common
```
```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```
```
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"
```
```
sudo apt update
```
```
apt-cache policy docker-ce  
```
```
sudo apt install docker-ce
```
```
sudo systemctl status docker
```
### Configuring the Docker command without sudo (optional):
```
sudo usermod -aG docker ${USER}
```
```
su - ${USER}
```
```
id -nG
```
>output:    yourusername sudo docker
```
sudo usermod -aG docker username
```
### Install docker-compose:
```
sudo curl -L "https://github.com/docker/compose/releases/download/1.26.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
```
```
sudo chmod +x /usr/local/bin/docker-compose
```
```
docker-compose --version
```
## The second step:
### Create dockerfiles
##### Create a file in your working folder and be sure to name them as indicated in the instructions
```
sudo touch Dockerfile
```
```
sudo touch docker-compose.yml
```
### Edit docker file
```
sudo nano Dockerfile
```
```
FROM python:3

ENV PYTHONUNBUFFERED 1

WORKDIR /app

COPY . .

RUN python -m pip install --upgrade pip setuptools wheel

RUN pip install -r req.txt
```

#### Указывает Docker использовать официальный образ python 3 с dockerhub в качество
(Instructs Docker to use the official python 3 image with dockerhub in quality)
```
"FROM python:3"
```
#### Устанавливает переменную окружения, которая гарантирует, что вывод из python
(Sets an environment variable that ensures that the output from python)
```
"ENV PYTHONUNBUFFERED 1"
```

#### Устанавливает рабочий каталог контейнера — "app"
(Sets the working directory of the container — "app")
```
WORKDIR /app
```
#### Копирует все файлы из нашего локального проекта в контейнер
(Copies all files from our local project to a container)
```
"COPY . ."
```
```
"COPY . ./home/user/yourProjectFolder"
```
#### Обновить pip
(Update pip)
```
RUN python -m pip install --upgrade pip setuptools wheel
```

#### Запускает команду pip install для всех библиотек, перечисленных в requirement.txt
(Runs the pip install command for all libraries listed in requirement.txt)
```
"RUN pip install -r requirement.txt"
```
### Edit docker-compose file
```
sudo nano docker-compose.yml
```
```
version: '3.8'
services:
 web:
 #build our image
  build: .
  command: python3 manage.py runserver 0.0.0.0:8000
  environment:
  #postgres__data
   DEBUG: 1
   POSTGRES_USER: USER
   POSTGRES_PASSWORD: PASS
   POSTGRES_DB: DB
   POSTGRES_HOST: 0.0.0.0 #our-ip
  ports:
   - 8000:8000
  depends_on:
   - database
#add data base
 database:
  image: postgres:11 #import postgre
  volumes:
   - postgres_data:/home/sy/SurveyProjectX/data
  ports:
   - 5432:5432
  environment:
  #postgres__data
   POSTGRES_USER: USER
   POSTGRES_PASSWORD: PASS
   POSTGRES_DB: DB
   POSTGRES_HOST: 0.0.0.0 #our-ip
volumes:
 postgres_data:

```
### Edit database info in django-setting file:
```
sudo nano /home/user/projectFolder/applicationFolder/settings.py
```
##### don't forget to import 'os' in settings.py
```
import os
```
##### change db info
```
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql_psycopg2',
        'NAME': os.environ.get('POSTGRES_DB', default='DB'),
        'USER': os.environ.get('POSTGRES_USER', default='USER'),
        'PASSWORD': os.environ.get('POSTGRES_PASSWORD', default='PASS'),
        "HOST": os.environ.get('POSTGRES_HOST', default='our ip'),
        "PORT": "5432",
    }
}
```
## The third step:
### run a project
### add need ports(i need open 8000)
```
sudo ufw allow 8000
```
```
docker-compose up -d
```
```
docker exec -it container_id python3 manage.py migrate
```
```
docker exec -it container_id python3 manage.py makemigrations
```
```
docker exec -it container_id python3 manage.py collectstatic
```
```
docker exec -it container_id python3 manage.py createsuperuser
```
## The final step:
### open our website in browser
```
http://our_ip:8000
```
