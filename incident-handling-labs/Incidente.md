# Processo de Tratamento de Incidentes - Casos de Estudo & Laboratórios 🛡️

Este repositório foi desenvolvido para documentar o meu progresso prático, metodologias aplicadas e relatórios de simulações focados em **Tratamento e Resposta a Incidentes (Incident Handling)**. 

Recentemente, concluí com sucesso o módulo prático de **Incident Handling Process** através da plataforma **Hack The Box Academy**, solidificando os conceitos fundamentais que guiam um analista de segurança defensiva (Blue Team) durante o ciclo de vida de uma violação cibernética.

---

## 📑 Ciclo de Vida do Tratamento de Incidentes Aplicado

Durante os laboratórios e simulações, apliquei metodologias estruturadas (alinhadas aos frameworks NIST e SANS) divididas em 6 fases críticas:

1. **Preparação (*Preparation*):** Configuração e auditoria de ferramentas de monitoramento e centralização de logs (Wazuh, Sysmon, Event Viewer).
2. **Detecção e Análise (*Detection & Analysis*):** Triagem de alertas de alta severidade em SIEM/plataformas de gerenciamento de casos (TheHive), identificando comportamentos anômalos no ecossistema corporativo.
3. **Contenção (*Containment*):** Estratégias para isolar sistemas afetados, bloquear conexões persistentes e mitigar o impacto imediato na rede.
4. **Erradicação (*Eradication*):** Remoção completa de componentes maliciosos (artefatos, malware persistente, contas comprometidas) após a identificação da causa raiz.
5. **Recuperação (*Recovery*):** Restauração segura de sistemas para o estado de produção operacional, validação de integridade e monitoramento contínuo pós-incidente.
6. **Lições Aprendidas (*Lessons Learned*):** Documentação técnica detalhada das falhas, criação de relatórios pós-incidente e melhoria das regras de detecção para mitigar ameaças futuras.

---

## 🛠️ Tecnologias e Frameworks Utilizados

*   **Plataformas de Análise:** SIEM (Wazuh Open Source), Gerenciador de Casos (TheHive).
*   **Investigação Forense de Logs:** Windows Event Logs, Sysmon Event Logs, Análise de Arquivos estruturados (JSON / CSV).
*   **Threat Intelligence & Engenharia de Detecção:** VirusTotal, CyberChef (Análise e decodificação de payloads e comandos obfuscados/Base64).
*   **Mapeamento de Ameaças:** Framework MITRE ATT&CK.

---

## 🚀 Conhecimentos Práticos Consolidados

*   **Identificação de Vetores de Ataque:** Análise de acessos não autorizados por meio de consoles web comprometidos (ex: gerenciadores de infraestrutura e exploits em aplicações expostas).
*   **Análise de Infraestrutura C2:** Rastreamento de conexões ativas estabelecidas por malwares (*Reverse Shells*), extração de IoCs (Indicadores de Comprometimento) como endereços IP remotos e portas suspeitas.
*   **Análise de Artefatos Maliciosos:** Engenharia reversa básica de linhas de comando executadas nativamente no sistema (ex: PowerShell obfuscado utilizando flags como `-EncodedCommand`, `-WindowStyle Hidden` e payloads de download do tipo `Invoke-Expression / IEX`).
*   **Identificação de Movimentação Lateral e Credenciais:** Rastreamento e auditoria de execução de ferramentas de dumping de credenciais em memória (como Mimikatz) utilizando logs do Sysmon para identificar o contexto domínio\usuário (`SubjectDomainName` / `SubjectUserName`).

---

## 🔗 Conecte-se Comigo

*   **LinkedIn:** [Seu Nome de Usuário do LinkedIn](https://linkedin.com/in/seu-perfil)
*   **Plataforma de Treinamento:** Desafios práticos validados via Hack The Box Academy.
