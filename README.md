# 💸 App de Finanças Pessoais: Papo Financeiro - Organize suas finanças conversando
Este projeto foi desenvolvido como um Desafio de Projeto da DIO de Vibe Coding utilizando o Lovable e o Copilot Web. A proposta é criar um aplicativo de organização financeira pessoal baseado em interações em linguagem natural.

---

## 📝 PRD Refinado no Copilot Web

```markdown
# PRD Aplicativo de Organização de Finanças Pessoais por Conversa

### Contexto
Quero criar um aplicativo de **Organização de Finanças Pessoais** que funcione por meio de conversas naturais com o usuário. O objetivo é reduzir a fricção de entrada de dados, aumentar a adesão de iniciantes e oferecer recomendações personalizadas de economia.

### Problema
Muitos usuários desistem de controlar gastos porque apps exigem entrada manual excessiva e pouca personalização. A solução proposta é uma experiência conversacional que permita registrar despesas sem formulários complexos e que entregue recomendações acionáveis conforme o perfil do usuário.

### Público Alvo
- **Primário:** iniciantes que querem começar a organizar finanças de forma prática e sem complicação.  
- **Secundário:** usuários que já usam apps financeiros mas buscam uma interface conversacional e divisão de despesas colaborativa.

### Funcionalidades Chave
1. **Registrar gastos via chat** em linguagem natural com extração de valor, categoria, data e nota.  
2. **Classificação automática** de transações com categorias básicas e possibilidade de ajuste manual.  
3. **Metas financeiras** criadas e acompanhadas via chat ou interface manual.  
4. **Agente Financeiro** que envia dicas personalizadas e sugestões de economia.  
5. **Relatórios simples e personalizados** com resumo mensal e gráficos por categoria.  
6. **Despesas compartilhadas** com divisão percentual customizável entre participantes (exemplo 70% / 30%) e controle de status de pagamento.  
7. **Acessibilidade e Design Universal** aplicados a todas as telas.  
8. **Autenticação e sincronização** entre dispositivos com opção de armazenamento local.

### Entregável da IA
- **Plano de MVP** com telas principais, recursos técnicos, modelo de dados, endpoints API e esboço de validação inicial.  
- **Tom educativo e linguagem simples em PT BR.**  
- **Aplicação dos princípios de Design Universal** para acessibilidade ampla.  
- **Garantia de cobertura de todas as funcionalidades chave.**

---

## Escopo do MVP
**Objetivo:** validar se usuários iniciantes conseguem registrar gastos por chat, obter classificação automática e acompanhar metas com recomendações úteis.

**Incluído**
- Chat conversacional para registro de transações.
- Classificação automática com categorias básicas.
- Criação e acompanhamento de metas.
- Agente Financeiro com dicas periódicas.
- Relatórios simples mensais.
- Despesas compartilhadas com divisão percentual.
- Autenticação básica e sincronização backend.
- Requisitos de acessibilidade WCAG 2.1 AA.

**Fora do MVP**
- Conexão automática com contas bancárias.
- OCR avançado de recibos.
- Integrações financeiras complexas e pagamentos automáticos.

---

## Telas Principais e Prioridade

| **Tela** | **Objetivo** | **Elementos chave** | **Prioridade** |
|---|---|---:|---|
| **Chat Principal** | Registrar transações e interagir com agente | Campo de texto; botões rápidos; histórico | Alta |
| **Registrar Transação Manual** | Entrada alternativa direta | Valor; categoria; data; nota; participantes | Alta |
| **Resumo Financeiro** | Visão mensal com gráficos simples | Gráfico de pizza; total gasto; saldo estimado | Alta |
| **Metas** | Criar e acompanhar metas | Meta; valor alvo; progresso; prazo | Alta |
| **Despesas Compartilhadas** | Gerenciar contas entre usuários | Lista de despesas; divisão percentual; status | Alta |
| **Configurações e Acessibilidade** | Preferências e ajustes de acessibilidade | Perfil; notificações; tema alto contraste | Média |

---

## Recursos Técnicos e Arquitetura
**Frontend**  
- **Stack sugerido:** React Native ou Flutter para iOS e Android.  
- **Componentes:** chat com rich text, botões de ação, formulários acessíveis, suporte a entrada por voz.

**Backend**  
- **Stack sugerido:** Node.js com Express ou Python FastAPI.  
- **Banco de dados:** PostgreSQL; Redis para cache.  
- **Autenticação:** OAuth2 / JWT; biometria no dispositivo.  
- **Armazenamento de arquivos:** S3 compatível para anexos.

**NLP e ML**  
- **NLU:** combinação de regras + modelo treinável para extrair intenções e entidades (valor, categoria, data, participantes).  
- **Classificação:** regras iniciais com modelo ML para melhorar com dados do usuário.  
- **Serviços possíveis:** Rasa self-hosted ou APIs de LLM para conversação.

**Infra e Observabilidade**  
- CI/CD, logs estruturados, Sentry para erros, métricas em Prometheus/Grafana.  
- Notificações via Firebase Cloud Messaging e APNs.

---

## Modelo de Dados Essencial
- **User:** id; nome; email; preferências; acessibilidade.  
- **Transaction:** id; user_id; valor; categoria; data; nota; origem; participants.  
- **SharedExpense:** id; creator_id; total; splits [{user_id, percent}]; status.  
- **Goal:** id; user_id; target_value; current_value; deadline.  
- **ConversationEvent:** id; user_id; message; intent; entities; timestamp.

---

## Endpoints API Sugeridos
- `POST /conversations/message` — enviar mensagem do usuário e receber resposta do agente.  
- `POST /transactions` — criar transação.  
- `GET /transactions` — listar transações com filtros por mês.  
- `POST /shared-expenses` — criar despesa compartilhada.  
- `POST /goals` `GET /goals` — gerenciar metas.  
- `GET /reports/monthly` — gerar resumo mensal.

---

## Acessibilidade e Design Universal
**Princípios aplicados**  
- **Perceptível:** contraste mínimo 4.5:1; texto redimensionável; rótulos claros.  
- **Operável:** navegação por teclado; foco visível; alvos de toque 44x44 dp.  
- **Compreensível:** linguagem simples; feedback claro; confirmações.  
- **Robusto:** compatibilidade com leitores de tela; ARIA labels; testes com NVDA e VoiceOver.

**Detalhes práticos**  
- Não usar cor como único indicador.  
- Oferecer modo alto contraste e ajuste de tamanho de fonte.  
- Checklist WCAG 2.1 AA aplicado a todas as telas.

---

## Plano de Validação Inicial e Métricas
**Objetivos de validação**  
- Usuário registra transação via chat em ≤ 2 minutos.  
- Classificação automática acerta ≥ 80% nas categorias básicas.  
- Engajamento com metas e dicas do agente.

**Fases de validação**  
1. **Teste de protótipo 1 a 2 semanas** com 8 a 12 usuários para tarefas chave.  
2. **Beta fechado 3 a 6 semanas** com 50 a 200 usuários para métricas e A/B testing.  
3. **Lançamento MVP 7 a 12 semanas** com 1.000+ usuários para medir retenção.

**Métricas chave**  
- **Tempo médio** para registrar transação via chat.  
- **Precisão** da classificação automática.  
- **Mensagens por usuário por semana.**  
- **Retenção D7 e D30.**  
- **Conversão de metas** e adoção de despesas compartilhadas.

**Critérios de sucesso do MVP**  
- ≥ 70% dos usuários conseguem registrar transação via chat sem ajuda.  
- Classificação automática ≥ 80% nas categorias principais.  
- Retenção D7 ≥ 25% entre usuários ativos.

---

## Riscos e Mitigação
- **NLU impreciso:** iniciar com regras e fallback para correção manual; coletar exemplos para treinar modelo.  
- **Privacidade de dados:** criptografia em trânsito e repouso; políticas claras; opção de exportar e excluir dados.  
- **Adoção baixa:** onboarding guiado e prompts iniciais que demonstram valor imediato.  
- **Complexidade de divisão desigual:** interface visual para ajustar porcentagens e simular valores antes de confirmar.

---

## Próximos Passos e Entregáveis para Desenvolvimento
- **Design:** protótipos de alta fidelidade das telas e fluxos de chat.  
- **NLP:** definir intents e entidades e criar dataset em PT BR.  
- **Backlog MVP:** priorizar histórias de usuário com critérios de aceitação.  
- **Infra:** configurar auth, DB, API e pipeline CI/CD.  
- **Testes:** plano de usabilidade e acessibilidade.  
- **Métricas:** instrumentar analytics desde o início.

**Entregáveis para gerar código com Lovable**  
- Protótipos Figma das telas principais.  
- Especificação de API com payloads.  
- Dataset de exemplos de mensagens em PT BR.  
- Checklist de acessibilidade WCAG adaptado.  
- Backlog priorizado com histórias de usuário e critérios de aceitação.

```

---

## 💬 Interações com o Lovable

> Crie um App de Finanças Pessoais com base no seguinte PRD (Product Requirements Document): {PRD}

---

## 🎯 Resultado Final

Acesse o protótipo funcional no Lovable:  
**[papofinanceiro.lovable.app](https://papofinanceiro.lovable.app/)**

<img width="550" height="1306" alt="image" src="https://github.com/user-attachments/assets/c7b7f92c-4e9e-4cfb-9460-4efedbe0fe17" />


---

## 🔍 Funcionalidades do App de Organização Financeira

### Funcionalidades do app Papo (resumo)

#### Visão geral
Aplicativo conversacional para **registrar gastos**, **classificar transações**, **criar e acompanhar metas**, **receber dicas financeiras** e **gerenciar despesas compartilhadas**, com foco em simplicidade e acessibilidade.

---

### Funcionalidades principais
- **Chat conversacional**  
  - Registrar transações por texto ou voz; extração de valor, categoria, data e nota.  
  - Ações rápidas via botões (Registrar gasto, Criar meta, Ver dica, Resumo do mês).  
  - Respostas proativas e follow‑ups para confirmar ou corrigir dados.

- **Entrada manual alternativa**  
  - Formulário simples: valor; categoria; data; nota; participantes; preview antes de salvar.  
  - Validações imediatas e opção de edição.

- **Classificação automática de transações**  
  - Regras + modelo ML para mapear texto livre em categorias; correção manual e aprendizado incremental.

- **Metas financeiras**  
  - Criar metas por chat ou UI (nome, valor alvo, prazo, contribuição periódica).  
  - Acompanhamento com percentual, previsão de conclusão e lembretes.

- **Relatórios e Resumo do mês**  
  - Resumo mensal: total gasto, gráficos por categoria, saldo estimado e alertas de orçamento.  
  - Acesso rápido via aba Resumo e botão dedicado.

- **Agente Financeiro e dicas**  
  - Dicas contextuais e periódicas; insights após transações; botão Ver dica para solicitar recomendações.

- **Despesas compartilhadas**  
  - Criar despesa, convidar participantes, definir splits percentuais ou valores fixos (ex.: 70% / 30%).  
  - Status de pagamento (pendente, parcial, pago) e notificações para participantes.

- **Navegação e organização**  
  - Abas principais: Chat, Resumo, Gastos, Metas, Dividir.  
  - Campo de entrada persistente com placeholder orientador e envio rápido.

---

### Fluxos de interação essenciais
- **Registrar gasto via chat**: usuário fala/digita → NLU extrai entidades → agente confirma → transação salva e histórico atualizado.  
- **Criar meta via chat**: usuário descreve meta → agente calcula contribuição e cria meta com previsão.  
- **Criar despesa compartilhada**: definir total → ajustar splits percentuais → enviar convites e acompanhar pagamentos.  
- **Fallback e correção**: quando NLU incerto, agente pede clarificação; sempre oferecer edição manual.

---

## 🧠 Reflexão

### O que funcionou bem?  
O refinamento do PRD previamente feito no Copilot foi bastante detalhado, e a interface do app ficou bastante clean e minimalista, facilitando o uso.

### O que não funcionou como o esperado?  
Os créditos acabaram apenas com a interação inicial, portanto não consegui refinar a aplicação e muitas funcionalidades não foram adicionadas. O app não consegue distinguir uma receita de um gasto, registrando tudo como gasto. Os dados do chat não são repassados para as outras abas, ficando apenas com os dados fake iniciais.

### O que aprendi sobre conversar com IAs?  
A parte de refinamento do PRD com o Copilot funcionou bem, porém a parte principal que seria gerar o app no Lovable não foi nem um pouco satisfatória por conta do limite de créditos gratuitos ser muito baixo.
