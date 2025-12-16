# Aula: Eventos + funções + conversão numérica (testando e corrigindo bugs no frontend)

## Objetivo da aula
Ao final, o aluno deve conseguir **testar, diagnosticar e corrigir** falhas comuns em páginas web que usam JavaScript para:

- Ler dados do usuário com `getElementById()` e `.value`
- Reagir a ações do usuário com `addEventListener()`
- Organizar lógica com `function`
- Converter e validar números com `Number()`, `parseInt()` e `parseFloat()`
- Identificar problemas via testes e **corrigir no código**

---

## 1) Parte teórica

### 1.1 DOM básico: `getElementById()` + `.value`
- **DOM** = a “árvore” do HTML que o JavaScript acessa.

**Para buscar um elemento:**
```js
const inputEmail = document.getElementById("email");
```

**Para ler o que o usuário digitou em inputs:**
```js
const emailDigitado = inputEmail.value; // sempre vem como TEXTO (string)
```
*Pontos de atenção:*
- .value sempre retorna string, mesmo se o input for type="number".
- Erro comum: fazer conta com string e “somar texto” sem querer.

### 1.2 Eventos: addEventListener()
- O evento é o “gatilho” (clique, submit, digitação, etc.).

*Clique em botão:*
```js
document.getElementById("btnLogin").addEventListener("click", function () {
  // ação
});
```

*Envio de formulário (login/cadastro):*
```js
document.getElementById("formCadastro").addEventListener("submit", function (event) {
  event.preventDefault(); // evita recarregar a página
  // valida e processa
});
```

*Erros comuns em projetos bugados:*
- Não usar event.preventDefault() e a página recarrega antes de validar.
- Listeners colocados em IDs errados.
- Código rodando antes do DOM carregar.

*Dica prática:*
- Coloque o <script> no final do <body> ou use:
```js
document.addEventListener("DOMContentLoaded", function () {
  // agora pode buscar elementos
});
```

### 1.3 function: organizando lógica
- Funções evitam repetição e deixam o teste/depuração mais fácil.

*Exemplo:*
```js
function validarEmail(email) {
  return email.includes("@") && email.includes(".");
}
```

*Boas práticas para a aula:*
- Funções pequenas, com um objetivo.
- Nomes claros: validarSenha, calcularTotal, mostrarErro.

### 1.4 Convertendo números: Number(), parseInt(), parseFloat()
- Como .value vem string, converter é obrigatório em cálculos e comparações numéricas.

- *Number()*: Converte para número (inteiro ou decimal).
```js
const idade = Number(document.getElementById("idade").value);
```
- Se o texto não for numérico → vira NaN.

- *parseInt()*: Converte para inteiro (corta casas decimais).
```js
const quantidade = parseInt("12.9", 10); // 12
```
*Boas práticas:*
- Usar sempre base 10: parseInt(valor, 10).

- *parseFloat()*: Converte para decimal.
```js
const preco = parseFloat("19.90"); // 19.9
```

- *NaN (Not a Number)*: o “alerta vermelho”
```js
if (Number.isNaN(preco)) {
  // valor inválido
}
```
*Erros comuns (ótimos para um site bugado):*
- Comparar string com número: "10" > 2 (funciona “às vezes”, mas é armadilha)
- Somar strings: "10" + "2" = "102"
- Aceitar campo vazio e gerar NaN sem tratar
- Vírgula decimal no Brasil: "19,90" → parseFloat vira 19 (ou NaN dependendo do caso)

*Dica para PT-BR (quando quiser tratar vírgula):*
```js
const texto = input.value.replace(",", ".");
const valor = Number(texto);
```

### 1.5 Mini-padrão de validação (modelo que os alunos vão aplicar)
```js
function lerNumero(id) {
  const texto = document.getElementById(id).value.trim().replace(",", ".");
  const n = Number(texto);
  return n;
}

function mostrarErro(idMsg, msg) {
  document.getElementById(idMsg).innerText = msg;
}

document.getElementById("form").addEventListener("submit", function (event) {
  event.preventDefault();

  const idade = lerNumero("idade");

  if (Number.isNaN(idade) || idade <= 0) {
    mostrarErro("msg", "Idade inválida.");
    return;
  }

  mostrarErro("msg", "OK!");
});
```
