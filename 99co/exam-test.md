# Part A

1. _Tell us about your main motication to pursue a career in the software industry!_

2) _Tell us about your strength that help your profession as a software engineer and how do you take advantage of them to become a better engineer!_

3. _Tell us about yout weaknesses that give you challenges and what are your efforts to overcome them!_

4) _Tell us about the most challenging project that you have worked on and what efforts or strategies did you use to solve the problems you met in that project!_

5. _Tell us about external factors that you would consider ideal to help you become a more effective engineer!_

6) _Tell us about how you see yourself in the next five years in software industry!_

# Part B

1. _When setting up a new website, the web can’t be accessed. On nginx error log it returns_
   `/var/www/html/index.html is forbidden (13: Permission denied).`

   _Doing an `ls -la` on `/var/www/html` returns the following result:_

   ```
   /var/www/html$ ls -al
   total 12
   drwxr-xr-x 2 root root 4096 Jul 8 09:47 .
   drwxr-xr-x 3 root root 4096 Mei 29 11:27 ..
   ---------- 1 root root 612 Mei 29 11:27 index.html
   ```

   _Explain how would you solve this issue as detailed as you need it to be. Feel free to add assumption as needed._

   **Answer**

   These problem appeared because permission of `index.html` file that should be accessed by nginx is sufficient. The permission of `index.html` file is 000, that means no read, write, execute access from all of user and group. To solve this problem, as minimum, read access permission from all user (assuming nginx use `nginx` user to spawn process) should be applied to `index.html`. So we need to use `chmod` command to change the permission:

   ```
   # assuming working directory is in /var/www/html
   chmod 444 index.html
   ```

   But for convinience, we should probably also add write `user` permission to the file for editing purpose. So final command is

   ```
   chmod 644 index.html
   ```

   The website should be accessible again.

2) _There’s a production database on server A that can only be accessed from server B. A database engineer needs to access the database regularly on server A but only has the permission to connect to server B. Explain how would you set the environment for the database engineer to connect to server A. You can be as detailed as possible and use assumption for the information that’s not given here._

   **Answer**

3) _Assume we have setup a service with the following layers:_

   _When the client receive error 502 Bad Gateway, how would you like to troubleshoot to fix the issue to point out the root problem? You can be as detailed as possible and use assumption for the information that’s not given here._

# Part C

This part helps us to understand how you would design and build a scalable system that could serve million users per month. Choose minimum 1 problem that you find the most interesting. Tell us how you would design the system given the requirements, what technologies (open source or 3rd party) you are going to use, and the strategy/approach that you are going to use to handlehigh usage. You can use diagrams to help illustrate your explanation. Feel free to add assumptions.

1. Let’s imagine we are going to build a Restful API system that can be accessed securely from public, fast enough to respond with sufficient body size, and minimum down time (nearly 0%). The system also will use common relational database (such as MySQL, PostgreSQL). With those conditions, tell us how would you design the system and the technologies that are used, preferably as cost-efficient as possible. Explain the strengths and weaknesses of that design.
2. Let’s imagine we are going to build a web application. There will be several people working on the code, and we need the code to be documented for every change. We need a system with at least two environments (production and other environment(s)) that can support our fast-paced product-delivery every two weeks. Sometimes, when a bug is found, the fix needs to be implemented on the web application as soon as possible. With those conditions, what do you think is the best solution to be implemented and what technologies will you use?
3. Let’s imagine we already have a Web app that runs on production. The app is behind a load balancer, running on virtual machines/containers and use a single database for transaction data. To reduce operational cost, we want to move the system into cloud public infrastructure such as AWS or GCP. Describe the migration steps that we should do with minimum down time.
