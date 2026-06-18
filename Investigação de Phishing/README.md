# Investigação de Phishing - O Phishing de Greenholt (TryHackMe)

Este repositório contém o artigo técnico e o processo de análise forense de e-mail realizado no laboratório prático **"The Greenholt Phish"** da plataforma TryHackMe. O objetivo foi analisar um e-mail suspeito, identificar técnicas de falsificação de identidade (spoofing) e extrair metadados de um artifício fraudulento.

---

## 🛠️ Cenário e Ferramentas Utilizadas

* **Ambiente:** Linux Ubuntu (VM do laboratório)
* **Ferramentas de E-mail:** Mozilla Thunderbird (Análise do cabeçalho bruto)
* **Ferramentas de Rede/DNS:** `nslookup`
* **Análise de Artefatos:** Terminal Linux (`sha256sum`, `file`, `ls`)

---

## 🔍 Etapas da Investigação

### 1. Análise de Cabeçalho (Cabeçalhos de E-mail)
Ao operar o arquivo bruto `challenge.eml`, a análise foi baseada no fluxo de tráfego dos servidores e nos mecanismos de autenticação do domínio enviado (`mutawamarine.com`):

* **IP de Origem do Servidor de Ataque:** `192.119.71.157`
* **Falha de SPF:** O cabeçalho registrado apresentou `Received-SPF: Fail`. O IP do remetente não estava listado na política autorizada do domínio.
* **Política DMARC:** Foi realizada uma consulta ao manual de DNS que retornou a string correspondente às regras do domínio:
```bash
  nslookup -type=txt _dmarc.mutawamarine.com
