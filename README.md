# Sines Docker's Containers Updater

**Sines** é um script Bash projetado para simplificar o gerenciamento de containers Docker, especialmente aqueles criados com Docker Compose. Ele oferece uma variedade de operações para listar, atualizar, reiniciar, visualizar logs e muito mais, tudo com uma interface amigável e suporte a cores no terminal.

Este script foi desenvolvido para **uso pessoal**, adaptado exclusivamente às minhas necessidades. No entanto, pode ser útil para outras pessoas com pouca experiência em Docker, fornecendo uma maneira simples e eficaz de gerenciar containers.

## Funcionalidades

- **Atualização de Containers**: Verifique e aplique atualizações para containers individuais (`upgrade`) ou todos de uma vez (`full-upgrade`), com confirmação interativa quando necessário.
- **Gerenciamento Simplificado**: Comandos como `restart`, `stop`, `logs`, `list` e `source` para interagir com seus containers.
- **Suporte a Docker Compose**: Trabalha diretamente com arquivos `docker-compose.yml` para pulls e recriações.
- **Segurança**: Inclui backups manuais antes de atualizações e tratamento robusto de erros.

## Pré-requisitos

- **Docker**: Instale o Docker no seu sistema ([instruções oficiais](https://docs.docker.com/get-docker/)).
- **Docker Compose**: Certifique-se de que o Docker Compose está disponível ([instruções oficiais](https://docs.docker.com/compose/install/)).
- **Bash**: O script foi projetado para rodar em ambientes com Bash (Linux, macOS, WSL no Windows).
- **Permissões**: Execute o script com privilégios suficientes para interagir com o Docker (normalmente como root ou usuário no grupo `docker`).

## Instalação

Clone o repositório ou baixe o script:

```bash
git clone https://github.com/woldpt/sines
cd sines
```

Torne o script executável:

```bash
chmod +x sines
```

(Opcional) Mova o script para um diretório no seu `$PATH` para acesso global:

```bash
sudo mv sines /usr/local/bin/
```

## Uso

Execute o script com a sintaxe:

```bash
sines [operação] <container>
```

### Operações Disponíveis

| Operação     | Descrição                                               | Exemplo                       |
| ------------ | ------------------------------------------------------- | ----------------------------- |
| full-upgrade | Atualiza todos os containers com confirmação interativa | `sines full-upgrade`          |
| go           | Entra na pasta do docker-compose.yml correspondente     | `sines go meu-container`      |
| help         | Mostra a ajuda                                          | `sines help`                  |
| info         | Exibe informações detalhadas do container               | `sines info meu-container`    |
| list         | Lista containers com uso de CPU e memória               | `sines list`                  |
| logs 20      | Mostra logs em tempo real (20 últimas linhas)           | `sines logs meu-container 20` |
| pull         | Faz pull da imagem sem recriar o container              | `sines pull meu-container`    |
| purge        | Remove recursos não utilizados do Docker                | `sines purge`                 |
| restart      | Reinicia o container                                    | `sines restart meu-container` |
| source       | Exibe o `docker-compose.yml` do container               | `sines source meu-container`  |
| stop         | Pára o container                                        | `sines stop meu-container`    |
| upgrade      | Atualiza um container específico com backup             | `sines upgrade meu-container` |

## Exemplos

### Atualizar um container específico

```bash
sines upgrade meu-container
```

Verifica se há uma nova versão, cria um backup e recria o container se necessário.

### Atualizar todos os containers

```bash
sines full-upgrade
```

Lista todos os containers em execução, verifica atualizações e pergunta `Y/n` apenas para aqueles com novas versões.

### Ver logs de um container

```bash
sines logs meu-container
```

### Listar todos os containers com uso de recursos

```bash
sines list
```

## Notas

- O script assume que os containers foram criados com **Docker Compose** para operações como `upgrade`, `pull` e `full-upgrade`. Containers sem Compose são pulados com um aviso.
- As cores no terminal são habilitadas automaticamente em sessões interativas.
- Backups são criados antes de atualizações (nomeados como `<container>-backup-YYYYMMDD_HHMMSS`) para rollback manual, se necessário.

## Contribuição

Sinta-se à vontade para abrir **issues** ou **pull requests** . Sugestões de melhorias ou correções são bem-vindas!

## Autor

**woldpt** (2025)

## Licença

Este projeto é distribuído sob a **Unlicense**. Veja o arquivo [LICENSE](LICENSE) para mais detalhes.
