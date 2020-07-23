# Template for nginx on Docker for https communication
This is a template to run nginx to receive https request and pass packets to webapp server.<br>

HTTPS/HTTP request -> nginx on docker -> webapp

## Requisites
In order to use this template, you need server where nginx runs. You can build it by AWS, vagrant, whatever. And then the server should have installed the follows.
* docker-cli
* docker-compose
* openssh-server
You can find many install instructions on the internet, for example [here](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-18-04).<br>

Also, you need to have domain name pointing the server(Eg. myserverexample.com). AWS Route53 is one of the options where you buy domain.<br>

With the all above prepared, (Certbot)[https://certbot.eff.org/lets-encrypt/ubuntubionic-other~] may help you simply have the server certified. You can follow the official instruction but some option may confuse you. Here's one of the example of following the instructions.

* My HTTP website is running "**None of the above**" on "**Ubuntu 18.04 LTS(bionic)**"
* Select "**default**" tab of a block in the middle of the page.
And then you follow the instruction, but I usually use standalone option at step4.
1. SSH into the server
2. Add Certbot PPA
```
$ sudo apt update
$ sudo apt install software-properties-common
$ sudo add-apt-repository universe
$ sudo add-apt-repository ppa:certbot/certbot
$ sudo apt update
```
3. Install Certbot
```
$ sudo apt install certbot
```
4. Run Certbot (You'll need to agree with license and input your domain name.)
```
$ sudo certbot certonly --standalone
```
5. Check generated certifications(keys)
You should have 4 pem files under /etc/letsencrypt/live/<domain-name>.

## Get Started
```
$ docker-compose 
```
