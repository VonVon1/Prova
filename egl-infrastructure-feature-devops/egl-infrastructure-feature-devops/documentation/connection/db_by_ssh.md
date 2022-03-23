# HOW TO ACCESS DATABASE
```
1 - Access Ec2 Dashboar on AWS Console.
2 - Select the instânce "egl-dev bastion" and click on connect button.
3 - Select the tab "Session Manager" and click in connect.
4 - switch to root user with command "sudo su ec2-user"
5 - RUN:
psql \
   --host=<DB_HOST> \
   --port=5432 \
   --username=<DB_USER> \
   --password \
   --dbname=<DB_NAME>
6 - database_password: in DM
```