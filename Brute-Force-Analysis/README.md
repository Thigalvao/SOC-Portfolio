# 🛡️ Relatório de Investigação de Incidente: Ataque de Força Bruta (Brute Force)

## 1. Resumo do Alerta
*   **ID do Alerta:** SOC-2026-BF01
*   **Severidade:** Alta
*   **Plataforma de Simulação:** LetsDefend / Laboratórios Práticos
*   **Descrição:** Detecção de múltiplas tentativas consecutivas e falhas de autenticação contra o endpoint de login de um servidor web institucional.

---

## 2. Linha do Tempo e Investigação dos Logs
Durante a triagem do alerta no ambiente simulado, foi realizada a extração e análise dos logs do servidor web (Nginx/Apache). Os seguintes artefatos técnicos foram identificados:

*   **IP de Origem da Ameaça:** `192.168.1.145` (Exemplo simulado do laboratório)
*   **Endpoint Alvo:** `POST /login.php`
*   **Volume de Requisições:** Mais de 250 requisições em um intervalo de 3 minutos.
*   **User-Agent Identificado:** `Mozilla/5.0 ... Hydra/9.1` (Evidência clara de uso de ferramenta automatizada de ataque).

### Análise de Código de Status HTTP:
*   As primeiras 249 requisições retornaram o status **HTTP 200** contendo no corpo da resposta a string `Login Failed` (Falha na autenticação).
*   A última requisição registrada às `14:32:10` retornou um redirecionamento **HTTP 302** (ou alteração no tamanho do payload), indicando que o atacante obteve **sucesso** ao quebrar a credencial do usuário administrado.

---

## 3. Indicadores de Comprometimento (IoCs) Detectados
*   **IP:** `192.168.1.145`
*   **Padrão de Ataque:** Requisições massivas automatizadas por dicionário (Wordlist).
*   **Contas Afetadas:** Conta de usuário `admin`.

---

## 4. Ações de Contenção e Mitigação Recomendadas (Escopo de SOC L1)
Para mitigar o incidente e restabelecer a segurança do ambiente, as seguintes medidas foram documentadas para execução:

1.  **Bloqueio de IP:** Criação de regra temporária no Firewall/WAF para bloquear todo o tráfego vindo do IP `192.168.1.145`.
2.  **Reset de Credenciais:** Forçar a redefinição imediata de senha da conta comprometida (`admin`), aplicando políticas de alta complexidade.
3.  **Implementação de Rate Limiting:** Recomendação para a equipe de engenharia para implementar limite de tentativas de login por IP e uso de CAPTCHA após 3 falhas consecutivas.
