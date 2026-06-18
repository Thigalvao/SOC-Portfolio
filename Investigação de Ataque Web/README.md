# Investigação de Ataque Web - LetsDefend

Este repositório contém a documentação e a análise forense digital realizadas durante o laboratório prático "Investigate Web Attack" da plataforma LetsDefend. O objetivo foi analisar arquivos de log de auditoria (`access.log`) para identificar a cadeia de ações de um atacante contra um servidor web.

---

## 🛠️ Cenário e Artefatos Analisados

* **Ambiente Analisado:** Logs de servidor web (Aplicação bWAPP)
* **Artefato Principal:** `access.log` (Logs de requisições HTTP)
* **Foco da Investigação:** Identificação de táticas, técnicas e procedimentos (TTPs) do invasor através da correlação de timestamps, métodos HTTP e payloads.

---

## 🔍 Linha do Tempo e Etapas do Ataque

### 1. Reconhecimento Automatizado (Scanner Web)
A análise inicial dos logs apontou um volume massivo de requisições concentradas em curtos intervalos de tempo voltadas para o escaneamento de vulnerabilidades.
* **Ferramenta Identificada:** `Nikto` (Versão 2.1.6)
* **Evidência:** Identificado por meio da string explícita no campo de `User-Agent` registrada nas requisições.

### 2. Mapeamento de Estrutura e Diretórios
Logo após a varredura inicial, o atacante buscou mapear a estrutura interna do site para localizar painéis sensíveis e arquivos ocultos.
* **Técnica Utilizada:** `Directory Brute Force`
* **Evidência:** Requisições sequenciais de força bruta disparadas contra caminhos comuns do sistema em busca de respostas bem-sucedidas.

### 3. Ataque de Autenticação (Adivinhação de Credenciais)
Com o mapeamento de um diretório restrito contendo um painel de login, o ator de ameaça tentou realizar o ganho de acesso à aplicação.
* **Técnica Utilizada:** `Brute Force`
* **Evidência:** Múltiplas tentativas de login consecutivas passando diferentes combinações de usuários e senhas diretamente via parâmetros na URL.

### 4. Exploração e Persistência via Injeção
Após o comprometimento, o atacante escalou as ações para conseguir execução remota no servidor afetado.
* **Técnica de Exploração:** `Code Injection` (Injeção de Código PHP)
* **Primeira Carga Útil (Payload):** `whoami` (Utilizado para validar o nível de privilégio e o contexto de execução no sistema operacional).
* **Mecanismo de Persistência:** Tentativa de fixação de acesso através da criação de uma conta de usuário maliciosa no Windows, camuflada via codificação de URL.
  * **Payload bruto extraído do log:** `%27net%20user%20hacker%20Asd123!!%20/add%27`

---

## 🏆 Conclusão e Resultados
A investigação foi concluída com sucesso mapeando todas as fases do incidente. A correlação detalhada dos logs permitiu extrair os Indicadores de Comprometimento (IoCs) exatos, fornecendo insumos essenciais para atividades de contenção, remediação e engenharia de detecção dentro do SOC.

---
*Laboratório concluído com sucesso em junho de 2026.*
