# 🛡️ Relatório de Investigação de Incidente: Injeção de Entidade Externa XML (XXE)

## 1. Resumo do Alerta
*   **ID do Alerta:** SOC-2026-XXE02
*   **Severidade:** Alta
*   **Plataforma de Simulação:** LetsDefend / Laboratórios Práticos
*   **Descrição:** Identificação de requisições HTTP maliciosas contendo payloads estruturados em XML com o objetivo de ler arquivos locais confidenciais do servidor (Local File Inclusion - LFI).

---

## 2. Processo de Análise e Triagem de Logs
Durante o monitoramento de tráfego e análise de requisições enviadas para a aplicação web corporativa, a seguinte atividade anômala foi identificada e isolada:

*   **Endpoint Alvo:** `POST /api/v1/xml-parser`
*   **Vulnerabilidade Explorada:** Falha na configuração do parser XML interno, que aceita e processa referências a entidades externas configuradas pelo usuário.
*   **Comportamento do Atacante:** Envio de um payload via método `POST` contendo a declaração de sistema `<!ENTITY xxe SYSTEM "file:///etc/passwd">`.

### Evidência de Impacto e Sucesso:
*   A análise do tamanho da resposta HTTP (Payload Size) e do log de transações revelou que o servidor respondeu com o código **HTTP 200 OK**.
*   No corpo da resposta da API, foram expostas com sucesso as linhas estruturais do arquivo interno do sistema Linux (`root:x:0:0:root:/root:/bin/bash`), confirmando o vazamento de dados e o sucesso da exploração por parte da ameaça externa.

---

## 3. Indicadores de Comprometimento (IoCs)
*   **Assinatura de Tráfego:** Strings contendo `SYSTEM "file://` dentro de requisições HTTP do tipo XML.
*   **Arquivo Alvo:** `/etc/passwd`
*   **Impacto:** Quebra de confidencialidade de arquivos estruturais do sistema operacional do servidor web.

---

## 4. Medidas de Mitigação e Recomendação Técnica
Como Analista de SOC, as seguintes recomendações foram documentadas e escaladas para as equipes de infraestrutura e desenvolvimento:

1.  **Desativação de DTDs Externas (Remediação Definitiva):** Configurar o parser XML da aplicação para desabilitar completamente o processamento de entidades externas (External Entities) e declarações de tipos de documentos (DTDs).
2.  **Ajuste de Regras de WAF (Web Application Firewall):** Implementar ou habilitar assinaturas de segurança específicas no WAF para bloquear requisições que contenham padrões de injeção de arquivos locais (`file://`, `/etc/passwd`, `win.ini`).
3.  **Princípio do Menor Privilégio:** Garantir que o usuário do sistema operacional que executa o serviço do servidor web não possua permissões de leitura em arquivos confidenciais globais que não sejam estritamente necessários para a aplicação funcionar.
