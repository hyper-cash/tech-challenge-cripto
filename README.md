# Desafio Técnico: O Cofre do Sistema Financeiro

## Introdução

Olá! Bem-vindo ao desafio técnico.

Este exercício foi projetado para avaliar suas habilidades em desenvolvimento full stack, sua capacidade de resolver problemas complexos e seu conhecimento em arquitetura de sistemas. Não se trata de uma avaliação de conhecimento de memória, mas sim de como você aborda um problema, utiliza ferramentas e comunica suas decisões.

O desafio está dividido em três etapas interconectadas. Boa sorte!

---

## O Desafio

### Etapa 1: O Enigma Criptográfico

Seu primeiro passo é decifrar um enigma para obter informações de configuração críticas. Você tem acesso a duas strings:

* **Arquivo 1:** `VGhlIGtleSB3aWxsIGJlIG9uZSBiZWZvcmUgaXRzIHRpbWUgYW5kIHdpbGwgc3RhbmQgZm9yIGFuZXRuaXR5IGFuZCBzZXJ2ZSBhcyBhIHNvdXJjZSBvZiBpbnRlZ3JhdGlvbi4gQ29udmVuYWRlcyB3aWxsIGJlIGJyb2tlbi4gT3VyIHJldHVybiBpcyB0aGUgZ2lmdCBvZiBjaGFvcy4=`
* **Arquivo 2:** `f867490acb2f567b57e7f7b31b81609162e24536717a6a7c4f1c9c4c1a51a1969a53`

**Instruções:**

Decifre o **Arquivo 1** para encontrar a chave necessária para decifrar o **Arquivo 2**. O resultado da decifração será a **`DATABASE_URL`** e o **`SUPER_SECRET_TOKEN`** necessários para a próxima etapa.

### Etapa 2: Desenvolvimento Full Stack e Deploy

Com os dados decifrados, crie uma aplicação full stack para validar transações.

**Backend**
* Utilize a tecnologia de sua preferência para o back-end em Node.js com TypeScript.
* Configure o banco de dados **PostgreSQL** usando a `DATABASE_URL` obtida na etapa anterior.
* Crie uma API para o endpoint `POST /api/payments`. O endpoint deve receber um objeto de pagamento e um `X-Idempotency-Key` no header da requisição.
* A API deve verificar se a `X-Idempotency-Key` já existe no banco de dados. Se sim, retorne a transação existente com status `409 Conflict`. Caso contrário, salve a nova transação com o status `201 Created`.
* A lógica da API deve ser protegida por uma validação do **`SUPER_SECRET_TOKEN`** (enviado em um header, como `Authorization`).
* Faça o deploy da sua aplicação back-end em um serviço de nuvem (ex: Google Cloud, AWS, Vercel, Railway).

**Frontend (Next.js/React)**
* Construa uma interface em **Next.js** usando **SSR**.
* Crie um formulário com **Tailwind CSS** para que o usuário insira um valor e uma descrição.
* Ao submeter, a aplicação deve enviar uma requisição para a API do back-end, incluindo o `X-Idempotency-Key` e o `Authorization` com o `SUPER_SECRET_TOKEN`.
* Use o **Tanstack Query** para gerenciar o estado e exibir as respostas da API, incluindo mensagens de sucesso, erro e o caso de idempotência.
* Faça o deploy da sua aplicação front-end em um serviço de nuvem.

### Etapa 3: DevOps e Arquitetura

* Forneça um `Dockerfile` para a aplicação backend.
* Crie um arquivo `docker-compose.yml` que orquestre o banco de dados PostgreSQL e o serviço backend, configurando as variáveis de ambiente necessárias.

---

## Instruções de Execução

Seu projeto deve ser configurado para rodar localmente com um único comando:

1.  Clone este repositório.
2.  Preencha as suas respostas nas seções abaixo.
3.  Garanta que o projeto possa ser iniciado com `docker-compose up --build`.

## Entregas

### Processo e Ferramentas

**Descreva o processo que você utilizou para decifrar o enigma e resolver as tarefas. Detalhe a metodologia e as ferramentas utilizadas para chegar à solução.**

### Decisões Arquiteturais

**Explique como a sua solução atual poderia ser escalada para suportar transações de alto volume. Pense em conceitos como filas (queues), processamento assíncrono e sistemas de ledger.**

### Observabilidade

**Descreva como você garantiria a observabilidade (logs, métricas, tracing) deste serviço em um ambiente de produção.**

### Links do Deploy

**Por favor, forneça o link da aplicação front-end em produção:**
