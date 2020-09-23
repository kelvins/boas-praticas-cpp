# Guia Rápido de Boas Práticas em C

# Sumário

1. [Introdução](#introdução)  
2. [Estilo de Código](#estilo-de-código)  
2.1. [Nomes de Variáveis](#nomes-de-variáveis)  
2.2. [Nomes de Constantes](#nomes-de-constantes)  
2.3. [Nomes de Funções](#nomes-de-funções)  
2.4. [Comentários](#comentários)  
2.5. [Indentação](#indentação)  
2.6. [Não utilize números mágicos](#não-utilize-números-mágicos)  
2.7. [Inclua guards](#inclua-guards)  
2.8. [Sempre utilize chaves](#sempre-utilize-chaves)  
2.9. [Mantenha as linhas com um comprimento razoável](#mantenha-as-linhas-com-um-comprimento-razoável)  
2.10. [Utilize aspas duplas para incluir arquivos locais](#utilize-aspas-duplas-para-incluir-arquivos-locais)  
2.11. [Utilize double em vez de float](#utilize-double-em-vez-de-float)  
3. [Dicas](#dicas)  
3.1. [Lembre-se de liberar a memória dos ponteiros e verificar o seu retorno](#Lembre-se-de-liberar-a-memória-dos-ponteiros-e-verificar-o-seu-retorno)  
3.2. [Códigos não utilizados devem ser deletados](#códigos-não-utilizados-devem-ser-deletados)  
3.3. [Evite funções com muitos parâmetros](#evite-funções-com-muitos-parâmetros)  
3.4. [Utilize espaços em branco para melhor visualização](#utilize-espaços-em-branco-para-melhor-visualização)  
3.5. [Limite o escopo das variáveis](#limite-o-escopo-das-variáveis)  
3.6. [Sempre use typedef nas structs mais comuns](#Sempre-use-typedef-nas-structs-mais-comuns)  
3.7. [Pare e dê uma volta](#pare-e-dê-uma-volta)  
4. [Referências](#referências)  

# Introdução

Este documento apresenta um guia rápido de boas práticas em **C** (baseado no guia do mesmo repositório sobre **C++**, mas enxugando-o apenas para as práticas relevantes em **C** e suas funcionalidades) e é voltado para iniciantes na linguagem mas também pode ser útil para desenvolvedores intermediários.

As informações apresentadas neste guia foram obtidas de alguns materiais (livros e blogs), citados nas referências, e de conhecimento prático pessoal.

Achei importante criar este material em PT_BR pois a maioria dos materiais encontrados estão escritos na língua do Tio Sam, o que dificulta um pouco o entendimento, principalmente para os iniciantes. Além disso, tentei resumir de forma bem prática e direta alguns conceitos básicos de forma que este material possa ser utilizado como um guia de consulta rápida. (@Kelvin)

De maneira semelhante, adaptei o guia do @Kelvin sobre boas práticas em **C++** para um guia específico de **C**, com base em conhecimento prático pessoal e no guia de estilos do curso CS50 (e claro, as próprias aulas do CS50x). (@JoaoVitorDio)

Caso você não concorde com algo ou tenha alguma informação a acrescentar, sinta-se à vontade para criar issues ou enviar pull requests.

# Estilo de Código

Todo projeto possui seu estilo de código, alguns com algumas práticas mais avançadas e outros praticamente sem nenhum padrão. Porém, o estilo de um código tem grande impacto em sua respectiva legibilidade. Sendo assim, é importante investir algumas horas do seu tempo para estudar um pouco sobre isso, além de realizar revisões de código sempre que possível, garantindo um código mais fácil de manter e evoluir.

## Nomes de Variáveis

Variáveis devem sempre começar com letra minúscula, por exemplo:

![#c5f015](https://placehold.it/12/c5f015/000000?text=+) Bom
```c
char myWeirdVariable;
// ou
char my_weird_variable;
```

![#f03c15](https://placehold.it/12/f03c15/000000?text=+) Ruim
```c
char MyWeird_Variable2;
// ou
char My_weirdVariable_3;
```

Utilize um padrão já conhecido para a declaração das variáveis, como por exemplo:

- [CamelCase][1]
- [snake_case][2]

Em **C**, diferentemente de em **C++**, o padrão mais adotado é o **snake_case**. Raramente se vê códigos utilizando CamelCase, e quando há, normalmente são reservados para **structs** ou **typedefs**. (Não é regra)

Entretanto, quando trabalhando em um projeto conjunto, é interessante usar sempre o mesmo padrão de nomenclatura já vigente, desde que seja um dos citados acima.

## Nomes de Constantes

Constantes devem ser declaradas sempre em letras maiúsculas (caixa alta). Isso também vale para MACROS ("defines").

![#c5f015](https://placehold.it/12/c5f015/000000?text=+) Bom
```c
#define MAX 500
const double PI = 3.14159;
```

![#f03c15](https://placehold.it/12/f03c15/000000?text=+) Ruim
```c
#define max 500
const double pi = 3.14159;
```

## Nomes de Funções

Nomes de funções devem começar com a primeira letra minúscula, assim como as variáveis. Em C, as funções majoritariamente são escritas em snake_case:

![#c5f015](https://placehold.it/12/c5f015/000000?text=+) Bom
```c
void my_function();
```

![#f03c15](https://placehold.it/12/f03c15/000000?text=+) Ruim
```c
void MyFunction();
```

![#f03c15](https://placehold.it/12/f03c15/000000?text=+) Pior ainda
```c
void My_Function();
```


## Comentários

Utilize `//` para blocos de comentários (comentários de múltiplas linhas) dentro de funções, por exemplo:

```c
int equal( int value1, int value2 )
{
    // Compara dois valores e retorna
    // verdadeiro se os valores são iguais
    if( value1 == value2 )
    {
        return 1;
    }
    return 0;
}
```

Caso seja necessário comentar um bloco de código para debugar ou por algum outro motivo, você não terá problemas, por exemplo:

![#c5f015](https://placehold.it/12/c5f015/000000?text=+) Bom
```c
int equal( int value1, int value2 )
{
    /*
    // Compara dois valores e retorna
    // verdadeiro se os valores são iguais
    if( value1 == value2 )
    {
        return 1;
    }
    */
    return 0;
}
```

Caso contrário, não seria possível comentar o bloco de código inteiro, por exemplo:

![#f03c15](https://placehold.it/12/f03c15/000000?text=+) Ruim
```c
int equal( int value1, int value2 )
{
    /*
    /*
     * Compara dois valores e retorna
     * verdadeiro se os valores são iguais
     */
    if( value1 == value2 )
    {
        return 1;
    }
    */
    return 0;
}
```

Além disso, na minha opinião, quando é utilizado `//` para comentários de múltiplas linhas o código parece ser mais legível do que quando se utiliza `/* */`.

## Indentação

O mais comum é a indentação ou recuo de código utilizando 4 espaços, 2 espaços ou 1 tab. Isso pode mudar de projeto para projeto ou mesmo de acordo com a linguagem de programação. Eu pessoalmente costumo utilizar 4 espaços e acredito que este seja o padrão mais utilizado pelos desenvolvedores. É possível configurar a IDE ou o editor para utilizar por padrão o indentação desejada.

**Pequeno ponto de atenção:** O arquivo específico do makefile necessariamente depende de hard tabs (1 tab). A opção mais comum é configurar a IDE para soft tabs de 4 espaços, e alterar somente na escrita do makefile, ou usar um conversor de soft tabs para hard tab da internet, por exemplo, esse: [Conversor de espaços para hard tabs][3]

## Não utilize números mágicos

Não utilize números 'mágicos', por exemplo:

![#f03c15](https://placehold.it/12/f03c15/000000?text=+) Ruim
```c
double calc( double value )
{
    return value * 3.14159;
}
```

Nestes casos opte por definir uma constante, por exemplo:

![#c5f015](https://placehold.it/12/c5f015/000000?text=+) Bom
```c
const double PI = 3.14159;

double calc( double value )
{
    return value * PI;
}
```

Mas utilize, SIM, números, quando isso fizer sentido, por exemplo:

![#c5f015](https://placehold.it/12/c5f015/000000?text=+) Bom
```c
double calc( double value )
{
    return value * 2;
}
```

![#f03c15](https://placehold.it/12/f03c15/000000?text=+) Ruim
```c
#define TWO 2

double calc( double value )
{
    return value * TWO;
}
```

## Inclua guards

Arquivos de cabeçalho (header files) devem utilizar guards para evitar problemas com a inclusão do mesmo arquivo múltiplas vezes e previnir conflitos com cabeçalhos de outros projetos. [Include_guards][4]

![#c5f015](https://placehold.it/12/c5f015/000000?text=+) Bom
```c
#ifndef MYTAD_H
#define MYTAD_H

struct my_struct
{
	int struct_infos;
};

#endif
```

![#f03c15](https://placehold.it/12/f03c15/000000?text=+) Ruim
```c
struct my_struct
{
	int struct_infos;
};
```

## Sempre utilize chaves

Sempre utilize chaves, ainda que exista apenas uma linha de código dentro de um bloco.
Há desenvolvedores que se utilizam das chaves na mesma linha da função/estrutura, e outros que a colocam na linha seguinte. Essa questão é pessoal e assim como citado na escolha entre CamelCase e snake_case, é bom usar o padrão já existente no projeto em que se trabalha. Se for um projeto unicamente seu e o seu estilo é o único do código, opte pelo que julgar mais confortável. Particularmente, uso em linhas separadas por ser uma leve recomendação do guia de estilos do CS50.

A não utilização de chaves pode causar erros semânticos no código, por exemplo:

![#c5f015](https://placehold.it/12/c5f015/000000?text=+) Bom
```c
int sum = 0;
for (int i = 0; i < 15; ++i)
{
    ++sum;
   printf("%d", i);
}
```

![#f03c15](https://placehold.it/12/f03c15/000000?text=+) Ruim
```c
for (int i = 0; i < 15; ++i)
    printf("%d", i);
```

![#f03c15](https://placehold.it/12/f03c15/000000?text=+) Erro semântico
```c
int sum = 0;
for (int i = 0; i < 15; ++i)
    ++sum;
    printf("%d", i);
```

## Mantenha as linhas com um comprimento razoável

Mantenha as linhas com um comprimento razoável. Caso a linha seja muito extensa, tenha muitos caracteres, vale a pena quebrá-la em múltiplas linhas, por exemplo:

![#f03c15](https://placehold.it/12/f03c15/000000?text=+) Ruim
```c
if( (x == 1 && y == 2 && myFunction() == true) || (x == 0 && y == 0 && myFunction() == false) )
{

}
```

![#c5f015](https://placehold.it/12/c5f015/000000?text=+) Bom
```c
if( (x == 1 && y == 2 && myFunction() == true) ||
    (x == 0 && y == 0 && myFunction() == false) )
{

}
```

## Utilize aspas duplas para incluir arquivos locais

Utilize aspas duplas (`""`) para incluir arquivos locais.

![#f03c15](https://placehold.it/12/f03c15/000000?text=+) Ruim
```c
#include <stdio.h>
#include <my_header.h>
```

![#c5f015](https://placehold.it/12/c5f015/000000?text=+) Bom
```c
#include <stdio.h>
#include "my_header.h"
```


## Utilize double em vez de float

A utilização de `float` irá reduzir a precisão. Porém, em operações com vetores `float` pode ser mais rápido que `double` se você puder sacrificar a precisão.

Contudo, `double` é a opção padrão recomendada já que este é o tipo padrão para valores de ponto flutuante em C.

# Dicas

Nesta seção você irá encontrar algumas dicas importantes que podem ser úteis durante o desenvolvimento.

## Lembre-se de liberar a memória dos ponteiros e verificar o seu retorno

Lembre-se de sempre liberar a memória alocada e jamais faça um programa com vazamento de memória (memory leak). A linguagem **C** não possui garbage collector, tampouco ponteiros inteligentes como **C++**, e toda a responsabilidade está na sua mão como desenvolvedor de fazer um código eficiente, enxuto, funcional e otimizado (e por isso a linguagem é tão rápida e poderosa). 

Lembrando: As funções de alocação e desalocação de memória heap fazem parte da biblioteca stdlib.h.

**Recomendações adicionais:** 
O uso da função assert() (que faz parte da biblioteca assert.h) substitui todo o código de verificação. Se a condição não for atendida, a função interromperá o fluxo do programa instantaneamente.
Sistemas Unix possuem uma ferramenta de terminal (incluída nos pacotes de desenvolvedor, comumente) super útil para verificar programas com vazamento de memória e ajudar a identificá-los. Procure por **Valgrind**.

![#c5f015](https://placehold.it/12/c5f015/000000?text=+) Bom
```c
#include <stdlib.h>

int rows = 5, columns = 2;

int **matriz = (int **) calloc(rows, sizeof(int *));

if (matriz == NULL)	// Verificacao manual:
{
	return 1;
}

for (int i = 0; i < rows; i++)
{
	matriz[i] = (int *) calloc(columns, sizeof(int));
	assert(matriz[i] != NULL);	// verificacao usando assert:
}

// Uso aleatório do array

// Liberando a memória:
for (int i = 0; i < rows; i++)
{
	free(matriz[i]);
}
free(matriz);


```

![#f03c15](https://placehold.it/12/f03c15/000000?text=+) Ruim
```c
#include <stdlib.h>

int rows = 5, columns = 2;

int **matriz = (int **) calloc(rows, sizeof(int *));
for (int i = 0; i < rows; i++)
{
	matriz[i] = (int *) calloc(columns, sizeof(int));
}

// Uso aleatório do array

return 0;
```

Sempre verifique seus programas com o Valgrind.



## Códigos não utilizados devem ser deletados

Códigos não mais utilizados (comentados) devem ser deletados, por exemplo:

![#f03c15](https://placehold.it/12/f03c15/000000?text=+) Ruim
```c
int equal( int value1, int value2 )
{
    /*
    if( value1 < value2 || value1 > value2 )
    {
        return 0;
    }
    else
    {
        return 1;
    }
    */
    // Compara dois valores e retorna
    // verdadeiro se os valores são iguais
    if( value1 == value2 )
    {
        return 1;
    }
    return 0;
}
```

![#c5f015](https://placehold.it/12/c5f015/000000?text=+) Bom
```c
int equal( int value1, int value2 )
{
    // Compara dois valores e retorna
    // verdadeiro se os valores são iguais
    if ( value1 == value2 )
    {
        return 1;
    }
    return 0;
}
```

Assim o código fica mais limpo e mais fácil de compreender.

## Evite funções com muitos parâmetros

Sempre que possível, evite a utilização de muitos parâmetros em funções. Funções com muitos parâmetros são geralmente difíceis de compreender. Se necessário, refatore a função.

![#f03c15](https://placehold.it/12/f03c15/000000?text=+) Ruim
```c
void show_user_information(char *firstName, char *lastName, char *gender, int age, double height, double weight);
```

![#c5f015](https://placehold.it/12/c5f015/000000?text=+) Bom
```c
// Onde 'User' é uma estrutura de dados
void show_user_information(user *individual_user);
```

## Utilize espaços em branco para melhor visualização

**Não consigo expressar a ênfase que eu gostaria de dar para essa dica específica**, é ultra relevante e *ignorada por muitos* . :unamused:

Utilize espaços em branco para melhor visualização, por exemplo:

![#c5f015](https://placehold.it/12/c5f015/000000?text=+) Bom
```c
if ((majorVersion == 2 && minorVersion == 5) || majorVersion >= 3)
```

![#f03c15](https://placehold.it/12/f03c15/000000?text=+) Ruim
```c
if((majorVersion==2 && minorVersion==5) || majorVersion>=3)
```

![#f03c15](https://placehold.it/12/f03c15/000000?text=+) Pior ainda
```c
if((majorVersion==2&&minorVersion==5)||majorVersion>=3)
```

Não é bem um padrão, mas nos cursos de ciência da computação de Harvard (onde eu aprendi), os espaços são usados assim, de acordo com o tipo de ferramenta da linguagem:

**Funções**:

`void my_function(int first_parameter, char second_parameter);`

**Estrutura condicional e estruturas de repetição**:
```c
if (random_variable == something)
{

}

for (int i = 0; i < something; i++)
{

}
```

**Operações aritméticas e comando de atribuição:**
```c
int x = variable % random_value;
```

**Uso de ponteiros de structs**:
```c
typedef struct 
{
		int struct_infos;
} my_struct_type;

my_struct_type variable, *p_my_pointer;

p_my_pointer = &variable;

p_my_pointer -> struct_infos = some value;

//	Não é necessário dar esses pulos de linha
```


## Limite o escopo das variáveis

Sempre que possível, limite o escopo das variáveis. É útil em termos de otimização de espaço da memória, quanto de legibilidade e compreensão do código, visto que o uso das variáveis estará logo nas linhas abaixo:

![#c5f015](https://placehold.it/12/c5f015/000000?text=+) Bom
```c
//	Declarando a variável de contagem dentro do laço
//	e garantindo seu curto período de vida na memória
for (int i = 0; i < 15; ++i)
{
    my_function(i);
}
```

![#f03c15](https://placehold.it/12/f03c15/000000?text=+) Ruim
```c
int i;
for (i = 0; i < 15; ++i)
{
    my_function(i);
}
//	i ainda está ocupando memória sem motivo, e um leitor pode se perder
//	com o atual valor de i quando ele for usado posteriormente, caso seja.
```

## Sempre use typedef nas structs mais comuns

Pelo bem da legibilidade do seu código, não congestione-o com inúmeras variáveis, parâmetros e quaisquer outros fins da sua estrutura com "struct nome_da_estrutura nome_da_variavel". Sempre utilize typedefs para as suas estruturas e sobretudo, nas mais comuns.

![#f03c15](https://placehold.it/12/f03c15/000000?text=+) Ruim
```c
struct carro 
{
	int ano;
	char[TAM_PLACA] placa_do_carro;
};

struct carro carrinho; 

void verify_car_year(struct carro carrinho);
```

![#c5f015](https://placehold.it/12/c5f015/000000?text=+) Bom
```c
typedef struct
{
	int ano;
	char[TAM_PLACA] placa_do_carro;
} carro;

carro carrinho; 

void verify_car_year(carro carrinho);
```

## Pare e dê uma volta

Sempre que estiver empacado na solução de um problema, respire fundo e vá dar uma volta ou fazer alguma outra atividade por um certo período de tempo. Isso ajuda a esfriar um pouco a cabeça e pensar em uma solução mais claramente.

# Referências

**C++ Best Practices**: https://www.gitbook.com/book/lefticus/cpp-best-practices/details

**Harvard's CS50 C Style Guide:** https://cs50.readthedocs.io/style/c/.

**Google C++ Style Guide**: https://google.github.io/styleguide/cppguide.html

**10 most voted C++ best practices**: http://codergears.com/Blog/?p=1957

[1]: https://pt.wikipedia.org/wiki/CamelCase "CamelCase"
[2]: https://en.wikipedia.org/wiki/Snake_case "snake_case"
[4]: https://pt.wikipedia.org/wiki/Include_guard "Mais informações sobre include guards aqui."
[3]: https://pinetools.com/convert-spaces-tabs "Conversor de espaços para hard tabs"
