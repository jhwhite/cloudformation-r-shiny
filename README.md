#Setting up an R Shiny instance with CloudFormation

##Contents

1. Set up AWS Account
2. Create KeyPair
3. Upload json to CloudFormation
4. SSH to your instance
5. Test!

###Set up AWS Account
Go to http://aws.amazon.com and register for an account. If you already have an account move on to Step 2.

###Create KeyPair
From your AWS console click the cube in the top left go to EC2 under the compute heading.

Then in the right navigation click Key Pairs.

Create a new Key Pair by clicking the Blue `Create Key Pair` button at the top.

Name your key pair and download it. Store it somewhere safe on your computer as it will be required to log into your computer in the future.

At this point follow these instructions to be able to log in to your instance in the future: [Connecting to Your Linux Instance Using SSH](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AccessingInstancesLinux.html)

###Upload json to CloudFormation
Click the cube in the top left again and this time click CloudFormation under Deployment and Management.

Click Create Stack.

On the next screen give your stack a name, this is arbitrary but should be descriptive. I name mine R-Shiny.

Under Source you should have downloaded or cloned the repo with the .json script to your computer. You can now just upload it to AWS. Or if you have an S3 bucket you can store it there and specify the URL to the template.

Click Next and in the dropdown choose the KeyPair that you created in the previous step.

Click Next for the next several screens.

###SSH to your instance
Once the CloudFormation screen says Create_Complete, you can go back to your EC2 instance screen and click the Connect button at the top.

On your local computer navigate to the directory you downloaded your AWS Key Pair to and run the ssh command given in the Connect To Your Instance modal shown in the EC2 page.

###Test!
Once you are in your instance make sure your programs have been installed.

* To check R is installed at the command line type `R`.
* To check git is installed type `git`.
* To check shiny server is running type `ps aux | grep shiny`. You should see two entries returned for running processes. If you only see one, shiny is not running.