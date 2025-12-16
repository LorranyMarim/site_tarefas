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

## Módulo 1: Autenticação (Login)

### CT-01: Login com Credenciais Válidas
* **Descrição:** Verificar se o usuário consegue logar com username e senha corretos.
* **Pré-condição:** Usuário "admin" cadastrado com senha "123".
* **Passos:**
    1. Acessar a página de login.
    2. No campo Usuário, digitar "admin".
    3. No campo Senha, digitar "123".
    4. Clicar no botão "Entrar".
* **Resultado Esperado:** O sistema deve redirecionar o usuário para a Home Page.

### CT-02: Login com Username Correto e Senha Incorreta/Vazia
* **Descrição:** Verificar a segurança ao inserir senha errada.
* **Pré-condição:** Estar na tela de login.
* **Passos:**
    1. No campo Usuário, digitar "admin".
    2. No campo Senha, digitar uma senha incorreta (ex: "000") OU deixar vazio.
    3. Clicar no botão "Entrar".
* **Resultado Esperado:** O sistema **NÃO** deve logar. Deve exibir uma mensagem de erro ("Usuário ou senha inválidos" ou "Preencha a senha").

### CT-03: Login com Username Incorreto/Vazio e Senha Certa
* **Descrição:** Verificar validação de usuário inexistente.
* **Pré-condição:** Estar na tela de login.
* **Passos:**
    1. No campo Usuário, digitar um nome inexistente (ex: "teste") OU deixar vazio.
    2. No campo Senha, digitar "123".
    3. Clicar no botão "Entrar".
* **Resultado Esperado:** O sistema **NÃO** deve logar. Deve exibir mensagem de erro.

### CT-04: Tentativa de Login com Campos Vazios
* **Descrição:** Verificar validação de campos obrigatórios.
* **Passos:**
    1. Deixar campo Usuário vazio.
    2. Deixar campo Senha vazio.
    3. Clicar em "Entrar".
* **Resultado Esperado:** O sistema deve exibir alertas visuais ou mensagens indicando que os campos são obrigatórios e não realizar o login.

### CT-05: Verificação de Placeholders (Dicas de Campo)
* **Descrição:** Garantir que os campos tenham dicas e não valores pré-preenchidos.
* **Passos:**
    1. Carregar a tela de Login.
    2. Observar os campos "Usuário" e "Senha".
* **Resultado Esperado:** Os campos devem estar vazios, contendo apenas um texto cinza (placeholder) como dica (ex: "Digite seu usuário"), e não valores reais como "admin" ou "123" pré-carregados.

---

## Módulo 2: Cadastro de Usuário

### CT-06: Validação de Regras de Cadastro
* **Descrição:** Verificar todas as validações de input no formulário de cadastro.
* **Passos:**
    1. Acessar tela de Cadastro.
    2. Tentar cadastrar com campo "Nome" tendo menos de 3 caracteres.
    3. Tentar cadastrar com campo "E-mail" sem formato válido (sem @ ou domínio).
    4. Tentar cadastrar com senha menor que 8 dígitos.
    5. Deixar qualquer campo vazio e clicar em "Cadastrar".
    6. Verificar se existe o campo "Confirmar Senha" e se ele valida a igualdade com a senha.
* **Resultado Esperado:** O sistema **NÃO** deve permitir o cadastro. Deve exibir mensagens de erro específicas para cada falha. Deve haver um texto explicativo sobre a complexidade da senha visível.

### CT-07: Fluxo de Cadastro com Sucesso
* **Descrição:** Verificar o fluxo completo de um cadastro válido.
* **Passos:**
    1. Preencher Nome (> 3 letras).
    2. Preencher E-mail válido.
    3. Preencher Username.
    4. Preencher Senha (> 8 dígitos).
    5. Preencher "Confirmar Senha" igual à senha anterior.
    6. Clicar em "Cadastrar".
* **Resultado Esperado:** O sistema deve exibir uma mensagem de sucesso ("Cadastro realizado com sucesso") e redirecionar automaticamente o usuário para a **Tela de Login**.

---

## Módulo 3: Home Page e Criação de Tarefas

### CT-08: Fechamento de Modal via Botão Cancelar
* **Descrição:** Verificar funcionalidade do botão cancelar na criação de tarefa.
* **Passos:**
    1. Na Home, clicar no botão de adição (+).
    2. O modal de criar tarefa abre.
    3. Clicar no botão "Cancelar".
* **Resultado Esperado:** O modal deve ser fechado e nenhuma tarefa deve ser criada.

### CT-09: Fechamento de Modal via Clique Externo
* **Descrição:** Verificar usabilidade ao clicar fora do modal.
* **Passos:**
    1. Abrir o modal de criação de tarefa.
    2. Clicar na área escura/fora do modal (backdrop).
* **Resultado Esperado:** O modal deve se fechar.

### CT-10: Limpeza de Campos do Modal ao Reabrir
* **Descrição:** Garantir que dados não salvos não persistam ao reabrir a janela.
* **Passos:**
    1. Abrir modal de criação.
    2. Digitar "Teste de persistência" no título.
    3. Fechar o modal (cancelar ou clicar fora).
    4. Abrir o modal de criação novamente.
* **Resultado Esperado:** Os campos Título e Descrição devem estar **limpos/vazios**.

### CT-11: Logout do Sistema
* **Descrição:** Verificar funcionalidade de sair.
* **Passos:**
    1. Na Sidebar, clicar na opção "Sair".
* **Resultado Esperado:** O usuário deve ser deslogado e redirecionado para a tela de Login.

---

## Módulo 4: Gerenciamento e Edição de Tarefas

### CT-12: Abertura e Opções do Modal de Edição
* **Descrição:** Verificar se ao clicar na tarefa as opções corretas aparecem.
* **Passos:**
    1. Criar uma tarefa na Home.
    2. Clicar sobre a tarefa criada.
* **Resultado Esperado:** Um modal deve abrir contendo os dados da tarefa preenchidos e os botões: "Cancelar", "Excluir", "Concluir" e "Salvar".

### CT-13: Edição de Tarefa (Salvar)
* **Descrição:** Editar o título ou descrição de uma tarefa existente.
* **Passos:**
    1. Abrir modal da tarefa.
    2. Alterar o texto do título.
    3. Clicar em "Salvar".
* **Resultado Esperado:** O modal fecha e, na lista da Home, a tarefa deve exibir o **novo título** atualizado.

### CT-14: Exclusão de Tarefa com Confirmação
* **Descrição:** Verificar o fluxo de exclusão segura.
* **Passos:**
    1. Abrir modal da tarefa.
    2. Clicar em "Excluir".
    3. Verificar se aparece mensagem de confirmação "Tem certeza?".
    4. Clicar em "Não" (deve voltar ao modal).
    5. Clicar em "Excluir" novamente e depois em "Sim".
* **Resultado Esperado:** O modal fecha e a tarefa **desaparece** da lista na Home.

### CT-15: Conclusão de Tarefa
* **Descrição:** Verificar o comportamento visual e lógico de completar uma tarefa.
* **Passos:**
    1. Abrir modal da tarefa.
    2. Clicar em "Concluir".
* **Resultado Esperado:**
    1. O modal fecha.
    2. Na lista, o título da tarefa deve estar **tachado** (riscado).
    3. Deve aparecer um ícone de **emoji "check" verde** junto à tarefa.
    4. Ao tentar clicar novamente nessa tarefa, **nada deve acontecer** (não abre mais o modal).

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
