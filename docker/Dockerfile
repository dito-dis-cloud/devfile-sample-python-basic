FROM registry.access.redhat.com/ubi9/python-39:1-117.1684741281

# By default, listen on port 8081
#EXPOSE 8081/tcp
#ENV FLASK_PORT=8081

# Set the working directory in the container
#WORKDIR /projects

# Install any dependencies
#RUN \
#  if [ -f requirements.txt ]; \
#    then pip install -r requirements.txt; \
#  elif [ `ls -1q *.txt | wc -l` == 1 ]; \
#    then pip install -r *.txt; \
#  fi
RUN pip install django
RUN pip install djangorestframework
RUN django-admin startproject example .
RUN ./manage.py migrate
RUN ./manage.py createsuperuser

# Copy the content of the local src directory to the working directory
#COPY . .
COPY ./settings.py ./example
COPY ./urls.py ./example

# Specify the command to run on container start
#CMD [ "python", "./app.py" ]
CMD [ "./manage.py", "runserver" ]
