# 🛡️ SOC & Blue Team Portfolio

Bem-vindo ao meu portfólio de Operações de Segurança (SOC) e Resposta a Incidentes. Este repositório documenta minhas análises técnicas, investigações de logs e resolução de cenários práticos de ameaças cibernéticas realizados em ambientes simulados.

---

## 👤 Sobre Mim
Profissional com sólida base analítica e experiência em ambientes de alta criticidade, focado em transição estruturada para a área de Cibersegurança. Atuo ativamente no monitoramento, triagem de alertas, análise de logs e resposta a incidentes (Blue Team), aplicando metodologias para identificação de Indicadores de Comprometimento (IoCs) e mitigação de riscos operacionais.

---

## 💻 Projetos e Análises Práticas

### 1. 📁 [Análise de Ataque de Força Bruta (Brute Force)](./Brute-Force-Analysis/)
*   **Descrição:** Investigação detalhada de logs de servidores web para identificação de tentativas massivas e consecutivas de login.
*   **Habilidades Aplicadas:** Análise de requisições HTTP (`POST /login`), correlação de *timestamps* para mapeamento do comportamento do atacante, identificação de assinaturas de *User-Agents* e detecção do momento exato do impacto.

### 2. 📁 [Detecção de XML External Entity (XXE)](./XXE-Injection-Analysis/)
*   **Descrição:** Triagem e contenção de incidentes envolvendo injeção de entidades externas XML na camada web.
*   **Habilidades Aplicadas:** Diagnóstico de parsers XML vulneráveis, identificação de parâmetros afetados, detecção de tentativas ilegítimas de leitura de arquivos estruturais confidenciais do sistema (diretório `/etc`) e análise de payloads maliciosos.

---

## 🛠️ Tecnologias e Ferramentas Praticadas
*   **SIEM:** Splunk, Elasticsearch
*   **Análise de Logs:** Logs de Servidores Web (Apache/Nginx), Logs de Sistema (Linux)
*   **Monitoramento e Redes:** Wireshark, Fundamentos do Protocolo TCP/IP
*   **Linguagens de Script:** Python para automação e segurança

---
📫 **Vamos nos conectar?** [Meu LinkedIn](https://www.linkedin.com/in/thiago-galv%C3%A3o-bernardes-9856a2185/)
