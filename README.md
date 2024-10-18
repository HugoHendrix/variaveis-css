
# Variáveis CSS: Design Dinâmico e Personalizável

As variáveis CSS, também conhecidas como propriedades personalizadas, permitem que os desenvolvedores definam valores reutilizáveis nas folhas de estilo e os modifiquem dinamicamente. Vamos explorar como funcionam as variáveis CSS com um exemplo prático.

## O que são Variáveis CSS?

As variáveis CSS são valores que você pode definir e reutilizar no seu código. Elas são declaradas com dois hífens (`--`) e, geralmente, são colocadas na pseudoclasse `:root` para que estejam disponíveis em toda a página. Elas podem armazenar valores como cores, tamanhos e fontes, e podem ser usadas em outros arquivos CSS.

**Exemplo:**

```css
:root {
  --main-color: #3498db;
}
```

Aqui, definimos uma variável chamada `--main-color` com o valor `#3498db`, que pode ser usada em qualquer parte do CSS.

## Como Usar Variáveis CSS?

Depois de definidas, você pode usar as variáveis em qualquer lugar do seu código usando a função `var()`.

**Exemplo:**

```css
.element {
  color: var(--main-color);
}
```

Neste exemplo, a cor do texto será definida pela variável `--main-color`. Se você quiser mudar a cor mais tarde, basta alterar o valor da variável, e todos os elementos que a utilizam serão atualizados automaticamente.

## Criando Temas com Variáveis CSS

As variáveis CSS são ótimas para criar sistemas de temas. Veja um exemplo simples:

```css
:root {
  --primary-color: #3498db;
  --secondary-color: #2ecc71;
}

.header {
  background-color: var(--primary-color);
  color: white;
}

.button {
  background-color: var(--secondary-color);
  color: white;
}
```

Aqui, definimos as cores primária e secundária e aplicamos essas cores em diferentes elementos da página.

## Exemplo Prático: Cores Dinâmicas

Vamos criar uma página em que a cor do tema muda dinamicamente quando o usuário clica em um botão.

### HTML

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>CSS Variables</title>
  <link rel="stylesheet" href="styles.css">
</head>
<body>
  <header class="header">
    <h1>Tema Dinâmico - Variáveis CSS</h1>
  </header>
  
  <button id="changeColorBtn">Mudar Cor do Tema</button>

  <script src="script.js"></script>
</body>
</html>
```

### CSS

```css
:root {
  --primary-color: #3498db;
}

.header {
  background-color: var(--primary-color);
  color: white;
  padding: 20px;
  text-align: center;
}

button {
  background-color: var(--primary-color);
  color: white;
  border: none;
  padding: 10px 20px;
  cursor: pointer;
  margin: 20px;
  border-radius: 5px;
}
```

### JavaScript

```javascript
document.getElementById('changeColorBtn').addEventListener('click', function() {
  var randomColor = '#' + Math.floor(Math.random()*16777215).toString(16);
  document.documentElement.style.setProperty('--primary-color', randomColor);
});
```

Neste exemplo, o botão muda a cor do tema quando clicado, gerando uma cor aleatória.

**document.getElementById('changeColorBtn'):**
Este código seleciona o elemento HTML com o ID changeColorBtn. Provavelmente há um elemento de botão HTML no conteúdo com este ID.

**.addEventListener('click', function() { … }):**
Este método adiciona um ouvinte de evento ao elemento de botão selecionado na etapa anterior pelo ID (changeColorBtn). quando o botão é clicado, então executa a função fornecida como o segundo argumento

**var randomColor ='#' + Math.floor(Math.random()*16777215).toString(16);:**
Este código gera um código de cor hexadecimal aleatório. Veja como ele funciona:

**Math.random():**
Esta função gera um número de ponto flutuante aleatório maior ou igual a 0 e menor que 1. É importante observar que Math.random() gera números pseudoaleatórios, o que significa que, embora a ordem dos números que produz pareça aleatória,
Math.floor():

Esta função arredonda para baixo para o inteiro mais próximo. por exemplo
```JS
var number1 = 20.8;
	var number2 = 17;
	var roundedNumber1 = Math.floor(number1); // roundedNumber1 will be 20
	var roundedNumber2 = Math.floor(number2); // roundedNumber2 will be 17

```

Math.floor(number1) arredonda 20,8 para baixo, para 20. Math.floor(number2) retorna 17, pois 17 já é um inteiro.

- * 16777215:
Esta seção garante que o número aleatório gerado esteja dentro do intervalo de valores apropriados para cores hexadecimais. (de #000000 a #FFFFFF).
- .toString(16):
O método toString(16) fornece uma representação hexadecimal do número aleatório gerado. Isso converte o valor RGB em uma string hexadecimal de seis dígitos.
- '#' + …:
Finalmente, o símbolo de hash (#) é concatenado com a sequência de cores hexadecimal, criando um código de cor hexadecimal válido para CSS


**document.documentElement.style.setProperty('–primary-color', randomColor); :**
Esta linha define a cor gerada aleatoriamente como o valor da variável CSS – primary-color. Aqui está o que está acontecendo:

- **document.documentElement:**
Seleciona o elemento raiz do documento HTML, tag <html>.
- **.style.setProperty():**
Este método define uma propriedade CSS no elemento selecionado (ou seja, em nosso exemplo, seu Button). Neste caso, ele está definindo o valor da variável CSS –primary-color.
- **'–primary-color':**
Este é o nome da variável CSS que definimos.
- **randomColor:**
randomColor é normalmente um nome de variável usado para armazenar um valor de cor gerado aleatoriamente. Esse valor geralmente é representado como um código de cor hexadecimal.

### Explorando o Exemplo
Este exemplo mostra uma página da web com um botão e um cabeçalho. A cor de fundo do botão e do cabeçalho são personalizadas usando a variável CSS –primary-color, que tem um valor padrão de #3498db. Um script JavaScript cria um código de cor hexadecimal aleatório ao clicar no botão, que é então atribuído como o novo valor da variável –primary-color. Como resultado, os usuários têm uma experiência interessante e interativa, pois a cor do tema do botão e do cabeçalho muda dinamicamente.

## Vantagens das Variáveis CSS

- **Reutilização e Modificação**: Você pode definir um valor uma vez e usá-lo em vários lugares, facilitando atualizações e manutenção do código.
- **Estilo Dinâmico**: Variáveis podem ser alteradas com JavaScript, criando temas dinâmicos e interativos.
- **Escopo Controlado**: Você pode limitar o uso das variáveis a certos elementos ou seções da página.
- **Cálculo e Interpolação**: É possível realizar operações matemáticas e concatenar valores.
- **Compatibilidade**: Funciona na maioria dos navegadores modernos.

## Conclusão

As variáveis CSS são uma maneira eficiente de criar estilos dinâmicos e gerenciar o design de forma mais simples. Elas facilitam a manutenção do código e oferecem mais controle sobre a aparência dos seus sites. Comece a utilizá-las em seus projetos para ver os benefícios em ação!


