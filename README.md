# Sonarqube setup for AEM project in local
Pull the docker image community edition 9.9.1
```bash
$ docker pull sonarqube:9.9.1-community
```
Create the docker container
```bash
$ docker create --name sonarqube -p 9000:9000 sonarqube:9.9.1-community
```
Start the docker container
```bash
$ docker start sonarqube
```
Go to **localhost:9000** from browser. Default credential is -
```
username: admin
password: admin
```
Change the password after login

Select **Manually**, enter project name, key, branch(usually the **main** branch) and hit **setup**

Now, select **locally** and generate a token with **No expiration**, copy the following token and hit **continue**

Select **Maven** and copy the following code. Now for the IDE setup in intellij idea - 

- Edit configuration (top right)
- hit plus(+) button and add maven configuration
- Paste the copied code in **Run** and remove mvn from the beginning
- Add another option at the end of the command ``` -Dsonar.inclusions=**/*.java```
- hit **ok**

Make sure you are using **JDK-11** for building the project. Change **JDK** from **project structure**

Now, run this maven config. Analysis reports will be automatically uploaded to sonarqube server **localhost:9000**

Remove \ from the **Run** command if you get any build error

Go to **localhost:9000** for sonarqube analysis report

