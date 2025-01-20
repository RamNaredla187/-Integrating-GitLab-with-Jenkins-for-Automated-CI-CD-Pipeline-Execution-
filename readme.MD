## Integrating GitLab with Jenkins for Automated CI/CD Pipeline Execution
#
### Create a Repository in GitLab
#### Add two files sample java program and Jenkinsfile in Main branch
#
## First u need to install the jenkins 
### if you want to install Go to browser and copy the url
```bash
https://github.com/RamNaredla187/jenkins-installation

```
### login into jenkins
### Step 1: Install GitLab Plugin in Jenkins
#### 1.Go to Manage Jenkins > Manage Plugins.
#### 2.Search for and install the GitLab Plugin.
#### 3.Restart Jenkins if required. 
#
### Step 2: Configure GitLab Credentials in Jenkins
##### You need to add credentials to allow Jenkins to authenticate with GitLab.
#### 1.Go to Manage Jenkins > Manage Credentials > (select a domain or (global)) > Add Credentials.

#### 2.Select Username with password(personal access key) or SSH Username with private key, depending on your method of authentication:
##### -For Personal Access Token (PAT):
##### 2.1.Use Username as your GitLab username.
##### 2.2.Use Password as the personal access token from GitLab (Role- Reporter is good).
##### 2.3.Ensure the token has read_repository and write_repository permissions.
#### For SSH:
##### Add your private SSH key and username.
#### 3.Save the credentials and note the ID for use later.
#
### Step 3: Create a New Freestyle Project
#### Go to the Jenkins dashboard and click New Item.
#### Select Freestyle Project.
#### Enter a name (e.g., GitLab-Java-Pipeline) and click OK.
#
### Step 4: Set Up GitLab Repository
#### In the project configuration, scroll to the Source Code Management section.
#### Select Git.
#### Enter your GitLab repository URL (e.g., https://gitlab.com/your-username/your-repository.git).
#### Under Credentials, select the credentials you created earlier.
#### Optionally, specify a branch (default: main or master).
#
### Step 5: Configure Build Triggers
####  Poll SCM
##### In the Build Triggers section, check Poll SCM.
##### Add a cron expression to poll for changes every minute:
```bash
*****
```
#### Jenkins will check for changes in the repository every minute.
#
### Step 6: Configure Build Steps
#### In the project configuration, scroll to the Build section.
#### Add a Build Step and select Execute Shell.
#### Add the following commands to compile and run the Java program:
```bash
# Set Java Home (adjust the path to your Java installation)
export JAVA_HOME='/usr/lib/jvm/java-11-openjdk-amd64'

# Compile the Java code
javac sample.java

# Run the compiled Java program
java sample
```
#
### Step 7: Add Post-Build Actions (Optional)
#### You can configure additional steps to run after the build, such as:

##### Sending notifications (e.g., email).
##### Archiving artifacts.
##### Publishing reports (e.g., JUnit results).
#
### Step 8: Run and Verify the Job
#### Save the configuration and return to the Jenkins dashboard.
#### Trigger the job manually using the Build Now button to verify the setup.
#### If using Polling, Jenkins will automatically check for changes at the interval defined.