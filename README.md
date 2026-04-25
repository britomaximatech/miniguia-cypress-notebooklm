# 🌲 Miniguia de Estudos sobre Cypress

> Caderno Temático construído com curadoria de fontes e engenharia de prompts no **NotebookLM** — Desafio de Projeto DIO

[![Cypress](https://img.shields.io/badge/Cypress-17202C?style=for-the-badge&logo=cypress&logoColor=white)](https://www.cypress.io/)
[![NotebookLM](https://img.shields.io/badge/NotebookLM-4285F4?style=for-the-badge&logo=google&logoColor=white)](https://notebooklm.google.com/)
[![DIO](https://img.shields.io/badge/DIO-Bootcamp-blueviolet?style=for-the-badge)](https://www.dio.me/)

---

## 📌 Contexto e Objetivos

### Sobre o Assunto Escolhido

O **Cypress** é um framework de testes end-to-end (E2E) de próxima geração, construído para a web moderna. Diferente de ferramentas tradicionais como Selenium, ele roda **dentro do navegador**, no mesmo loop de execução da aplicação, proporcionando testes mais rápidos, estáveis e confiáveis.

Escolhi o Cypress como tema deste caderno temático porque é a principal ferramenta utilizada no meu dia a dia como **QA (Quality Assurance)**, e aprofundar o conhecimento nela é essencial para melhorar a qualidade da automação de testes em projetos reais.

### Objetivos de Estudo

- 🎯 **Compreender a arquitetura** do Cypress e por que ela elimina problemas de flakiness comuns em ferramentas tradicionais
- 🎯 **Dominar as boas práticas** oficiais de seleção de elementos, organização de testes e controle de estado
- 🎯 **Aprender padrões avançados** como interceptação de rede, `cy.session()`, e testes de componentes
- 🎯 **Aplicar o conhecimento** em cenários reais de automação E2E em projetos corporativos
- 🎯 **Construir um material de referência** rápida para consulta no dia a dia profissional

---

## 📚 Curadoria de Fontes

As fontes abaixo foram selecionadas criteriosamente e carregadas no **NotebookLM** para construir este caderno temático. Priorizei fontes oficiais, abertas e de alta qualidade técnica:

| # | Fonte | Tipo | Descrição |
|---|-------|------|-----------|
| 1 | [📄 Why Cypress? — Documentação Oficial](https://docs.cypress.io/guides/overview/why-cypress) | Documentação Web | Página oficial explicando a arquitetura, diferenciais e funcionalidades do Cypress. Cobre desde o conceito até os produtos (Cypress App, Cloud, Accessibility) |
| 2 | [📄 Best Practices — Documentação Oficial](https://docs.cypress.io/guides/references/best-practices) | Documentação Web | Guia oficial de boas práticas cobrindo seleção de elementos com `data-*`, organização de testes, login programático e controle de estado |
| 3 | [📂 Cypress Docs PT-BR — Tradução Comunitária](https://github.com/pedrohyvo/cypress-docs-pt-br) | Repositório GitHub | Tradução da documentação oficial do Cypress para Português-BR mantida pela comunidade. Facilita o estudo em língua nativa |
| 4 | [📄 Cypress Real World App (RWA)](https://github.com/cypress-io/cypress-realworld-app) | Repositório GitHub | Aplicação full-stack de exemplo (estilo Venmo) mantida pelo time do Cypress para demonstrar testes em cenários reais com autenticação, transações e CI/CD |
| 5 | [📄 Real World Testing with Cypress](https://learn.cypress.io) | Curso/Currículo | Currículo oficial e gratuito da Cypress.io com módulos sobre fundamentos, padrões avançados e testes do mundo real |

> 🔗 **Notebook NotebookLM:** [Acessar caderno temático](https://notebooklm.google.com/notebook/7a05ec99-4067-442e-94e3-0e5bffb0ea32)

### Critérios de Seleção das Fontes

- ✅ **Oficialidade**: Prioridade para documentação mantida pelo time do Cypress
- ✅ **Atualidade**: Fontes atualizadas com a versão mais recente do framework
- ✅ **Acessibilidade**: Todas as fontes são gratuitas e abertas
- ✅ **Profundidade**: Combinação de teoria (docs) com prática (RWA + curso)
- ✅ **Diversidade**: Textos em inglês e português para acessibilidade linguística

---

## 🧪 Engenharia de Prompts e "Cicatrizes"

### Prompts Estratégicos Testados

Abaixo estão as perguntas que elaborei no NotebookLM, as variações testadas e os resultados obtidos.

---

#### 🔬 Prompt 1 — Entendendo a Arquitetura

**Prompt inicial:**
> *"Explique a arquitetura do Cypress"*

**Problema encontrado:** A resposta foi genérica e superficial, sem referências às fontes carregadas.

**Prompt refinado (v2):**
> *"Com base nas fontes fornecidas, explique como a arquitetura do Cypress difere do Selenium e por que isso impacta a estabilidade dos testes. Cite exemplos específicos das fontes."*

**Resultado:** Resposta muito mais detalhada, com citações das fontes e comparação direta:

> *"Diferente do Selenium que opera fora do navegador executando comandos remotos pela rede, o Cypress é executado dentro do mesmo run loop da aplicação. Isso significa que ele tem acesso nativo a todos os objetos: window, document, DOM, timers e service workers. Essa arquitetura permite que o Cypress saiba exatamente quando a página carregou, quando um elemento ficou visível e quando uma animação terminou."*
> — Referência: Why Cypress? (docs.cypress.io)

**🩹 Cicatriz:** Prompts vagos geram respostas genéricas. Sempre incluir "com base nas fontes" e pedir citações específicas.

---

#### 🔬 Prompt 2 — Boas Práticas de Seletores

**Prompt inicial:**
> *"Quais são as melhores práticas para selecionar elementos no Cypress?"*

**Prompt refinado (v2):**
> *"Segundo o guia de Best Practices do Cypress, qual a hierarquia recomendada de seletores? Compare o uso de `data-cy`, `cy.contains()` e seletores CSS tradicionais. Quando usar cada um?"*

**Resultado:** O NotebookLM organizou uma tabela comparativa excelente:

> | Seletor | Recomendado? | Por quê? |
> |---------|:---:|----------|
> | `cy.get('button')` | ❌ | Muito genérico, sujeito a mudanças |
> | `cy.get('.btn-large')` | ❌ | Acoplado ao CSS, muda com redesign |
> | `cy.get('#main')` | ❌ | IDs dinâmicos quebram os testes |
> | `cy.get('[data-cy="submit"]')` | ✅ | Isolado de CSS/JS, feito para testes |
> | `cy.contains('Submit')` | ⚠️ | Usar quando o texto é crítico para o teste |
>
> — Referência: Best Practices (docs.cypress.io)

**🩹 Cicatriz:** Pedir comparações lado-a-lado e tabelas faz o NotebookLM organizar melhor a informação.

---

#### 🔬 Prompt 3 — Waits e Flakiness

**Prompt inicial:**
> *"Como evitar testes flaky no Cypress?"*

**Prompt refinado (v2):**
> *"Por que o Cypress não precisa de `cy.wait()` com tempos fixos? Explique o mecanismo de automatic waiting e retry-ability com base na documentação oficial. Dê exemplos de código comparando a abordagem errada vs. a correta."*

**Resultado:**

> O Cypress possui **automatic waiting** integrado: ele automaticamente espera por comandos e assertions antes de prosseguir. Quando você usa `cy.get()`, o Cypress automaticamente aguarda até o `defaultCommandTimeout` (4s por padrão) pelo elemento aparecer no DOM.
>
> ```javascript
> // ❌ ERRADO — wait fixo frágil
> cy.get('#btn-salvar').click()
> cy.wait(5000)
> cy.get('.toast-sucesso')
>
> // ✅ CORRETO — assertion reativa
> cy.get('#btn-salvar').click()
> cy.get('.toast-sucesso', { timeout: 10000 })
>   .should('be.visible')
>   .and('contain', 'Salvo com sucesso')
> ```
>
> — Referência: Why Cypress? / Best Practices

**🩹 Cicatriz:** Pedir "exemplos de código comparando errado vs. correto" é extremamente eficaz para extrair conteúdo prático e acionável da IA.

---

#### 🔬 Prompt 4 — Padrão Real World App

**Prompt inicial:**
> *"O que é o Real World App?"*

**Prompt refinado (v2):**
> *"Analise o Cypress Real World App (RWA) como referência de projeto profissional. Quais padrões de organização, custom commands e estratégias de CI/CD ele utiliza? O que posso aprender dele para aplicar nos meus projetos?"*

**Resultado:** O NotebookLM extraiu padrões práticos valiosos:

> **Custom Commands reutilizáveis:**
> ```javascript
> // getBySel — seleciona por data-test
> Cypress.Commands.add('getBySel', (selector, ...args) => {
>   return cy.get(`[data-test=${selector}]`, ...args)
> })
>
> // getBySelLike — seleciona por data-test parcial
> Cypress.Commands.add('getBySelLike', (selector, ...args) => {
>   return cy.get(`[data-test*=${selector}]`, ...args)
> })
> ```
>
> **Padrões organizacionais:**
> - Autenticação programática via API (sem UI)
> - Database seeding para estado limpo entre testes
> - Interceptação de rede para controle de respostas
> - Execução paralela com Cypress Cloud
>
> — Referência: Real World App (github.com/cypress-io)

**🩹 Cicatriz:** Ao analisar repositórios como fonte, pedir "padrões" e "o que posso aplicar" gera respostas mais práticas do que pedir "o que é".

---

#### 🔬 Prompt 5 — Resumo Consolidado

**Prompt:**
> *"Crie um resumo consolidado de todos os conceitos-chave sobre Cypress abordados nas fontes. Organize por categorias: Arquitetura, Boas Práticas, Comandos Essenciais e Integração CI/CD. Use bullet points concisos e cite as fontes."*

**Resultado:** Gerou a base do Miniguia de Estudo abaixo ⬇️

---

### Lições Aprendidas (Troubleshooting)

| Problema | Solução |
|----------|---------|
| Respostas genéricas sem citar fontes | Sempre incluir *"com base nas fontes"* no prompt |
| Respostas muito longas e desorganizadas | Pedir formato específico: tabela, bullet points, código |
| IA misturando informação de fontes diferentes | Especificar *qual* fonte analisar no prompt |
| Respostas sem exemplos práticos | Pedir *"compare errado vs. correto com código"* |
| Conteúdo superficial | Usar verbos específicos: *"analise"*, *"compare"*, *"diferencie"* em vez de *"explique"* |

---

## 📖 Miniguia de Estudo — Entrega Final

### 1. Resumos Estruturados

#### 🏗️ Arquitetura do Cypress

- O Cypress roda **dentro do navegador**, no mesmo run loop da aplicação
- Não usa Selenium ou WebDriver — comunica-se via um processo Node.js local
- Tem **acesso nativo** a todos os objetos: `window`, `document`, DOM, funções, timers
- Controla todo o processo de automação de cima a baixo, resultando em testes consistentes
- Suporta Chrome, Firefox, Edge e Electron

#### ✅ Boas Práticas Essenciais

- **Seletores**: Usar `data-cy` ou `data-test` em vez de classes CSS, IDs ou tags
- **Login**: Autenticar programaticamente via API (`cy.request()`) ou usar `cy.session()` para cachear sessões
- **Testes isolados**: Cada teste deve ser independente — não depender de estado de testes anteriores
- **Sem `cy.wait()` fixo**: Usar assertions (`should`) e intercepts (`cy.intercept()`) em vez de esperas hardcoded
- **Estado controlado**: Usar `beforeEach` para definir estado limpo, nunca `afterEach` para limpar

#### 🧩 Tipos de Testes Suportados

| Tipo | Descrição | Exemplo |
|------|-----------|---------|
| **E2E** | Testa fluxos completos no navegador como um usuário real | Login → Comprar → Checkout |
| **Componente** | Testa componentes UI isolados (React, Angular, Vue, Svelte) | Renderizar botão e validar texto |
| **API** | Testa endpoints HTTP diretamente | `cy.request('POST', '/api/users')` |
| **Acessibilidade** | Verifica acessibilidade com Cypress Accessibility | Validar `alt` em imagens, roles ARIA |

#### 🚀 Funcionalidades Principais

- **Time Travel**: Snapshots de cada passo para voltar no tempo e ver o que aconteceu
- **Automatic Waiting**: Espera automaticamente por elementos, animações e transições
- **Debuggability**: Erros descritivos + integração com DevTools do navegador
- **Network Control**: Intercepta e simula chamadas de rede com `cy.intercept()`
- **Spies & Stubs**: Controla comportamento de funções, respostas do servidor e timers
- **Retries**: Retry automático de testes falhos configurável por ambiente
- **Screenshots & Videos**: Captura automática de evidências em caso de falha

#### 🔄 Integração CI/CD

- Suporte nativo a GitHub Actions, GitLab CI, CircleCI, AWS CodeBuild e Bitbucket Pipelines
- **Cypress Cloud**: Gravação de execuções, paralelismo, detecção de flaky tests
- **Test Replay**: Reproduz exatamente o que aconteceu durante a execução
- **Smart Orchestration**: Priorização de specs, cancelamento automático e paralelização

---

### 2. Glossário de Conceitos-Chave

| Termo | Definição |
|-------|-----------|
| **E2E (End-to-End)** | Tipo de teste que simula o fluxo completo do usuário, do início ao fim, em um navegador real |
| **Spec File** | Arquivo de teste do Cypress (`.cy.js`/`.cy.ts`) que contém os casos de teste (`describe` + `it`) |
| **Command** | Método encadeado do Cypress (`cy.get()`, `cy.click()`, `cy.type()`) que executa ações no navegador |
| **Assertion** | Verificação de que o estado da aplicação é o esperado (`.should('be.visible')`, `.should('have.text', ...)`) |
| **Selector** | String usada para localizar elementos no DOM. Recomenda-se usar `data-cy` ou `data-test` |
| **Automatic Waiting** | Mecanismo do Cypress que aguarda automaticamente por elementos e assertions antes de prosseguir |
| **Retry-ability** | Capacidade do Cypress de retentar assertions que falharam até o timeout ser atingido |
| **cy.intercept()** | Comando para interceptar, espiar ou simular (stub) requisições de rede HTTP |
| **cy.session()** | Comando que cacheia o estado da sessão (cookies, localStorage) para reutilizar entre testes |
| **cy.request()** | Comando para fazer requisições HTTP diretamente, sem passar pela UI (útil para setup/login) |
| **Custom Command** | Comando personalizado registrado via `Cypress.Commands.add()` para reutilização em testes |
| **Fixture** | Arquivo de dados estáticos (JSON) armazenado em `cypress/fixtures/` para uso nos testes |
| **Plugin** | Extensão que roda no processo Node.js do Cypress para adicionar funcionalidades extras |
| **Test Isolation** | Princípio de que cada teste deve rodar de forma independente sem depender de outros testes |
| **Flaky Test** | Teste instável que ora passa, ora falha sem alteração de código — geralmente por timing ou estado |
| **data-cy / data-test** | Atributos HTML customizados adicionados exclusivamente para uso em seletores de teste |
| **beforeEach** | Hook que roda antes de cada teste dentro de um bloco `describe` — ideal para setup |
| **Cypress Cloud** | Serviço pago para gravar execuções, analisar resultados e gerenciar suítes de teste |
| **Test Replay** | Funcionalidade do Cypress Cloud que reproduz a execução exata de um teste para debug |
| **Stub** | Substitui uma função ou resposta de rede por uma versão controlada durante o teste |

---

### 3. Prompts Reutilizáveis para Revisão

Use estes prompts no NotebookLM (ou qualquer IA) para revisar e aprofundar estudos sobre Cypress:

#### 📋 Revisão Rápida
```
"Resuma em 5 bullet points os principais diferenciais do Cypress em relação ao Selenium,
com base na documentação oficial."
```

#### 📋 Seletores e Boas Práticas
```
"Crie uma tabela comparando os tipos de seletores no Cypress (tag, class, id, data-cy, 
cy.contains). Para cada um, indique: exemplo de código, nível de fragilidade (alto/médio/baixo)
e quando usar."
```

#### 📋 Debugging e Troubleshooting
```
"Liste os 5 erros mais comuns ao escrever testes Cypress e como corrigir cada um. 
Inclua exemplos de código mostrando o antes (errado) e depois (correto)."
```

#### 📋 Padrões Avançados
```
"Explique como usar cy.intercept() para testar cenários de erro de API (500, 404, timeout).
Dê 3 exemplos práticos com código."
```

#### 📋 Organização de Projeto
```
"Com base no Real World App do Cypress, qual a estrutura de pastas recomendada para
um projeto de automação E2E? Descreva o papel de cada diretório."
```

#### 📋 CI/CD
```
"Como configurar o Cypress para rodar em uma pipeline CI/CD com GitHub Actions?
Inclua o arquivo YAML completo com etapas de instalação, execução e artefatos."
```

#### 📋 Performance
```
"Quais são as técnicas para reduzir o tempo de execução de uma suíte Cypress com
mais de 50 testes? Compare cy.session(), paralelização e Smart Orchestration."
```

---

## 🛠️ Como Utilizar Este Material

1. **Clone o repositório** para ter acesso offline:
   ```bash
   git clone https://github.com/britomaximatech/miniguia-cypress-notebooklm.git
   ```

2. **Acesse o NotebookLM** para interagir com as fontes:
   [🔗 Abrir Caderno Temático](https://notebooklm.google.com/notebook/7a05ec99-4067-442e-94e3-0e5bffb0ea32)

3. **Use os prompts reutilizáveis** acima para revisar conceitos sempre que necessário

4. **Aplique nos seus projetos** seguindo as boas práticas documentadas aqui

---

## 📊 Estrutura do Repositório

```
miniguia-cypress-notebooklm/
├── README.md          # 📖 Este documento — Miniguia completo
├── LICENSE            # 📜 Licença do projeto
└── .git/              # 🗂️ Controle de versão
```

---

## 👨‍💻 Autor

**Lucas Brito**
- GitHub: [@britomaximatech](https://github.com/britomaximatech)
- Projeto desenvolvido como parte do Desafio de Projeto da **DIO**

---

## 📝 Licença

Este projeto está sob a licença MIT. Consulte o arquivo [LICENSE](./LICENSE) para mais detalhes.

---

> 💡 *"O mercado valoriza profissionais que mostram o raciocínio por trás dos resultados."* — DIO
