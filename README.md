# Linux Nginx Percona PHP Deployment Examples

- Requires Ansible 1.2 or newer
- Expects CentOS/RHEL 6.x hosts

This playbooks will simply setup and configure all the required software to run LNMPP(Linux Nginx Percona PHP) stacks. It also have some examples for multiple environments directories structure such as local, staging, production etc. Just make sure to adjust your hosts file accordingly on each environments

Deploying to staging environment:

	ansible-playbook -i environments/staging/hosts build-all.yml

Deploying to local vagrant environment:

	ansible-playbook -i environments/local/hosts build-all.yml

### Running Ansible Development on your local vagrant box

This is the quick way to test this ansible playbook on your local. You will need to install this following software:

- VirtualBox
- Vagrant

After that, create  ssh-key that will be used to run the ansible deployment to your vagrant box and build your vagrant box:

	ssh-keygen -t rsa -b 2048
	cd /path/to/your/repository
	git clone https://github.com/alamsyahho/ansible-lnpp-example.git
	cd /path/to/your/repository/ansible-lnpp-example
	vagrant plugin install vagrant-hostmanager
	vagrant up

When everything are done, simply run this ansible playbook command from your preferred terminal:

	ansible-playbook -i environments/local/hosts build-all.yml

###### You're done! Access your local vagrant on http://vagrant.local

### Ideas for Improvement

Here are some ideas for ways that these playbooks could be extended:

- Provide some sample for application deployment, such as php laravel framework deployment
- Add more parameter into my.cnf and configure most of its configuration parameter such as buffer pool, etc
- Add supervisord installation
- Redis installation from source. Current playbook only install redis 2.4 which quite outdated
