# Relatório do Código Original

## 1. Identificação do experimento

Este projeto foi desenvolvido como um experimento de geração de código utilizando um modelo de linguagem executado localmente.

O objetivo era avaliar a capacidade do modelo de criar uma aplicação web completa a partir de requisitos relativamente abertos, permitindo que a própria IA escolhesse um diferencial para o produto.

### Modelo utilizado

- **Modelo:** `qwen3.6-27b@q4_k_m`
- **Quantidade de parâmetros:** aproximadamente 27 bilhões
- **Quantização:** Q4_K_M
- **Execução:** modelo local
- **Tipo de projeto:** aplicação web em HTML, CSS e JavaScript
- **Formato inicial:** arquivo único contendo toda a aplicação

---

## 2. Prompt utilizado

> Quero que desenvolva um app de calculadora bem completo e com algum tipo de diferencial do mercado que vc mesmo pode desenvolver.
>
> Eu quero so que no app tenha um menu para mudarmos a identidade visual da calculadora pra, como varias cores diferentes e estilos diferentes de boatões. Quero que de o seu melhor e use o max de inteligência que vc conseguir para me entregar o resultado mais satisfatório

O prompt foi mantido neste relatório conforme foi originalmente enviado ao modelo.

---

## 3. Funcionalidades solicitadas

Os requisitos principais apresentados ao modelo foram:

1. Criar uma calculadora web completa.
2. Implementar operações matemáticas básicas.
3. Escolher e desenvolver algum diferencial em relação a calculadoras convencionais.
4. Criar um menu de personalização visual.
5. Disponibilizar diferentes combinações de cores.
6. Permitir a alteração do estilo dos botões.
7. Criar uma interface visualmente agradável.
8. Utilizar o máximo possível da capacidade do modelo.

---

## 4. Diferenciais escolhidos pelo modelo

Além da personalização solicitada, o modelo tentou implementar diferentes recursos avançados:

- Operações matemáticas básicas.
- Operações científicas.
- Potenciação.
- Raízes quadradas e cúbicas.
- Logaritmos.
- Funções trigonométricas.
- Conversão entre graus e radianos.
- Fatorial.
- Porcentagem.
- Memória da calculadora.
- Histórico de cálculos.
- Entrada pelo teclado.
- Diferentes modos de funcionamento.
- Entrada de expressões em linguagem natural em português.
- Seis temas visuais.
- Cinco estilos diferentes para os botões.
- Persistência das preferências visuais no navegador.

A entrada em linguagem natural foi o principal diferencial escolhido pelo modelo. A proposta era permitir comandos como:

- `quadrado de 15`
- `raiz quadrada de 81`
- `raiz cúbica de 27`
- `fatorial de 5`
- `seno de 90`
- `log natural de 10`
- `dois mais três`
- `2 elevado a 8`

---

## 5. Características positivas da versão original

Apesar dos problemas encontrados posteriormente, o código original apresentou pontos positivos.

### Interface ambiciosa

A aplicação possuía uma interface visualmente elaborada, com:

- visor da calculadora;
- teclado numérico;
- botões científicos;
- painéis secundários;
- menu de personalização;
- seletor de temas;
- seletor de estilos;
- efeitos visuais;
- adaptação parcial para dispositivos móveis.

### Escopo acima de uma calculadora básica

O modelo não se limitou a gerar uma calculadora com quatro operações. Ele tentou desenvolver:

- parser de expressões;
- funções científicas;
- interpretação de frases em português;
- memória;
- histórico;
- personalização visual;
- persistência de configurações.

### Organização visual do código

Embora todo o projeto estivesse concentrado em um único arquivo, havia uma separação perceptível entre:

- estrutura HTML;
- estilos CSS;
- lógica JavaScript;
- definição dos temas;
- definição dos estilos dos botões;
- funções matemáticas;
- controle da interface.

### Funcionamento parcial do motor matemático

Durante a auditoria, algumas partes do motor matemático conseguiram ser testadas isoladamente.

Foram identificados resultados corretos em casos como:

- `2 + 3 * 4`;
- multiplicação implícita;
- porcentagem;
- constante π;
- fatorial em formato pós-fixo, como `5!`.

Entretanto, o funcionamento dessas partes isoladas não significava que a aplicação completa carregava corretamente no navegador.

---

## 6. Problemas encontrados na versão original

A auditoria realizada com o Codex identificou que a aplicação original era visualmente promissora, mas tecnicamente instável.

### 6.1. Erro crítico de sintaxe

Existia um erro de sintaxe no JavaScript, relacionado à função `handleImplicitMult`.

Faltava fechar corretamente uma chamada de `replace`, causando a interrupção do carregamento de todo o script.

Como consequência:

- a calculadora não inicializava;
- os botões não funcionavam;
- os menus não eram configurados;
- os temas não eram carregados;
- a personalização não ficava disponível;
- as operações matemáticas não podiam ser executadas normalmente.

**Gravidade:** crítica.

---

### 6.2. Inicialização incompleta

A função `init()` existia, mas não era chamada de maneira segura após o carregamento da página.

Isso fazia com que partes da interface não fossem configuradas, mesmo que o erro principal de sintaxe fosse corrigido.

A inicialização deveria estar vinculada ao evento:

```javascript
document.addEventListener('DOMContentLoaded', init);
