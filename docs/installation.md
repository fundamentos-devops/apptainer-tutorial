# Instalação do Apptainer
<p align="justify">
    O <b>Apptainer</b> é uma ferramenta de containers amplamente utilizada em ambientes de pesquisa, HPC e computação científica. Ele permite criar e executar containers de forma segura e eficiente, mesmo em sistemas onde você não tem permissões de superusuário.
</p>

## Pré-requisitos

O Apptainer é executado nativamente no Linux, mas também pode ser utilizado em Windows e macOS por meio de máquinas virtuais (VMs). Abaixo estão os pré-requisitos recomendados para instalação e uso:

- **Sistema operacional**: 
  - Linux (nativamente)  
  - Windows/macOS (via máquinas virtuais)

- **Espaço em disco**:  
  - Aproximadamente 200 MiB após compilação e instalação

- **Requisitos de hardware**:  
  - Nenhum requisito específico de CPU ou memória para execução
  - Recomendado pelo menos 2 GB de RAM ao compilar a partir do código-fonte

## Instalação

Escolha sua distribuição:

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