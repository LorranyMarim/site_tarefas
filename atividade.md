# Atividade Prática — Teste e Refatoração do Site **Minhas Tarefas Digital**

## Contexto
Você recebeu um arquivo **HTML único** chamado **Minhas Tarefas Digital** contendo telas de **Login**, **Cadastro** e **Home** (tarefas).  
O site foi entregue **com bugs intencionais** e inconsistências de usabilidade.

Sua missão será atuar como **testador(a) de frontend** e, em seguida, como **dev** para corrigir os problemas.

---

## Objetivo da Atividade
1. **Executar os casos de teste (CT-01 a CT-15)** exatamente como descritos.
2. Identificar e registrar **todas as falhas** (com evidências).
3. **Refatorar o código** para que o site passe nos testes e se comporte conforme os resultados esperados.
4. Personalizar a aplicação (nome, cores e, opcionalmente, layout).
5. Entregar tudo em repositórios conforme solicitado.

---

## Sistema sob Teste (SUT)
- **Aplicação:** Minhas Tarefas Digital  
- **Tecnologias:** HTML + CSS (Bootstrap 5) + JavaScript (DOM)  
- **Telas/Módulos:**
  - Módulo 1: Autenticação (Login)
  - Módulo 2: Cadastro de Usuário
  - Módulo 3: Home Page e Criação de Tarefas
  - Módulo 4: Gerenciamento e Edição de Tarefas

---

## Escopo de Testes
Os testes desta atividade validam:
- Fluxos corretos de **login, cadastro e logout**
- Validações de campos obrigatórios e regras de cadastro
- Usabilidade do modal de criação de tarefas (cancelar, fechar, limpar campos)
- Comportamentos esperados na edição, exclusão e conclusão de tarefas

---

## Casos de Teste que Devem Ser Executados
Execute e registre evidências para **todos** os casos abaixo:

### Módulo 1 — Autenticação (Login)
- **CT-01:** Login com credenciais válidas  
- **CT-02:** Login com username correto e senha incorreta/vazia  
- **CT-03:** Login com username incorreto/vazio e senha certa  
- **CT-04:** Tentativa de login com campos vazios  
- **CT-05:** Verificação de placeholders (dicas de campo)

### Módulo 2 — Cadastro de Usuário
- **CT-06:** Validação de regras de cadastro  
- **CT-07:** Fluxo de cadastro com sucesso

### Módulo 3 — Home Page e Criação de Tarefas
- **CT-08:** Fechamento de modal via botão Cancelar  
- **CT-09:** Fechamento de modal via clique externo  
- **CT-10:** Limpeza de campos do modal ao reabrir  
- **CT-11:** Logout do sistema

### Módulo 4 — Gerenciamento e Edição de Tarefas
- **CT-12:** Abertura e opções do modal de edição  
- **CT-13:** Edição de tarefa (Salvar)  
- **CT-14:** Exclusão de tarefa com confirmação  
- **CT-15:** Conclusão de tarefa (efeito visual + bloqueio de clique)

> Observação: se algum caso de teste **não existir** na interface atual (ex.: “Confirmar senha”, “Editar tarefa”), isso deve ser registrado como **falha** e depois implementado na refatoração.

---

## Regras para Registro das Evidências
Para cada caso de teste, você deve registrar:
- **ID do caso de teste** (ex.: CT-02)
- **Passos executados**
- **Resultado esperado**
- **Resultado obtido**
- **Status:** Passou / Não passou
- **Evidência:** print(s) da tela e/ou erro no console (F12) quando aplicável

As evidências devem aparecer no seu PDF final.

---

## Fase 1 — Execução de Testes (Sem Alterar o Código)
1. Abra o arquivo do site no navegador.
2. Execute **CT-01 a CT-15**.
3. Gere o relatório com os resultados e evidências **antes de corrigir** qualquer bug.

---

## Fase 2 — Refatoração e Correções
Após concluir os testes:
1. Corrija o código para que o site **atenda aos resultados esperados** dos CTs.
2. Ajuste validações e fluxos de navegação conforme as descrições.
3. Implemente funcionalidades ausentes necessárias para cumprir os CTs (quando aplicável).
4. Reteste os casos para confirmar que os bugs foram resolvidos.

---

## Personalização Obrigatória
Na versão refatorada, você deve:
- Alterar o **nome do site** (título e/ou marca visível)
- Personalizar **cores do tema** (ex.: variáveis CSS, Bootstrap, etc.)

Personalização opcional:
- Ajustes de layout (sidebar, cards, espaçamentos, tipografia)
- Melhorias de usabilidade (mensagens, feedback visual, mensagens inline)

---

## Entrega em Repositórios (Obrigatório)
Você fará **DOIS repositórios** no GitHub:

### Repositório 1 — Relatório de Testes
Deve conter:
- `relatorio_de_teste_e_evidencias.pdf`

> Este repositório deve representar a fase de QA: o que passou, o que falhou e as evidências.

### Repositório 2 — Versão Refatorada
Deve conter:
- `home_refatorada.html`
- (opcional) pasta de assets se você separar CSS/JS, mas o arquivo solicitado deve existir com esse nome

> Este repositório deve representar a solução final: código corrigido + personalização.

---

## Critérios de Avaliação
- Execução completa dos CTs (CT-01 a CT-15)
- Qualidade do relatório (clareza, organização, evidências)
- Correções funcionando conforme resultados esperados
- Organização do código (refatoração, legibilidade)
- Personalização aplicada corretamente
- Repositórios entregues com os arquivos e nomes exigidos

---

## Checklist Final antes de Enviar
- [ ] Executei todos os CTs e registrei resultados
- [ ] O PDF contém evidências (prints) e status (passou/não passou)
- [ ] Corrigi os bugs para atender aos resultados esperados
- [ ] Personalizei nome e cores do site
- [ ] Criei os dois repositórios
- [ ] Enviei `relatorio_de_teste_e_evidencias.pdf` no repo 1
- [ ] Enviei `home_refatorada.html` no repo 2
