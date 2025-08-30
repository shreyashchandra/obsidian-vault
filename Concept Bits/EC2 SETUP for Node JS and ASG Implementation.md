
## Create New EC2 Instance 
- Command to change the permission (Read and Write permission for current mac account user) of PEM File- `chmod 700 my-mac.pem` 
-  ![[Screenshot 2025-08-30 at 4.51.09 PM.png]] Keep rest of the settings to default
- Install Node JS using nvm [ref][https://www.digitalocean.com/community/tutorials/how-to-install-node-js-on-ubuntu-20-04] 
- Setup GIT in their :-
- `git config --global user.name "Your Name"
- `git config --global user.email "youremail@domain.com"` 
- clone git repo using git clone command and use the https url (will work without setting up the ssh)
- start the node app
- can directly edit inbound rule(in security tab of Instance for the port on which app is running) then can directly visit it.

## ASG Setup
- Create image of the instance- ![[Screenshot 2025-08-30 at 5.11.53 PM.png]] ![[Screenshot 2025-08-30 at 5.12.43 PM.png]] 
- Crate a custom security group(optional)-![[Screenshot 2025-08-30 at 5.15.54 PM.png]] 
- Create Launch Template-![[Screenshot 2025-08-30 at 5.42.45 PM.png]] ![[Screenshot 2025-08-30 at 5.42.56 PM.png]] 