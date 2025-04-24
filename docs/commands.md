# Comandos Básicos do Apptainer

A tabela abaixo apresenta os comandos mais comuns do Apptainer e uma breve descrição de cada um:

| Comando | Descrição |
|--------|-----------|
| `apptainer build imagem.sif receita.def` | Cria uma imagem `.sif` a partir de um arquivo de definição `.def`. Equivalente a um `Dockerfile`. |
| `apptainer exec imagem.sif comando` | Executa um comando dentro da imagem. Ex: `ls`, `python`, etc. |
| `apptainer shell imagem.sif` | Abre um shell interativo dentro da imagem. Útil para depuração. |
| `apptainer run imagem.sif` | Executa o script padrão definido no `%runscript` da imagem. |
| `apptainer run --bind /host:/container imagem.sif` | Faz bind de um diretório do host para dentro do container. |
| `apptainer inspect imagem.sif` | Exibe informações sobre a imagem (`labels`, `env`, `runscript`, etc.). |
| `apptainer instance list` | Exibe informações sobre as instâncias. |
| `apptainer help` | Para verificar todos os comandos disponíveis. |
