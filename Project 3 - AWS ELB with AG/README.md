# AWS ELB-ASG
- Launch an Ec2 Instance
![one](./images/one.png)
![2](./images/2.png)
![3](./images/3.png)
![4](./images/4.png)
- Advanced details
    - Add this bash script to the user data
    ```
   #!/bin/bash

   # Variable Declaration
   #PACKAGE="httpd wget unzip"
   #SVC="httpd"
   URL='https://www.tooplate.com/zip-templates/2098_health.zip'
   ART_NAME='2098_health'
   TEMPDIR="/tmp/webfiles"

   yum --help &> /dev/null

   if [ $? -eq 0 ]
   then
   # Set Variables for CentOS
   PACKAGE="httpd wget unzip"
   SVC="httpd"

   echo "Running Setup on CentOS"
   # Installing Dependencies
   echo "########################################"
   echo "Installing packages."
   echo "########################################"
   sudo yum install $PACKAGE -y > /dev/null
   echo

   # Start & Enable Service
   echo "########################################"
   echo "Start & Enable HTTPD Service"
   echo "########################################"
   sudo systemctl start $SVC
   sudo systemctl enable $SVC
   echo

   # Creating Temp Directory
   echo "########################################"
   echo "Starting Artifact Deployment"
   echo "########################################"
   mkdir -p $TEMPDIR
   cd $TEMPDIR
   echo

   wget $URL > /dev/null
   unzip $ART_NAME.zip > /dev/null
   sudo cp -r $ART_NAME/* /var/www/html/
   echo

   # Bounce Service
   echo "########################################"
   echo "Restarting HTTPD service"
   echo "########################################"
   systemctl restart $SVC
   echo

   # Clean Up
   echo "########################################"
   echo "Removing Temporary Files"
   echo "########################################"
   rm -rf $TEMPDIR
   echo

   sudo systemctl status $SVC
   ls /var/www/html/

   else
   # Set Variables for Ubuntu
   PACKAGE="apache2 wget unzip"
   SVC="apache2"

   echo "Running Setup on CentOS"
   # Installing Dependencies
   echo "########################################"
   echo "Installing packages."
   echo "########################################"
   sudo apt update
   sudo apt install $PACKAGE -y > /dev/null
   echo

   # Start & Enable Service
   echo "########################################"
   echo "Start & Enable HTTPD Service"
   echo "########################################"
   sudo systemctl start $SVC
   sudo systemctl enable $SVC
   echo

   # Creating Temp Directory
   echo "########################################"
   echo "Starting Artifact Deployment"
   echo "########################################"
   mkdir -p $TEMPDIR
   cd $TEMPDIR
   echo

   wget $URL > /dev/null
   unzip $ART_NAME.zip > /dev/null
   sudo cp -r $ART_NAME/* /var/www/html/
   echo

   # Bounce Service
   echo "########################################"
   echo "Restarting HTTPD service"
   echo "########################################"
   systemctl restart $SVC
   echo

   # Clean Up
   echo "########################################"
   echo "Removing Temporary Files"
   echo "########################################"
   rm -rf $TEMPDIR
   echo

   sudo systemctl status $SVC
   ls /var/www/html/
   fi 
   
   ```
![5](./images/5.png)
![28](./images/28.png)
![29](./images/29.png)

- Set up an AMI

![6](./images/6.png)

- Image and templates -> create image

![7](./images/7.png)
![8](./images/8.png)

- Hover over to launch templates

![9](./images/9.png)
![10](./images/10.png)
![31](./images/31.png)

- Create a target group next

![11](./images/11.png)
![13](./images/13.png)
![14](./images/14.png)

- Now, we move to creating a load balancer

![12](./images/12.png)
![32](./images/32.png)
![15](./images/15.png)
![16](./images/16.png)
![17](./images/17.png)
![18](./images/18.png)
![19](./images/19.png)
![20](./images/20.png)

- Create an Auto Scaling group

![21](./images/21.png)
![22](./images/22.png)
![23](./images/23.png)
![24](./images/24.png)
![25](./images/25.png)
![26](./images/26.png)
![27](./images/27.png)

- Go to target group for health check again

# Congratulations !