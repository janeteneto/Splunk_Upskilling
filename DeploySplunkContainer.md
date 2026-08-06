1. Install Docker on your laptop using this link: https://docs.docker.com/desktop/setup/install/mac-install/
3. Open a terminal and run this command to check if you have Docker properly installed on your machine:
```
docker version
```
4. Run this command to download the required Splunk Enterprise image to your local Docker image library:
```
docker pull splunk/splunk:latest
```
Should look like something like this:
<img width="1712" height="994" alt="image" src="https://github.com/user-attachments/assets/cf2c61c8-dbd6-4eaa-82ce-fb8689525bcb" />
After the pull is complete, the output will be a long set of numbers and letters, which is the **container ID** of your new Splunk Enterprise instance.

5. Now, we need to run the command to run the Splunk image on the local host, create a password so that you can access it and accept Splunk's license terms. Remember to replace **<Password123!>** with your chosen password:
```
docker run -d \
--name splunk \
-p 8000:8000 \
-p 8088:8088 \
-p 8089:8089 \
-e SPLUNK_GENERAL_TERMS="--accept-sgt-current-at-splunk-com" \
-e SPLUNK_START_ARGS="--accept-license" \
-e SPLUNK_PASSWORD="Password123!" \
splunk/splunk:latest
```

6. To check the container's ID, status and port, run the command ```docker ps```. It should be something like this:

<img width="825" height="106" alt="Screenshot 2026-08-06 at 15 51 35" src="https://github.com/user-attachments/assets/10389dd2-5a65-418f-ad2e-8167ec9b301f" />

7. Open a web browser on the host and access SplunkWeb inside the container using the address:
```
localhost:8000
```
If successful, it should look like this:


8. Log in to Splunk Enterprise inside the container using the username admin and the password you set when you ran the Docker image.
9. 
