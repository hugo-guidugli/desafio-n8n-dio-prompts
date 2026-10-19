# Desafio Criativo — Automação de Pedidos com n8n

## 1. Objetivo

Desenvolver uma proposta de automação utilizando o n8n para registrar pedidos comerciais, armazenar os dados de vendas e enviar e-mails de confirmação automaticamente.

A solução busca reduzir tarefas manuais, minimizar erros de registro e melhorar a organização das informações comerciais.

## 2. Ferramentas utilizadas

- **n8n:** orquestração da automação.
- **Google Forms:** coleta das informações dos pedidos.
- **Google Sheets:** armazenamento dos registros.
- **Gmail:** envio dos e-mails de confirmação.

## 3. Prompt desenvolvido

Atue como um especialista em automação de processos com n8n, com experiência em integrações com Google Workspace, validação de dados e boas práticas de desenvolvimento de workflows.

Projete uma automação para registrar pedidos comerciais, armazenar os dados de vendas e enviar uma confirmação automática por e-mail.

**Público-alvo:** equipe comercial e gerencial.

**Requisitos:**

1. Receber os dados enviados pelo Google Forms.
2. Validar os campos obrigatórios e o formato do endereço de e-mail.
3. Ignorar registros com e-mail ausente ou inválido.
4. Organizar os dados e registrar os pedidos no Google Sheets.
5. Calcular o valor total com base na quantidade e no valor unitário, quando disponíveis.
6. Enviar um e-mail de confirmação pelo Gmail somente após o registro bem-sucedido.
7. Tratar falhas de integração para evitar confirmações indevidas.

Explique quais nós devem ser utilizados no n8n, a função e a configuração de cada nó, as conexões entre as etapas, as condições de decisão, as expressões relevantes e os testes necessários.

Apresente a solução de forma didática, com um diagrama textual do workflow, priorizando simplicidade, confiabilidade, segurança e facilidade de manutenção.

## 4. Lógica do workflow

1. **Recebimento:** detectar uma nova resposta do formulário por meio de uma integração compatível com o n8n.
2. **Validação:** verificar se o e-mail está presente e possui formato válido.
3. **Decisão:** utilizar o nó IF para separar os registros válidos dos inválidos.
4. **Preparação:** organizar os campos e calcular o valor total, quando aplicável.
5. **Registro:** adicionar os dados do pedido ao Google Sheets.
6. **Confirmação:** enviar o e-mail pelo Gmail após a gravação bem-sucedida.
7. **Tratamento de erros:** identificar falhas e evitar confirmações de pedidos não registrados.

### Diagrama simplificado

Google Forms → Google Sheets Trigger → IF (validação do e-mail)

- **Saída verdadeira:** preparar dados → registrar pedido → enviar confirmação por Gmail.
- **Saída falsa:** encerrar o processamento sem enviar e-mail.

A planilha de respostas do formulário pode funcionar como origem dos dados, enquanto outra planilha pode armazenar os pedidos processados.

## 5. Nós sugeridos no n8n

| Nó | Finalidade |
|---|---|
| Google Sheets Trigger | Detectar novas respostas registradas na planilha de entrada. |
| IF | Verificar a validade do e-mail e direcionar o fluxo. |
| Edit Fields (Set) | Organizar os campos e preparar os dados. |
| Google Sheets | Registrar o pedido na planilha de destino. |
| Gmail | Enviar a confirmação ao cliente. |

Os nós e as operações disponíveis dependem da versão do n8n e da configuração das credenciais. O Google Forms deve estar conectado à planilha de respostas, caso seja utilizada essa estratégia de gatilho.

## 6. Regras de negócio

- Pedidos sem e-mail válido não devem avançar para o registro e o envio de confirmação.
- O e-mail de confirmação só deve ser enviado após o registro bem-sucedido.
- O valor total deve ser calculado somente quando houver quantidade e valor unitário válidos.
- Falhas de integração devem ser identificadas para permitir análise e reprocessamento controlado.

## 7. Plano de testes

- **Teste 1:** pedido com e-mail válido — verificar o registro e o envio da confirmação.
- **Teste 2:** pedido sem e-mail — verificar se o processamento é interrompido.
- **Teste 3:** pedido com e-mail em formato inválido — verificar se não ocorre registro nem envio de confirmação.
- **Teste 4:** falha ao gravar na planilha — verificar se o e-mail não é enviado.
- **Teste 5:** quantidade e valor unitário válidos — verificar o cálculo do valor total.

## 8. Resultado esperado

Uma automação simples e organizada para receber pedidos, validar informações, registrar dados comerciais e confirmar o recebimento por e-mail, reduzindo tarefas manuais e aumentando a confiabilidade do processo.

**Status do projeto:** proposta de workflow documentada para implementação e testes no n8n.

