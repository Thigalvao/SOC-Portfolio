Investigação de phishing - O phishing de Greenholt (TryHackMe)
Este repositório contém o artigo técnico e o processo de análise forense de e-mail realizado no laboratório prático "The Greenholt Phish" da plataforma TryHackMe. O objetivo foi analisar um e-mail suspeito, identificar técnicas de falsificação de identidade (spoofing) e extrair metadados de um artifício fraudulento.

🛠️ Cenário e Ferramentas Utilizadas
Ambiente: Linux Ubuntu (VM do laboratório)
Ferramentas de E-mail: Mozilla Thunderbird (Análise do cabeçalho bruto)
Ferramentas de Rede/DNS: nslookup
Análise de Artefatos: Terminal Linux ( sha256sum, file, ls)
🔍 Etapas da Investigação
1. Análise de Cabeçalho (Cabeçalhos de Email)
Ao funcionar o arquivo bruto challenge.eml, foi baseado no fluxo de tráfego dos servidores e nos mecanismos de autenticação do domínio remetente ( mutawamarine.com):

IP de Origem do Servidor de Ataque: 192.119.71.157
Falha de SPF: O cabeçalho registrado Received-SPF: Fail. O IP do remetente não estava listado na política autorizada do domínio.
Política DMARC: Foi realizada uma consulta DNS manual ( nslookup -type=txt _dmarc.mutawamarine.com) que retornou a seguinte string de configuração: v=DMARC1; p=quarantine; fo=1 (A política p=quarantineinstrui o servidor de destino a isolar a mensagem caso ela falhe no SPF/DKIM).
2. Análise Forense do Anexo (Extração de Malware)
O e-mail continha um anexo suspeito simulando ser um documento importante. A investigação prosseguiu os seguintes passos no terminal:

Identificação de Evasão: O arquivo aparentava ser um arquivo Cabinet do Windows ( SWT_#09674321____PDF____.CAB), com tamanho em disco de aproximadamente 400 KB .
Análise de Assinatura Real: Ao rodar o comando file, descobriu-se que o atacante alterou a extensão para roubar gateways de segurança, mas a estrutura real do arquivo era um arquivo compactado RAR :
$ file SWT_#09674321____PDF____.CAB
SWT_#09674321____PDF____.CAB: RAR archive data, v5
