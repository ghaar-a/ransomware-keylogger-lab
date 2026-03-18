# ransomware-keylogger-lab
# 🛡️ Cybersecurity Lab em Python

### Análise Prática de Comportamentos de Ransomware e Keylogger

---

## 📌 Visão Geral

Este projeto apresenta um laboratório prático em Python com foco na análise de comportamentos típicos de ameaças digitais, especificamente:

* **Ransomware (criptografia de arquivos)**
* **Keylogger (captura de entrada do usuário)**

O objetivo não é desenvolver malware funcional, mas sim **compreender como essas ameaças operam internamente**, permitindo a construção de estratégias eficazes de defesa.

---

## 🎯 Objetivos

* Demonstrar como arquivos podem ser criptografados e restaurados
* Explorar técnicas de captura de entrada via teclado
* Analisar riscos associados à exfiltração de dados
* Desenvolver pensamento voltado à **detecção e mitigação**

---

## ⚠️ Aviso de Segurança e Ética

Este projeto possui finalidade **exclusivamente educacional**.

🚫 O uso indevido dessas técnicas pode violar leis e privacidade.
🔒 Recomenda-se executar apenas em ambiente controlado (ex: máquina virtual).

O componente de envio de dados deve ser interpretado como **estudo de comportamento malicioso**, não como prática recomendada.

---

## 🏗️ Estrutura do Projeto

```bash
cyber-lab/
│
├── ransomware_sim/
│   ├── decryptor.py
│   └── chave.key
│
├── keylogger_sim/
│   ├── keylogger_file.py
│   ├── keylogger_email.py
│   └── log.txt
│
└── test_files/
```

---

## 🔐 Módulo 1 — Ransomware (Simulação de Descriptografia)

### 📖 Descrição

Este módulo implementa a **fase de recuperação de arquivos**, utilizando criptografia simétrica com a biblioteca `cryptography`.

### ⚙️ Funcionamento

* Carrega uma chave previamente gerada (`chave.key`)
* Percorre arquivos dentro do diretório `test_files`
* Descriptografa os arquivos utilizando `Fernet`

### 🔍 Destaques do Código

* Uso de `os.walk()` para varredura de diretórios
* Exclusão de arquivos críticos (ex: `.key`, script principal)
* Processamento automático em lote

### 🧠 Conceitos

* Criptografia simétrica (Fernet/AES)
* Manipulação de arquivos
* Automação de processos

---

## ⌨️ Módulo 2 — Keylogger (Captura de Teclas)

Este módulo é dividido em duas abordagens.

---

### 📄 2.1 Registro Local (Arquivo)

Captura eventos do teclado e armazena em `log.txt`.

### ⚙️ Funcionalidades

* Captura caracteres digitados
* Tratamento de teclas especiais:

  * Espaço → `" "`
  * Enter → `\n`
  * Tab → `\t`
  * ESC → `[ESC]`
* Ignora teclas modificadoras (Shift, Ctrl, Alt)

### 🧠 Conceitos

* Event listeners (`pynput`)
* Logging de entrada
* Tratamento de eventos

---

### 📡 2.2 Simulação de Exfiltração (Estudo)

⚠️ **Este componente representa comportamento típico de malware e deve ser tratado apenas como análise teórica.**

### 📖 Descrição

* Armazena entradas em memória
* Periodicamente tenta enviar os dados por e-mail

### ⚠️ Riscos Demonstrados

* Vazamento de dados sensíveis
* Comprometimento de credenciais
* Monitoramento invisível do usuário

### 🧠 Conceitos

* Automação com `Timer`
* Uso de SMTP
* Exfiltração de dados

---

## 🔄 Fluxo de Execução

1. Arquivos são preparados em `test_files/`
2. Processo de descriptografia é executado
3. Keylogger captura entradas localmente
4. (Teórico) dados podem ser enviados periodicamente
5. Logs são analisados

---

## 🛡️ Análise de Segurança

### 🔍 Indicadores de Comprometimento (IoCs)

* Arquivos sendo modificados em massa
* Criação de arquivos `.key`
* Processos acessando teclado constantemente
* Tráfego SMTP suspeito

---

## 🧱 Medidas de Defesa

### 🖥️ No sistema

* Uso de antivírus/EDR
* Monitoramento de processos
* Controle de permissões

### 🌐 Na rede

* Bloqueio de SMTP não autorizado
* Firewall com inspeção de tráfego

### 👤 No usuário

* Evitar executar arquivos desconhecidos
* Uso de autenticação multifator
* Conscientização em segurança

---

## 🧪 Tecnologias Utilizadas

* Python 3.x
* `cryptography` (Fernet)
* `pynput` (captura de teclado)
* `smtplib` (simulação de envio)

---

## 🚀 Possíveis Melhorias

* Implementar módulo de detecção em tempo real
* Criar dashboard de monitoramento
* Adicionar logs estruturados
* Simular resposta automatizada (bloqueio de processo)

---

## 🤝 Conclusão

Este projeto demonstra, de forma prática, como ameaças digitais podem operar em nível técnico.

Mais importante, ele reforça que:

> **Compreender o ataque é o primeiro passo para construir uma defesa eficaz.**

---

## 📎 Licença

Uso educacional recomendado. Sugere-se licença MIT.

---

## 👤 Autor

Projeto desenvolvido para fins de estudo em cibersegurança, com foco em análise prática e defesa de sistemas.

---
