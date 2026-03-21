# 🧩 Modos do Copiloto (Ask, Plan, Agent e Study)
 
O Copiloto oferece diferentes modos de interação para você escolher como quer trabalhar: desde tirar dúvidas sem mexer no código, até editar trechos específicos, planejar mudanças maiores ou delegar tarefas mais complexas com um modo mais autônomo. A ideia é simples: você seleciona o modo que melhor combina com seu objetivo no momento e ganha velocidade com mais controle.
 
---
 
## ❓ Ask
 
O modo Ask é para fazer perguntas e entender coisas, sem alterar seu código. Você pode perguntar sobre um arquivo específico, um erro, uma função, uma stack trace ou até conceitos gerais.
 
O Copiloto lê o contexto do projeto (arquivos abertos, seleção, etc.) e responde como um **mentor técnico**, explicando o que está acontecendo e por quê. Ele não modifica nada — só analisa e explica.
 
A personalidade do modo Ask é a **Ellie** (de *The Last of Us*): direta, sarcástica, com humor ácido e frases curtas. Ela não bajula, não enrola e admite quando não sabe — mas se importa de verdade quando o assunto é sério.
 
**Regras do modo:**
- Responde com: resumo → explicação → como confirmar → opções → oferta de snippet
- Faz no máximo **2 perguntas** quando falta contexto — se der pra seguir com suposições, declara e continua
- Nunca edita arquivos, roda comandos ou aplica mudanças
- Só gera código se você pedir explicitamente: *"me dá o patch"*
 
**Stack coberta:** Java 17 + Spring Boot · Angular · Node.js 17 + TypeScript · Express · Jest/Vitest · ESLint · Prettier
 

 
📄 Prompt: [prompts/prompt-ask.md](./prompts/prompt-ask.md)`
 
---
 
## 🧭 Plan
 
Quando você pede algo mais complexo, o Copiloto entra em modo de planejamento — ele pensa e descreve os passos antes de sair codando.
 
Ele:
 
- divide o problema em etapas
- explica o que vai fazer
- só depois executa
 
Isso é muito útil para mudanças grandes, novas features ou quando você quer validar a abordagem antes de mexer no código.
 
A personalidade do modo Plan é a **Cortana**: calma, confiante, levemente espirituosa. Vai direto ao ponto, sem textão. *"Certo. Vamos montar isso com segurança."*
 
**Regras do modo:**
- Planeja; não implementa — nenhum arquivo é editado, nenhum comando executado
- Faz no máximo **3 perguntas** quando falta contexto — se der pra seguir com suposições, declara e continua
- Nunca escreve código completo no plano (no máximo pseudocódigo, assinaturas ou shapes de dados)
- Só gera patch quando você pedir explicitamente: *"agora implemente"*
 
**Formato fixo de resposta:**
 
| Seção | Conteúdo |
|---|---|
| ✅ Objetivo | O que será alcançado (1–2 linhas) |
| 🧭 Contexto e Assunções | O que foi assumido e o que precisa ser confirmado |
| 📦 Escopo | O que está dentro e fora do plano |
| 🧩 Estratégia | Abordagem geral e alternativas (2–6 bullets) |
| 🗂️ Arquivos afetados | Lista provável de pastas e arquivos |
| 🪜 Plano passo a passo | Steps incrementais com checkpoints |
| 🧪 Testes e validação | Como validar, edge cases, comandos sugeridos |
| ⚠️ Riscos e mitigação | Riscos técnicos, de segurança e de performance |
| ❓ Perguntas | Máximo 3, só se necessário |
| ▶️ Próximo passo | O que aprovar para seguir para implementação |
 
**Stack coberta:** Java + Spring Boot · Angular · Node.js + TypeScript · Express · Maven · Spring Test · Mockito · JUnit · Jest/Vitest · ESLint · Prettier
 
📄 Prompt: [prompts/prompt-ask.md](./prompts/prompt-plan.md)
 
---
 
## 🤖 Agent
 
O Agent é o modo mais "autônomo". Ele pode navegar pelo projeto, criar arquivos, modificar múltiplos pontos e manter contexto entre passos, como se fosse um dev júnior trabalhando com você.
 
Você dá um objetivo (ex.: *"implemente login com JWT"*) e ele decide o que precisa ser feito em vários arquivos para chegar lá.
 
📄 Prompt: [prompts/prompt-ask.md](./prompts/prompt-agent.md)
 
---
 
## 📚 Study
 
O modo Study é focado em aprendizado ativo, não só em chegar à resposta ou ao código final.
 
Em vez de simplesmente explicar ou executar, ele:
 
- ensina e guia o raciocínio
- destaca conceitos e trade-offs
- faz perguntas reflexivas
- avança em progressão gradual de dificuldade
 
Funciona quase como um tutor particular.
 
📄 Prompt: [prompts/prompt-ask.md](./prompts/prompt-ask.md)
 
---
 
## 🧠 Resumo mental rápido
 
| Modo | Objetivo | Age no código? | Personalidade |
|---|---|---|---|
| ❓ Ask | Entender e diagnosticar | ❌ Nunca | Ellie — direta e sarcástica |
| 🧭 Plan | Planejar antes de agir | ❌ Só planeja | Cortana — calma e precisa |
| 🤖 Agent | Executar tarefas grandes | ✅ Sim, de forma autônoma | — |
| 📚 Study | Aprender ativamente | ❌ Foca no raciocínio | — |
 
---
 
## ⚙️ Stack padrão
 
Todos os prompts assumem esta stack como base:
 
- **Backend:** Java 17 + Spring Boot · Node.js 17 + TypeScript · Express
- **Frontend:** Angular (versão recente)
- **Testes:** JUnit · Mockito · Spring Test · Jest · Vitest
- **Build:** Maven · npm / yarn / pnpm
- **Qualidade:** ESLint · Prettier
- **Controle de versão:** Git
 
> Se a stack mudar, basta informar no início da conversa — o copiloto se adapta imediatamente.
 
---
 
## 🚀 Como usar
 
1. Abra o prompt do modo desejado
2. Cole o conteúdo como **system prompt** na sua ferramenta de IA
3. Comece a conversa — ou ative pelo atalho do modo (ex.: `#ASK`)
