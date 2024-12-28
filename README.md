# SIEM Project - Security Information and Event Management

Este projeto implementa um ambiente de **SIEM (Security Information and Event Management)** para monitoramento de logs de dispositivos e servidores, com foco em segurança cibernética e detecção de ameaças.

## Objetivos do Projeto

- Centralizar logs de dispositivos de rede e servidores.
- Detectar eventos suspeitos ou maliciosos em tempo real.
- Criar dashboards e alertas personalizados para monitoramento.
- Aumentar a visibilidade do ambiente de rede e segurança.

## Tecnologias Utilizadas

- **Wazuh**: Plataforma de SIEM e HIDS (Host Intrusion Detection System).
- **ELK Stack**: Solução de coleta e análise de logs (Elasticsearch, Logstash, Kibana).
- **Graylog**: Para análise de logs e criação de alertas.
- **Linux**: Ubuntu Server como sistema operacional base.

## Requisitos do Ambiente

### Hardware
- **CPU**: 4 vCPUs ou mais.
- **Memória**: 8-16 GB RAM.
- **Armazenamento**: SSD de pelo menos 100 GB.

### Software
- **Sistema Operacional**: Ubuntu Server ou CentOS.
- **Dependências**:
  - Java (para Elasticsearch e Graylog).
  - MongoDB (para Graylog).
  - Curl, wget, e pacotes básicos de administração.

## Configuração do Ambiente

### 1. Instalação do SIEM
Escolha uma das ferramentas abaixo:

#### Wazuh
```bash
curl -s https://packages.wazuh.com/4.4/wazuh-install.sh | bash
```

#### ELK Stack
```bash
sudo apt update
sudo apt install elasticsearch logstash kibana
```

#### Graylog
```bash
sudo apt update
sudo apt install graylog-server
```

### 2. Configuração de Logs

#### Dispositivos de Rede
- Configure o envio de logs via Syslog:
  ```
  logging host <IP_DO_SIEM>
  logging trap informational
  ```

#### Servidores Windows
- Instale e configure o agente **Winlogbeat** para enviar eventos de segurança:
  ```powershell
  .\winlogbeat.exe setup
  .\winlogbeat.exe -e
  ```

#### Servidores Linux
- Configure o envio de logs com rsyslog:
  ```bash
  *.* @<IP_DO_SIEM>:1514
  ```

### 3. Criação de Regras e Dashboards
- Configure alertas para eventos críticos:
  - Falhas de login.
  - Alterações em privilégios administrativos.
  - Escaneamento de portas (via Nmap ou similar).
- Crie dashboards personalizados para visualização de métricas importantes.

## Testes

- Simule incidentes de segurança para validar os alertas e dashboards:
  - Tentativas de login inválidas.
  - Escaneamento de portas.
  - Transferência de arquivos suspeitos.


## Licença

Este projeto é licenciado sob a [MIT License](LICENSE).

---

Caso precise de mais informações ou suporte, entre em contato! 🚀
