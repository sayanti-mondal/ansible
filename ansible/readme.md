##########Brief Desciption of the Exercises#####################

1. Exercise1 - Creating the 1st inventory file containg one server and its required informations to ssh into i 
2. Exercise2 - Creating the 2nd inventory file containing 2 webservers and 1 database server and also added grouping
3. Exercise3 - Creating the 3rd inventory file containing the grouping of all the servers and defining variable
4. Exercise4 - A Playbook with multiple plays, where one play installs the tomcat service on webservers & another play installs the mariadb service on the DB server
5. Exercise5 - Installs tomcat service on two centos target machines, starts & enable the web service, update the default home page with a customized one
6. Exercise6 - Installs mariadb service on a centos target machine, starts & enables the Database service, Creates a Database and database user
7. Exercise7 - Introducing ansible.cfg file the working directory, where we mentioned the inventory file location, log file location and other settings. Thats why to run the playbook we dont need to mention inventory path anymore. we can just run ansible-playbook <playbook_name>
8. Exercise8 - In this playbook demonstrated playbook variables and output variables.
 
    variables are of 4 types generally in ansible
     - variables defined in playbooks
     - inventory based variables
     - Fact variables
     - Output variable 

    Declare Variable - defined variables inside playbook using var key. it is generally mentioned before tasks.
      var:
       db_name: value
       db_user: value
       db_pass: value  
   
    Use Variable - How to use those variables inside a task with syntax "{{ var_name }}" [double quotes within that two curly braces]

    print Variable - Use Debug module to print those variables in two different method 
      - inside a message:- msg: " Database name is {{db_name}} "
      - var: db_name
 
    Register output variable - how to register output of a task as a variable and then print it

9. Exercise9 - In this project demonstated  
       - var_precedence.yml:- variable precedence concept based on the location of variable. Defined same variables in playbook, group_vars/all, group_vars/webservers, host_vars/web02. variable precedence is environment_variables > playbook_variables > host_vars > group_vars/<group_name> > group_vars/all  
       - variables_list_dic.yml:- Then we created another playbook to understand the concept of list and dictionary variables  
       - print_facts.yml:- Created a playbook to print different Fact variables of all the target srrvers. This variables are created during the task "gathering facts"  
       - ansible variables documentation link - https://docs.ansible.com/ansible/latest/playbook_guide/playbooks_variables.html  
       - Runtime variable/environment variable command -> ansible-playbook example.yml -e "variable_name=value"  
            
10. Exercise10 - In this project discussed about condition   
           - playbook installs chrony when os is centos but installs ntp when os is ubuntu  
           - condition is denoted by when and declared in the same column of module  
           - ansible condition documentation:- https://docs.ansible.com/ansible/latest/playbook_guide/playbooks_conditionals.html
     
11. Exercise11 - Install multiple packages using for loop

12. Exercise12 - Using the concept of template module, jinja2 templating and handlers updating the configuration of apache configuration file and then restart the service using handlers.  
            - handlers: Sometimes you want a task to run only when a change is made on a machine. handlers are written in the same column as tasks.   
            - jinja2 templating is used for changing the default configuartion of a software, like apache running port 8081 instead of 80. It is written under template module.  
            - Often handler is used with jinja2 templating, since a task need to run only when there is a configuration change made by jinja2 template 
 
13. Exercise13 - create a role from the existing ansible playbook  
               - ansible-galaxy init <rolename> : is the command to create a role  
               - role is genearlly created under roles folder and defined in the ansible playbook  
               - when we run the playbook, it executes the role mentioned in the playbook

14. aws - In this folder created a playbook to create an aws keypair and then created an ec2 instance with that key pair  
              - ansible can talk to aws through access_key and secret_access_key  
                  export AWS_ACCESS_KEY_ID='AK123'
                  export AWS_SECRET_ACCESS_KEY='abc123'  
                ansible doc link - https://docs.ansible.com/ansible/latest/collections/amazon/aws/docsite/guide_aws.html  
              - The amazon.aws collection contains a number of modules and plugins for controlling Amazon Web Services (AWS)  
              - modules doc - https://docs.ansible.com/ansible/latest/collections/amazon/aws/index.html#module-development-guidelines


#############################################################################
