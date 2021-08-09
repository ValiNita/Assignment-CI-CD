I Assignment-CI-CD
The first part of the assignment was to install Jenkins on a vagrant virtual machine.
I created one job with the Jenkins GUI that cloned : (https://github.com/MarilenaIstrate/simple-java-maven-app).
The app had to be built, tested and the Junit had to be published.
II
The second part of the assignment was to do the same thing but through a pipeline(I used bash commands) 
1.Initially I allowed Jenkins to run sudo with NOPASSWD using the visudo command.
2.I installed maven so I can run Marilena's script (https://github.com/MarilenaIstrate/simple-java-maven-app).
3.Added stages as below :
clone->list->change ownership->install maven->clone marilena s code->list 2->check mvn command->Build->Test->list final folders.
