# Configure Django to run on Docker 
This is a step-by-step tutorial that details how to configure Django to run on Docker with Postgres. For production environments, we'll add on Nginx and Gunicorn. We'll also take a look at how to serve Django static and media files via Nginx. For HTTPS-secured websites, we also need Let’s Encrypt.

Dependencies:
```
Django
Docker
Python
Nginx
Gunicorn
Let’s Encrypt
```

> [Dockerizing Django with Postgres, Gunicorn, and Nginx](https://testdriven.io/blog/dockerizing-django-with-postgres-gunicorn-and-nginx/)
> [Nginx and Let’s Encrypt with Docker in Less Than 5 Minutes](https://pentacent.medium.com/nginx-and-lets-encrypt-with-docker-in-less-than-5-minutes-b4b8a60d3a71)

### Build project structure
First of all, you should build the directories structure like:
```
home
├── api(This is the Django project directory)
├── certbot
├── nginx
├── postgres
```

### download docker and docker-compose 
### change settting of Dockerfile, docker-compose.yml(path, domain, and so on)
### run lentencrypt.sh



## Environment
How to check the process location/how to free the port
process id：456
check where it is run: ps aux | grep 4874
list the processes list: lsof -i -P -n | grep LISTEN

## Static files
If your admin pages opened without and rendering, it might be because of no migration, run the following command in your VM
#### step 1
Enter the Django project containers:
```
docker exec -it your_django_container_name bash
```
#### step 1
Run the migration,
```
python manage.py collectstatic --no-input --clear
```

Then when you log in the Django admin at the first time, you might meet the problem: there is no "postgres" user, you could run the following command in the Django project container.
```
python manage.py createsuperuser.
```

## Postgres user problem
User problem. For example, I got the FATAL:  password authentication failed for user "postgres".

you just run the following command:
```
docker exec -it ubuntu_bash bash
psql -U postgres postgres
Alter user postgres with superuser password 'postgres';
```


