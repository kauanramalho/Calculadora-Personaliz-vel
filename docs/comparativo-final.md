# Comparativo Final: Código Original x Versão Aprimorada

## 1. Contexto

O protótipo inicial desta calculadora foi gerado pelo modelo local:

```text
qwen3.6-27b@q4_k_m
```

Depois, o projeto foi analisado, testado e aprimorado com auxílio do Codex.

Este documento compara a situação inicial da aplicação com o resultado obtido após a auditoria e a implementação das correções.

> **Observação:** a versão original não estava salva separadamente em um histórico Git no momento da auditoria. Por isso, este comparativo foi elaborado com base no diagnóstico registrado antes das mudanças e nos testes realizados depois delas, e não a partir de um `git diff` completo linha por linha.

---

## 2. Comparação técnica

| Área | Código original | Versão aprimorada | Resultado |
|---|---|---|---|
| Inicialização | Havia erro de sintaxe, funções ausentes e `init()` não era executada corretamente | Estrutura corrigida e inicialização vinculada ao `DOMContentLoaded` | A calculadora carrega completamente |
| Operações básicas | Algumas rotinas funcionavam isoladamente, mas a interface não conseguia utilizá-las de forma confiável | Soma, subtração, multiplicação, divisão, negativos, decimais e precedência foram validados | Funcionando |
| Potenciação | O retorno de `evaluateExpression()` era usado incorretamente | Potências foram integradas ao novo parser | Funcionando |
| Trigonometria | Dependia de substituições textuais frágeis e sujeitas a loops | `sin`, `cos`, `tan` e funções inversas passaram a ser processadas pelo parser | Funcionando |
| Conversão DEG/RAD | Comportamento instável | Conversão implementada diretamente nas funções trigonométricas | Funcionando |
| Fatorial | O botão dependia de uma função ausente ou incompleta | Operador `!` e função `fact()` implementados com validação | Funcionando |
| Raízes | Transformações textuais pouco confiáveis | `sqrt`, raiz cúbica e símbolo de raiz receberam tratamento próprio | Funcionando |
| Logaritmos | Implementação frágil | `log()` e `ln()` passaram a ser processados diretamente | Funcionando |
| Porcentagem | Dependia do avaliador genérico | Operador `%` implementado no parser | Funcionando |
| Segurança | Expressões eram executadas com `new Function` | Tokenizador e parser matemático restrito | Risco crítico removido |
| Entradas inválidas | Podiam interromper o fluxo ou gerar resultados pouco claros | Divisão por zero, domínio inválido, símbolos desconhecidos e expressões incompletas passaram a ser rejeitados | Tratamento mais previsível |
| Linguagem natural | Parser limitado e dependente de substituições específicas | Reconhece operações, números por extenso, potências, raízes, fatorial, trigonometria e logaritmos | 11 frases diferentes testadas |
| Memória | Funções ausentes ou incompletas | Armazenar, recuperar, somar, subtrair e limpar foram implementados | Funcionando |
| Histórico | Painel dependia de funções incompletas | Resultados passaram a ser registrados e o painel pode ser aberto e fechado | Funcionando |
| Modos da calculadora | Controles incompletos | Modos padrão, científico e memória implementados | Funcionando |
| Teclado | Suporte incompleto | Números, operadores, `Enter`, `Backspace`, `Escape` e atalhos processados | Funcionando |
| Temas | Inicialização incompleta e seletores incorretos no tema Neon City | Todos os seis temas foram corrigidos e testados | Funcionando |
| Estilos dos botões | A troca de estilo podia gerar erro com classe vazia | Classes passaram a ser adicionadas e removidas apenas quando válidas | Cinco estilos funcionando |
| Persistência | Não havia garantia confiável após recarregar | Tema e estilo são recuperados após a atualização da página | Persistência confirmada |
| Botão de igualdade | Ocupava duas colunas e causava desalinhamento | Passou a ocupar uma única célula | Grade equilibrada |
| Responsividade | Poucos ajustes para telas pequenas | Breakpoints específicos e redução de espaçamento, fontes e dimensões | Melhor comportamento em celulares |
| Console | Erros JavaScript impediam partes da aplicação de funcionar | Teste final executado sem erros no console | Zero erros encontrados |

---

## 3. Parser matemático

### Versão original

A versão original utilizava uma abordagem baseada em:

- substituições textuais;
- transformação da expressão em JavaScript;
- execução com `new Function`;
- retornos inconsistentes entre números e objetos.

Essa estratégia apresentava problemas de:

- segurança;
- previsibilidade;
- precedência;
- funções aninhadas;
- validação;
- manutenção.

### Versão aprimorada

A versão atual utiliza:

- tokenização;
- parser matemático restrito;
- operadores permitidos;
- constantes conhecidas;
- funções matemáticas controladas;
- validação de domínio;
- tratamento de erros.

Com isso, entradas desconhecidas ou potencialmente perigosas são rejeitadas antes da execução.

---

## 4. Operações suportadas após as melhorias

### Operações básicas

- Soma.
- Subtração.
- Multiplicação.
- Divisão.
- Números negativos.
- Números decimais.
- Parênteses.
- Precedência matemática.

### Operações avançadas

- Potenciação.
- Porcentagem.
- Fatorial.
- Raiz quadrada.
- Raiz cúbica.
- Logaritmo de base 10.
- Logaritmo natural.
- Valor absoluto.
- Constantes π e e.

### Trigonometria

- Seno.
- Cosseno.
- Tangente.
- Arco seno.
- Arco cosseno.
- Arco tangente.
- Modo DEG.
- Modo RAD.

---

## 5. Diferencial em linguagem natural

A versão original já apresentava a ideia de interpretar frases em português, mas a implementação era limitada.

Após as alterações, o recurso passou a reconhecer comandos como:

```text
quadrado de 15
raiz quadrada de 81
raiz cúbica de 27
fatorial de 5
seno de 90
log natural de 10
dois mais três
2 elevado a 8
```

As expressões geradas pela entrada em linguagem natural também passam pelo parser matemático seguro. Dessa forma, esse recurso não contorna as validações de segurança.

---

## 6. Personalização visual

### Código original

O código original possuía uma proposta visual ampla, mas apresentava problemas de inicialização, seletores incompatíveis e manipulação incorreta de classes.

### Versão aprimorada

A versão final possui:

- seis temas testados;
- cinco estilos de botões testados;
- menu de personalização funcional;
- correção do tema Neon City;
- correção dos estilos Moderno, Quadrado, Redondo, Neon e Glass;
- persistência das preferências;
- restauração automática após recarregar a página.

---

## 7. Testes realizados

### Resultado geral

```text
34 de 34 testes automatizados aprovados
```

### Validações adicionais

- 11 comandos em português aprovados.
- Operações básicas validadas.
- Operações científicas validadas.
- Precedência matemática validada.
- DEG e RAD validados.
- Fatorial validado.
- Porcentagem validada.
- Memória validada.
- Histórico validado.
- Entrada pelo teclado validada.
- Seis temas aplicados.
- Cinco estilos aplicados.
- Persistência confirmada.
- Nenhum erro encontrado no console.
- Tentativas de executar JavaScript rejeitadas.

---

## 8. Resumo quantitativo

| Indicador | Resultado |
|---|---:|
| Testes automatizados | 34 de 34 aprovados |
| Comandos em português testados | 11 |
| Temas validados | 6 |
| Estilos de botões validados | 5 |
| Erros finais no console | 0 |
| Execução arbitrária de JavaScript | Bloqueada |
| Persistência da personalização | Confirmada |

---

## 9. Resultado geral

A versão original era visualmente promissora e demonstrava ambição técnica, mas funcionava como um protótipo instável.

Existiam funcionalidades aparentes na interface que não possuíam implementação completa. Além disso, um erro de sintaxe impedia o carregamento integral da aplicação e o avaliador matemático apresentava um problema importante de segurança.

Após a auditoria e as correções, o projeto passou a ser:

- executável;
- funcional;
- mais seguro;
- responsivo;
- personalizável;
- testado;
- documentado;
- consistente.

---

## 10. Conclusão

O projeto demonstra um fluxo completo de desenvolvimento assistido por inteligência artificial:

1. Definição dos requisitos.
2. Geração de um protótipo por um LLM local.
3. Execução e inspeção do resultado.
4. Auditoria técnica com outro modelo.
5. Identificação de falhas funcionais e de segurança.
6. Correção e refatoração.
7. Implementação das funções ausentes.
8. Validação automatizada.
9. Testes visuais e de responsividade.
10. Documentação das diferenças entre as versões.

O principal valor deste projeto não está apenas no código gerado, mas no processo de avaliação crítica, teste, correção e documentação do resultado produzido por diferentes ferramentas de inteligência artificial.
