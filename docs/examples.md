
=== "Exemplo 1 | ci-sum-2025"

    Clone o repositório:
    ```bash
    git clone https://github.com/gustavokubiack/ci-sum-2025.git
    cd ci-sum-2025/
    ```

    Crie o arquivo `app.def`:
    ```bash
    Bootstrap: docker
    From: python:3.13-slim

    %files
        app.py /app/app.py

    %post
        mkdir -p /app
        pip install --no-cache-dir --upgrade pip

    %environment
        export HOME=/app
        export PYTHONPATH=/app

    %runscript
        exec python3 /app/app.py
    ```

    Build:
    ```bash
    apptainer build app.sif app.def
    ```

    Execute:
    ```bash
    apptainer run app.sif
    ```

=== "Exemplo 2 | postgres"

    Crie o arquivo `postgres.def`:
    ```bash
    Bootstrap: docker
    From: postgres:15

    %labels
        Maintainer FundamentosDevOpsApptainer <apptainer@fundamentosdevops.com>
        Version 1.0

    %environment
        export PGDATA=/var/lib/postgresql/data
        export POSTGRES_USER=usuario
        export POSTGRES_PASSWORD=senha

    %runscript
        echo "Iniciando PostgreSQL..."
        exec docker-entrypoint.sh postgres

    %startscript
        echo "Rodando PostgreSQL no modo startscript..."
        exec docker-entrypoint.sh postgres
    ```

    Build:
    ```bash
    apptainer build postgres.sif postgres.def
    ```

    Execute:
    ```bash
    mkdir -p ./pgdata
    mkdir -p ./run_pg 
    apptainer run --bind ./pgdata:/var/lib/postgresql/data --bind ./run_pg:/var/run/postgresql postgres.sif
    ```

=== "Exemplo 3 | nginx"

    Crie o arquivo `index.html`:
    ```html
    <!DOCTYPE html>
    <html lang="pt-br">
        <head>
            <meta charset="UTF-8">
            <title>Nginx em Execução</title>
            <style>
                body {
                    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
                    background-color: #f4f4f4;
                    color: #333;
                    text-align: center;
                    padding: 50px;
                }
                h1 {
                    color: #2e8b57;
                }
                .container {
                    background-color: white;
                    padding: 40px;
                    margin: auto;
                    border-radius: 10px;
                    box-shadow: 0px 0px 15px rgba(0,0,0,0.1);
                    max-width: 600px;
                }
                footer {
                    margin-top: 40px;
                    font-size: 0.9em;
                    color: #666;
                }
            </style>
        </head>
        <body>
            <div class="container">
                <h1>🚀 Nginx está rodando com sucesso!</h1>
                <p>Esta página faz parte da apresentação da disciplina <strong>Fundamentos de DevOps</strong>.</p>
                <p>Servidor configurado e rodando via Apptainer 🎉</p>
            </div>
            <footer>
                Fundamentos de DevOps - 2025
            </footer>
        </body>
    </html>
    ```

    Crie o arquivo `nginx.def`:
    ```bash
    Bootstrap: docker
    From: nginx
    Includecmd: no

    %files
    index.html /usr/share/nginx/html/index.html

    %startscript
    nginx
    ```

    Build:
    ```bash
    sudo apptainer build nginx.sif nginx.def
    ```

    Inicie a instância:
    ```bash
    sudo apptainer instance start --writable-tmpfs nginx.sif web
    ```

    Liste as instâncias:
    ```bash
    sudo apptainer instance list
    ```