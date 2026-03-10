DESAFIO QA BEEDOO 2026 – MARCOS NOEL

Sobre o desafio

Esse repositório reúne minha resolução do desafio técnico pra vaga de Analista de Qualidade de Software Júnior na Beedoo.  
O objetivo foi testar uma aplicação simples de cadastro e listagem de cursos, documentar os resultados e responder algumas perguntas sobre o processo.

A ideia aqui não foi só sair clicando, mas sim pensar como um QA: explorar com calma, criar cenários relevantes e registrar os bugs com clareza.

---

Objetivo da aplicação

A aplicação é uma plataforma pra cadastrar cursos.  
Você preenche os dados (nome, descrição, instrutor, datas, etc.), escolhe se é presencial ou online, e o curso aparece numa lista pública.
Parece simples, mas por trás disso tem fluxos importantes que precisam funcionar, e alguns não funcionam tão bem quanto deveriam.

---

Principais fluxos testados

- Cadastrar curso com dados válidos (presencial e online)
- Cadastrar curso com campos em branco
- Cadastrar curso com caracteres especiais
- Inserir valores extremamente longos em cada campo (nome, descrição, instrutor, endereço)
- Testar datas absurdas (muito antiga, muito futura, término antes do início)
- Testar número de vagas negativo
- Tentar acessar os detalhes de um curso recém-criado
- Tentar editar ou excluir um curso

---

Pontos mais críticos que identifiquei

- **Nenhum campo é obrigatório** — você consegue criar um curso completamente em branco
- **Campos de texto livre não têm limite de caracteres**, o que causa quebra de layout na lista
- **O card do curso não é clicável** — não dá pra acessar os detalhes
- **Não tem edição** (funcionalidade esperada)
- **Exclusão não funciona de verdade** — aparece um pop-up falando que foi excluído, mas o curso continua lá
- **Datas inválidas são aceitas** (ano 1, ano 275760, término antes do início)
- **Campo de vagas aceita valor negativo**

---

Casos de teste

Os casos de teste completos, com passos, resultados e evidências, estão na planilha abaixo:

[Planilha de Casos de Teste]((https://docs.google.com/spreadsheets/d/17PAGct91xAuVrecO4Xx6F3tMr_O9gAwoCh2v7j1Q7kk/edit?usp=sharing))

---

Exemplos de casos em Gherkin

Cenário: Cadastrar curso com data de término anterior à data de início
  Dado que estou na página de cadastro de cursos
  Quando informo uma data de início válida
  E informo uma data de término que é anterior à data de início
  E clico em "Cadastrar Curso"
  Então o sistema deve exibir uma mensagem de erro
  E não deve permitir o cadastro

Cenário: Tentar acessar detalhes de um curso recém-criado
  Dado que um curso foi cadastrado com sucesso
  E estou na página de listagem de cursos
  Quando passo o mouse sobre o card do curso
  E clico no card
  Então o cursor muda para o ícone de proibido (🚫)
  E o card não responde ao clique

---

Bugs encontrados

Todos os bugs identificados estão documentados na aba "Bugs Beedoo (BB)" da planilha, com:
- Título do problema
- Passos pra reproduzir
- Resultado esperado vs atual
- Severidade
- Link da evidência

---

 Evidências
As imagens e gravações dos testes estão disponíveis na pasta abaixo:

[Evidências Desafio Beedoo - Marcos Noel da Silva](https://drive.google.com/drive/folders/1wZlabRiha9eyrWOx7u_WkvK9uu4D1yG9?usp=sharing)

---

Ferramentas que usei

- Navegador (Chrome)
- Google Sheets pra documentar os testes
- Printscreen e gravação de tela pras evidências
- GitHub pra versionar o material
