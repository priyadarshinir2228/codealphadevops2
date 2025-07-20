This is a simple python flask application to host a simple web app.

After starting the flask application you can access following URL's on the server:

Function	URL
index	http://<server>:<port>/
json	http://<server>:<port>/json/
hello	http://<server>:<port>/hello/
hello <name>	http://<server>:<port>/hello/<name>
primes 100	http://<server>:<port>/primes/
primes <count>	http://<server>:<port>/primes/<count>
How to run
You can run the application in 2 ways:

Build and run the docker image
Build and run the code from source
Docker instructions
Requirements:

Docker installed
Build the docker image in the project root folder with:

docker build . -t flask-example-cicd:latest
To run the docker image in interactive mode:

docker run --rm -it -p 8080:8080/tcp --name flask-example flask-example-cicd:latest
To run the docker image in detached mode:

docker run --rm -d -p 8080:8080/tcp --name flask-example flask-example-cicd:latest
You can change the environmental variable for flask in the Dockerfile, for example you can change the port by changing ENV FLASK_RUN_PORT=8080.

Stop the running container:

docker stop flask-example
Build from source
Requirements:

python3
python3-dev
python3-pip
gcc (to compile cython)
musl-dev (to compile cython)
Instructions for Debian/Ubuntu
Install requirements:
apt update
apt install gcc musl-dev python3 python3-dev python3-pip
Build/Install project:
. build.sh
Run the server on localhost:8080:
. run.sh
Development
Virtual Environment
For local development you can use a virtual environment → How to install virtualenv.

Create a virtual environment:

# linux example
python3 -m venv "venv"
source venv/bin/activate
With deactivate you can disable the virtual environment.

Debugging
Built-In flask debugger
You can debug the flask app by running following commands:

Linux (Bash)
Windows (CMD)
Windows (PowerShell)
External Debugger
When using an external debugger, the app should still be in debug mode, but it an be useful to disable the built-in debugger and reloader, which can interfere.

flask run --no-debugger
flask run --no-reload
flask run --no-debugger --no-reload
Example configuration for VS Code
Testing
To run unit tests:

# install pytest manually or use "reset-dev.sh"
pip3 install pytest 
pytest
Reset development environment
You can use the script reset-dev.sh to reset your development environment:

. reset-dev.sh
The script will do following:

(Re)create the virtual environment venv without dependencies installed
Activating venv in current terminal
Install development/testing tools in venv
flake8 (Linting)
pylint (Linting)
autopep8 (Formatting)
pytest (Testing)
Remove all folders created by build/install
package info (*egg-info)
build folder
dist folder
pycache folders
built cython files (*.so, *.pyd)
Now you can build the project manually or with build.sh.
