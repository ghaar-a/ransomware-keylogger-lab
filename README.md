# ransomware-keylogger-lab 
# 🛡️ Cybersecurity Lab em Python

### Simulação Controlada de Ransomware e Keylogger com Foco em Defesa

---

## 📌 Visão Geral

Este projeto tem como objetivo construir um **laboratório prático de cibersegurança**, utilizando Python, para demonstrar — de forma **ética, controlada e educacional** — como determinadas ameaças digitais operam.

Mais importante do que simular ataques, este projeto enfatiza **detecção, mitigação e prevenção**, preparando o desenvolvedor para compreender comportamentos maliciosos e atuar defensivamente no mundo real.

---

## 🎯 Objetivos do Projeto

* Simular o comportamento de um **ransomware** em ambiente controlado
* Demonstrar a captura de entradas de teclado em modo **educacional e transparente**
* Implementar mecanismos básicos de **detecção de atividades suspeitas**
* Consolidar conhecimentos sobre **criptografia, monitoramento e segurança de sistemas**
* Desenvolver uma visão crítica sobre **ameaças reais e suas defesas**

---

## ⚠️ Aviso Importante (Ética e Segurança)

Este projeto foi desenvolvido com propósito **estritamente educacional**.

🔒 Garantias:

* Nenhuma funcionalidade furtiva foi implementada
* Não há coleta de dados sensíveis reais
* Não ocorre envio de dados para redes externas
* Todas as simulações são limitadas a ambientes controlados

🚫 Este projeto **não deve ser utilizado para fins maliciosos**.

---

## 🏗️ Estrutura do Projeto

```
cyber-lab/
│
├── ransomware_sim/
│   ├── encryptor.py
│   ├── decryptor.py
│   ├── file_generator.py
│   └── ransom_note.txt
│
├── keylogger_sim/
│   ├── key_capture.py
│   ├── logger.py
│   └── demo_mode.py
│
├── defense/
│   ├── monitor.py
│   ├── heuristics.py
│   └── report.md
│
├── utils/
│   └── crypto_utils.py
│
├── main.py
└── README.md
```

---

## 🔐 Módulo 1 — Ransomware Simulado

### 📖 Descrição

Este módulo simula, de forma segura, o comportamento de um ransomware, utilizando criptografia para bloquear arquivos em um diretório controlado.

### ⚙️ Funcionalidades

* Geração de arquivos de teste
* Criptografia de arquivos com chave local
* Descriptografia dos arquivos
* Exibição de mensagem de “resgate” (educativa)

### 🧠 Conceitos abordados

* Criptografia simétrica (ex: AES/Fernet)
* Manipulação de arquivos
* Automação de processos em lote

---

## ⌨️ Módulo 2 — Captura de Teclas (Modo Educacional)

### 📖 Descrição

Simulação de captura de entrada do teclado, com total transparência ao usuário.

### ⚙️ Funcionalidades

* Captura de eventos de teclado em tempo real
* Registro em arquivo `.txt`
* Execução com aviso explícito ao usuário

### 🔒 Limitações intencionais

* Sem execução em segundo plano
* Sem ocultação
* Sem envio de dados externos
* Sem persistência no sistema

### 🧠 Conceitos abordados

* Hooks de teclado
* Logging de eventos
* Privacidade e ética em software

---

## 🛡️ Módulo 3 — Detecção e Defesa

### 📖 Descrição

Implementação de mecanismos simples de monitoramento para identificar comportamentos suspeitos semelhantes a malware.

### ⚙️ Funcionalidades

* Monitoramento de alterações em arquivos
* Identificação de atividade anômala
* Geração de alertas

### 🔍 Heurísticas utilizadas

* Modificação em massa de arquivos
* Alterações rápidas de extensões
* Frequência elevada de escrita em disco
* Captura contínua de entradas

### 🧠 Conceitos abordados

* Detecção baseada em comportamento
* Heurística em segurança
* Fundamentos de EDR (Endpoint Detection and Response)

---

## 🔄 Fluxo de Execução

1. Gerar arquivos de teste
2. Executar criptografia (simulação de ransomware)
3. Analisar impacto nos arquivos
4. Executar descriptografia
5. Iniciar captura de teclado (modo visível)
6. Executar módulo de monitoramento
7. Analisar logs e alertas

---

## 🧪 Tecnologias Utilizadas

* Python 3.x
* Bibliotecas padrão (`os`, `time`, `logging`)
* Biblioteca de criptografia (ex: `cryptography`)
* Biblioteca de captura de teclado (ex: `pynput`, em modo controlado)

---

## 📊 Resultados Esperados

Ao final do projeto, espera-se que o desenvolvedor seja capaz de:

* Entender como ataques podem ser estruturados
* Identificar padrões de comportamento malicioso
* Aplicar conceitos de defesa em sistemas reais
* Desenvolver pensamento crítico em segurança

---

## 🛡️ Medidas de Prevenção (Mundo Real)

* Uso de antivírus e EDR
* Backups regulares e isolados
* Atualizações de sistema
* Restrição de permissões
* Monitoramento contínuo
* Conscientização do usuário

---

## 🚀 Possíveis Extensões

* Dashboard de monitoramento (CLI ou Web)
* Integração com ferramentas de log (SIEM)
* Uso de Machine Learning para detecção
* Simulação de outros vetores de ataque

---

## 🤝 Conclusão

Este projeto vai além da implementação técnica: ele representa uma jornada de aprendizado sobre **como ataques funcionam — e principalmente como se defender deles**.

A compreensão prática desses conceitos é essencial para qualquer profissional que deseja atuar com desenvolvimento seguro, análise de vulnerabilidades ou cibersegurança.

---

## 📎 Licença

Este projeto é de uso educacional. Recomenda-se a adoção de uma licença como MIT para compartilhamento.

---

## 👤 Autor

Desenvolvido como parte de estudos práticos em cibersegurança e programação em Python.

---
