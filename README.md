# ransomware-keylogger-lab
# Simulação de Malware em Python: Ransomware e Keylogger

**Projeto Prático – Formação em Segurança da Informação com Python**

Este repositório apresenta a implementação controlada e educativa de dois tipos de malware simulados: um ransomware baseado em criptografia simétrica e um keylogger com captura de keystrokes e exfiltração via e-mail. O objetivo é compreender o funcionamento técnico dessas ameaças, seus mecanismos de persistência e impacto, bem como identificar vetores de detecção e estratégias de mitigação.

**Ambiente de execução**: VirtualBox com snapshot isolado. Nenhum código foi executado em ambiente de produção ou máquina hospedeira.

## Objetivos do Projeto

- Implementar um ransomware simulado com criptografia AES e nota de resgate  
- Desenvolver um keylogger com captura global de teclas e envio automático de logs  
- Documentar o comportamento observado e propor medidas técnicas de prevenção e detecção  
- Gerar documentação técnica completa para fins de portfólio e aprendizado

## Tecnologias Utilizadas

- Python 3.10+  
- cryptography (Fernet – AES-128-CBC + HMAC-SHA256)  
- pynput (captura de eventos de teclado em nível de sistema)  
- smtplib + ssl (envio de e-mail via Gmail com App Password)  
- PyInstaller (opcional – geração de executável standalone sem console)

## Estrutura do Repositório
malware-simulado/
├── ransomware/
│   ├── ransomware.py          # Script de criptografia e nota de resgate
│   ├── decryptor.py           # Script de recuperação com chave Fernet
│   ├── create_test_files.py   # Geração de arquivos de teste
│   ├── ransom_note.txt        # Modelo de mensagem de resgate
│   └── test_files/            # Diretório com arquivos para simulação
│
├── keylogger/
│   ├── keylogger.py           # Captura de teclas + envio por e-mail
│   ├── email_sender.py        # Módulo auxiliar para exfiltração
│   └── log.txt                # Exemplo de saída capturada

 
## 1. Ransomware Simulado

### Funcionamento Técnico

1. Geração de chave Fernet única por execução  
2. Varredura recursiva da pasta `test_files/`  
3. Criptografia de arquivos com extensões selecionadas (.txt, .docx, .pdf, .jpg, etc.)  
4. Substituição do conteúdo original pelo cifrado + extensão `.ransomware`  
5. Geração e exibição de nota de resgate (texto simples ou pop-up básico)

### Principais Trechos de Código

```python
from cryptography.fernet import Fernet

key = Fernet.generate_key()
cipher = Fernet(key)

with open(filepath, 'rb') as f:
    data = f.read()
    encrypted_data = cipher.encrypt(data)

with open(filepath + '.ransomware', 'wb') as f:
    f.write(encrypted_data)
Resultados Observados

Tempo médio de criptografia: < 5 segundos para ~20 arquivos
Recuperação 100% funcional via decryptor.py com a chave correta
Detecção imediata por Windows Defender (comportamento heurístico) quando executado fora de exclusão

2. Keylogger Simulado
Funcionamento Técnico

Listener global via pynput.keyboard.Listener
Captura diferenciada: caracteres imprimíveis (.char) vs. teclas especiais (AttributeError)
Tratamento de encoding UTF-8 para suportar acentos e caracteres especiais
Registro incremental em log.txt com timestamp
Envio periódico (ex.: a cada 60 s) via SMTP com autenticação segura

Principais Trechos de Código
Pythondef on_press(key):
    try:
        with open("log.txt", "a", encoding="utf-8") as f:
            f.write(key.char)
    except AttributeError:
        with open("log.txt", "a", encoding="utf-8") as f:
            if key == keyboard.Key.space:
                f.write(" ")
            elif key == keyboard.Key.enter:
                f.write("\n")
            # ... demais tratamentos
Resultados Observados

Captura fiel em qualquer aplicação (bloco de notas, navegador, editores)
Envio bem-sucedido via Gmail (App Password obrigatório)
Executável gerado com PyInstaller --onefile --noconsole permanece invisível na barra de tarefas

Medidas de Detecção e Mitigação Recomendadas

Prevenção:
Backup offline ou 3-2-1 (3 cópias, 2 mídias, 1 offsite)
Desativação de macros e execução de arquivos não confiáveis
Uso de App Passwords ou autenticação sem senha em serviços de e-mail

Detecção:
Monitoramento de processos (Process Explorer, Sysinternals)
Análise heurística e comportamental (Defender, EDR)
Inspeção de tráfego de rede (Wireshark) para detecção de exfiltração SMTP

Resposta:
Isolamento imediato da máquina afetada
Restauração a partir de backup limpo
Análise forense pós-incidente (não pagar resgate)


Como Executar com Segurança

Clone o repositório
Crie um snapshot da máquina virtual
Instale dependências: pip install -r requirements.txt
Gere arquivos de teste: python create_test_files.py
Execute os scripts individualmente dentro da VM

Aviso: Nunca execute esses códigos fora de ambiente isolado.
Conclusão Técnica
A simulação demonstrou que ameaças como ransomware e keylogger podem ser implementadas com poucas dezenas de linhas de código Python, utilizando bibliotecas legítimas e amplamente disponíveis. Isso reforça a importância de controles de aplicação (whitelisting), monitoramento comportamental e educação contínua como barreiras primárias contra esses vetores.
Qualquer sugestão de melhoria ou correção técnica é bem-vinda via Issues.


