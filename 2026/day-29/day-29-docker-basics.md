Docker


systemctl status docker

=? docker service is running -> means docke engine is running -> inside it contains containerd
							-> dockerd wraps containerd


docker client: which used to run commands

docker client talks with dockerd and dockerd talks with containerd -> containerd creates container

docker search nginx

if you go inside container: use exit to come out

sed command used to The sed command (Stream Editor) is used to search, find and replace, insert, or delete text in a file without opening it.

today i created docker image on simple python flask application,

Docker file i created is

PS C:\Users\amarn\Desktop\90DaysOfDevOps\flask-app-ecs> cat .\Dockerfile
FROM python:3.14

WORKDIR /app

COPY . .

RUN pip install -r requirements.txt

EXPOSE 80

CMD ["python", "run.py"]

to create image command is: docker build -t image_name  (t for tag)
after that list out images: docker images
to create container: docker run -p 80:80 -d image_name    (p for port and d for detached mode)
to list container: docker ps
to stop container: docker stop container_id
to remove container: docker rm container_id
to remove images: docker rmi image_name

i used docker desktop for this,
i have checked in localhost app is running
