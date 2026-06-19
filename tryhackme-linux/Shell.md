# TryHackMe: Linux Shells - Estudo de Caso e Análise de Logs

Repositório dedicado à documentação do meu progresso e aprendizado no laboratório **Linux Shells** da plataforma TryHackMe. O objetivo deste laboratório foi aprofundar o conhecimento prático na linha de comando Linux, manipulação de fluxos e análise de arquivos de auditoria para fins de segurança cibernética.

---

## 🛠️ Tecnologias e Conceitos Praticados

*   **Sistemas Operacionais:** Linux (Distribuição baseada em Debian/Ubuntu).
*   **Investigação de Logs:** Análise de histórico de autenticação e atividades do sistema.
*   **Comandos Essenciais:** `grep`, `cat`, `ls`, `find` e operadores de redirecionamento de fluxo.

---

## 📝 Resumo do Laboratório & Desafios

Durante o desafio prático dentro do AttackBox, foram propostas questões focadas na busca de padrões ocultos e informações específicas no sistema de arquivos.

### Cenário 1: Filtragem de Informações com `grep`
Para localizar a primeira pista ("Qual arquivo contém a palavra-chave?"), foi necessário varrer diretórios do sistema em busca de strings específicas. 

*   **Abordagem Inicial:** Varreduras amplas no diretório raiz (`/`) podem travar ou gerar erros de permissão em diretórios virtuais (como `/proc` ou `/sys`).
*   **Solução Eficiente:** Filtragem direcionada utilizando o redirecionamento de erros para ocultar mensagens de permissão negada:
```bash
    grep -rn "termo-da-busca" /var/log/ 2>/dev/null
    ```
*   **Resultado:** Identificação do arquivo de auditoria crítico: `authentication.log`.

### Cenário 2: Inspeção do Arquivo de Log
Com o arquivo identificado, o passo seguinte exigia extrair informações internas ("Onde o gato está dormindo?"). arquivos de log reais podem conter milhares de linhas, tornando a leitura manual inviável.

*   **Comando aplicado:** Uso do `grep` com a flag `-i` (ignore case) para capturar a linha exata que continha o padrão textual procurado dentro do arquivo de log correspondente.

---

## 🧠 Principais Aprendizados (Takeaways)

1. **Eficiência na Busca:** O uso correto de flags como `-r` (recursivo) e `-n` (mostrar número da linha) acelera drasticamente o processo de triagem em uma análise de incidentes.
2. **Tratamento de Saídas (`2>/dev/null`):** Essencial para limpar o terminal de ruídos (erros de leitura) e focar estritamente nos dados que importam.
3. **Análise de Logs de Autenticação:** Compreensão prática de como o Linux registra eventos no ecossistema `/var/log/`, peça-chave para auditorias de segurança (Blue Team).

---

🚀 *Acompanhando a consistência: Laboratório concluído durante a trilha de aprendizado contínuo em segurança da informação!*
