git clone https://github.com/sparklecast1/ansible.git

cd anible

ansible-playbook -vv -i inventory/hosts -l test-stand playbooks/baget.yml -k -K -u root



TESTED:
ansible version = ansible 2.8.1
python = 2.7.5
Centos 7 - 3.10.0-957.21.3.el7.x86_64
