# Instalação do Apptainer

O **Apptainer** é uma ferramenta de containers amplamente utilizada em ambientes de pesquisa, HPC e computação científica. Ele permite criar e executar containers de forma segura e eficiente, mesmo em sistemas onde você não tem permissões de superusuário.

Escolha sua distribuição para começar:

=== "Ubuntu / Debian"

    ```bash
    sudo apt update
    sudo apt install -y wget
    cd /tmp
    wget https://github.com/apptainer/apptainer/releases/download/v1.4.0/apptainer_1.4.0_amd64.deb
    sudo apt install -y ./apptainer_1.4.0_amd64.deb
    ```


=== "Fedora"
    
    ```bash
    sudo dnf install -y epel-release
    sudo dnf install -y apptainer
    ```