# ansible-p01-wordpress
Projeto para aprofundar os conhecimentos sobre Ansible.

O projeto utiliza como motivação a criação de uma aplicação wordpress em 3 camadas, utilizando Ansible para provisionar as diferentes máquinas.

Durante o percurso do projeto foi explorado como o ansible trabalha com o seu arquivo de playbook e arquivo de inventário. Definindo vários grupos de hosts e suas holes específicas, cada hole com suas tasks e handlers específicas. Também foi visto a utilização de váriaveis e templates.

Utilizando Vagrant criamos três máquinas virtuais. Uma para conter uma base de dados MySQL. Uma para conter um servidor Apache com PHP, que será utilizado para disponibilizar uma aplicação Wordpress. E uma última máquina virtual para a execução do Ansible, já que essa é uma ferramenta que depende de um ambiente linux.
