# Investigação de Phishing - Snapped Phish-ing Line (TryHackMe)

Este repositório contém a documentação e a análise forense realizada na sala **"Snapped Phish-ing Line"** da plataforma TryHackMe. O objetivo principal do laboratório foi investigar uma campanha ativa de phishing que simulava uma página de login do Office 365 e identificar os artefatos deixados pelo adversário.

## 🛡️ Habilidades e Conceitos Aplicados
* **Análise Forense Digital e Resposta a Incidentes (DFIR):** Investigação de servidores maliciosos e identificação de falhas de configuração.
* **Engenharia Reversa em Scripts Web:** Análise de código-fonte em PHP para entender o fluxo de exfiltração de dados.
* **Análise de Logs:** Triagem de arquivos de log para rastrear dados capturados e escopo do impacto.
* **Criptografia e Ofuscamento:** Uso do CyberChef para decodificação de strings ocultas e análise de integridade com hashes SHA256.

---

## 🕵️‍♂️ Resumo da Investigação Passo a Passo

### 1. Identificação de Diretório Exposto
Durante a análise do domínio utilizado pelo atacante (`kennaroads.buzz`), foi identificada uma vulnerabilidade de **Directory Listing** (Listagem de Diretórios) na pasta `/data`. Essa falha de configuração permitiu acesso direto à estrutura de arquivos do invasor, onde estava exposto o kit de phishing compactado.

### 2. Análise do Mecanismo de Coleta (`submit.php`)
Ao extrair o kit de phishing e analisar o arquivo responsável por processar as credenciais digitadas pelas vítimas (`submit.php`), foi inspecionada a função de envio de e-mails do PHP. O código revelou que os dados exfiltrados eram direcionados diretamente para o seguinte endereço controlado pelo adversário:
* **E-mail do atacante:** `m3npat@yandex.com`

### 3. Escopo do Impacto e Análise de Logs (`log.txt`)
O servidor mantinha um arquivo de log ativo chamado `log.txt`. A análise desse arquivo permitiu identificar a captura em tempo real de credenciais corporativas legítimas, além de mapear metadados das vítimas, como endereços IP de origem baseados nos Estados Unidos e Filipinas.

### 4. Decodificação de Artefatos Ocultos (`flag.txt`)
Na raiz do diretório de phishing, um arquivo oculto chamado `flag.txt` continha uma string codificada em Base64 e invertida (`fUxSVV8zSHRfaFQxd195NExwe01IVAo=`). 
Utilizando a ferramenta **CyberChef**, foram aplicadas as seguintes operações na receita:
1. `Reverse`
2. `From Base64`

O processo revelou com sucesso o valor secreto da flag do desafio: **`THM{pL4y_w1Th_tH3_URL}`**.

---

## 📁 Estrutura da Pasta
* `README.md` -> Este relatório detalhado com as evidências da investigação.

*Nota: Por questões de segurança, conformidade e boas práticas de desenvolvimento, os arquivos de código-fonte originais do kit de phishing não foram incluídos neste repositório público.*
