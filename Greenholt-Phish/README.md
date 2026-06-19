# Análise de Phishing: Caso "O Greenholt Phish" (TryHackMe)

## 📌 Visão Geral do Cenário
Este projeto documenta a investigação e resposta a um incidente de phishing direcionado utilizando técnicas reais de análise de e-mails maliciosos. O objetivo foi identificar os vetores de ataque, analisar artefatos (como cabeçalhos e anexos), extrair indicadores de comprometimento (IoCs) e mitigar a ameaça simulada dentro de um ambiente de SOC (Security Operations Center).

---

## 🛠️ Ferramentas Utilizadas
* **Análise de Cabeçalhos:** CyberChef / MXToolbox
* **Reputação de IP e Domínio:** VirusTotal / Cisco Talos
* **Análise de Anexos/Links:** Ambientes de Sandbox / Oletools (se aplicável no cenário)
* **Plataforma de Simulação:** TryHackMe

---

## 🕵️‍♂️ Fase de Investigação & Análise

### 1. Análise dos Metadados do E-mail
A investigação começou com a extração e leitura dos cabeçalhos brutos do e-mail suspeito para identificar a real origem da mensagem.
* **Remetente Declarado (Display Name):** [Inserir o nome que aparecia no remetente]
* **Endereço de E-mail Real (Return-Path / From):** [Inserir o e-mail real do atacante encontrado no cabeçalho]
* **Servidor de Origem (IP):** [Inserir o endereço IP do servidor que enviou o e-mail]
* **Destinatário:** [Inserir o e-mail do alvo interno da empresa]

### 2. Verificação de Autenticação de E-mail
Foram analisados os registros de segurança para validar se o e-mail sofreu spoofing:
* **SPF (Sender Policy Framework):** [Passou / Falhou - Explicar brevemente]
* **DKIM (DomainKeys Identified Mail):** [Válido / Inválido]
* **DMARC:** [Resultado da política]

### 3. Análise do Conteúdo e Engenharia Social
O corpo do e-mail utilizava técnicas clássicas de indução psicológica, como:
* **Gatilho de Urgência:** [Exemplo: solicitação de alteração de senha imediata ou verificação de fatura vencida]
* **Presença de Links Maliciosos:** A URL camuflada redirecionava o usuário para `[Inserir o link malicioso encontrado - lembre-se de defangar o link, ex: hxxp://site-malicioso[.]com]`.

### 4. Análise do Anexo (Se houver)
* **Nome do Arquivo:** `[Nome do arquivo]`
* **Hash (SHA256):** `[Inserir a Hash do arquivo para checagem em Sandbox]`
* **Comportamento:** [Breve descrição do que o anexo faz se aberto, ex: macro maliciosa, download de malware secundário]

---

## 📊 Indicadores de Comprometimento (IoCs) Identificados
| Tipo | Valor | Descrição |
| :--- | :--- | :--- |
| **IP** | `[Inserir IP]` | Servidor de envio malicioso / C2 |
| **Domínio** | `[Inserir Domínio]` | Domínio utilizado para a campanha / Hospedagem do Phishing |
| **URL** | `hxxps://...` | Link de destino do phishing |
| **Hash SHA256** | `[Inserir Hash]` | Hash do artefato malicioso analisado |

---

## 🛡️ Ações de Mitigação Recomendadas
Com base nas descobertas, as seguintes medidas defensivas seriam aplicadas em um ambiente corporativo real:
1. **Bloqueio Perimetral:** Adicionar o IP e o domínio identificados à lista de bloqueio (Blocklist) do Firewall, Proxy e Gateway de E-mail (SEG).
2. **Purga de E-mails:** Executar uma busca e remoção (Search and Purge) na caixa de entrada de outros colaboradores que possam ter recebido a mesma campanha.
3. **Revogação de Credenciais:** Caso algum usuário tenha interagido com o link, forçar a redefinição de senha imediatamente e revisar sessões ativas do M365/Google Workspace.
4. **Conscientização:** Compartilhar o caso com a equipe de Awareness para reforçar o treinamento interno contra engenharia social.

---

## 🏆 Conclusão e Aprendizados
A resolução com 100% de aproveitamento deste laboratório permitiu consolidar conceitos práticos de triagem de phishing em um nível de analista Tier 1/2 de SOC. A identificação rápida de IoCs e a leitura correta de cabeçalhos brutos são fundamentais para conter incidentes antes que eles se transformem em um comprometimento severo de rede.
