# Ansible Exemplo

## Run

Criar 3 servidores utilizando o Vagrant. Um para rodar o ansible, um para o mysql e outro para o wordpress

```bash
vagrant up
```

## Exemplo 1

Exemplo de provisionamento de wordpress utilizando Ansible. As tasks e handlers estão todas agrupadas em um único arquivo (`provision.yml`).

```bash
vagrant ssh ansible
sudo ansible-playbook /vagrant/exemplo1/provision.yml -i /vagrant/exemplo1/hosts
```

## Exemplo 2

Exemplo de provisionamento de wordpress utilizando Ansible. As tasks e handlers estão modularizadas em roles.

```bash
vagrant ssh ansible
sudo ansible-playbook /vagrant/exemplo2/provision.yml -i /vagrant/exemplo2/hosts
```

## Exemplo 3

Exemplo utilizando como target uma máquina Windows

```bash
vagrant ssh ansible
sudo ansible-playbook /vagrant/exemplo3/provision.yml -i /vagrant/exemplo3/hosts
```

## Exemplo 4

Utilizando variáveis por ambiente (dev)

```bash
vagrant ssh ansible
sudo ansible-playbook /vagrant/exemplo4/provision.yml -i /vagrant/exemplo4/hosts
```

Utilizando variáveis criptografadas (prod). Vault pass: `senha`

```bash
vagrant ssh ansible
sudo ansible-playbook /vagrant/exemplo4/provision.yml -i /vagrant/exemplo4/hosts --ask-vault-pass --extra-vars 'stage=prod'
```
