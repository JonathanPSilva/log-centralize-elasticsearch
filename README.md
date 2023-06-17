# Centralização de Logs
    O objetivo de projeto é centralizar os logs em um Servidor remoto e usar uma ferramenta de análise como Elasticsearch para visualizar esses logs.
    
    Em um ambiente de produção os container não devem rodar no Servidor de logs, mas sim em uma maquina separada. Caso você perca a maquina você não perde os logs.
    
    Nesse procedimento será feito em uma maquina só. Ajuste conforme necessário.


# Requisitos:
    - rsyslog
    - docker

# Observações:
    - A configuração abaixo foi feita em uma ambiente rodando a distro Linux Mint(Ubuntu).
    - Ajuste conforme sua distro.


# Preparação do Ambiente:
## Criando diretório onde ficará os logs que são recebidos remotamente via rsyslog.
sudo mkdir /var/log/rsyslog

## Ajustando permissões para o diretório
sudo chown -R syslog:adm /var/log/rsyslog


## Configurando Rsyslog
## Fazer um backup do arquivo de configuração default do rsyslog
sudo cp /etc/rsyslog.conf /etc/rsyslog.conf.default

## Copiar ou ajustar as configurações de acordo com o rsyslog.conf e os arquivos no diretorio rsyslog.d deste projeto.

## Restart no serviço
systemctl restart rsyslog.service

## Habilitando na inicialização
systemctl enable rsyslog.service