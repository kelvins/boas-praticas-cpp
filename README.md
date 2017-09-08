# Guia Rápido de Boas Práticas em C++

# Sumário

1. [Introdução](#introdução)  
2. [Estilo de Código](#estilo-de-código)  
2.1. [Nomes de Variáveis](#nomes-de-variáveis)  
2.2. [Nomes de Constantes](#nomes-de-constantes)  
2.3. [Nomes de Funções](#nomes-de-funções)  
2.4. [Nomes de Classes](#nomes-de-classes)  
2.5. [Comentários](#comentários)  
2.6. [Indentação](#indentação)  
2.7. [Não utilize números mágicos](#não-utilize-números-mágicos)  
3. [Dicas](#dicas)  
3.1. [Lembre-se de deletar os ponteiros](#lembre-se-de-deletar-os-ponteiros)  
3.2. [Utilize ponteiros inteligentes](#utilize-ponteiros-inteligentes)  
3.3. [Códigos não utilizados devem ser deletados](#códigos-não-utilizados-devem-ser-deletados)  
3.4. [Evite métodos com muitos parâmetros](#evite-métodos-com-muitos-parâmetros)  
3.5. [Utilize espaços em branco para melhor visualização](#utilize-espaços-em-branco-para-melhor-visualização)  
3.6. [Pare e dê uma volta](#pare-e-dê-uma-volta)  
4. [Referências](#referências)  

# Introdução

Este documento apresenta um guia rápido de boas práticas em **C++** e é voltado para iniciantes na linguagem mas também pode ser útil para desenvolvedores intermediários.

As informações apresentadas neste guia foram obtidas de alguns materiais (livros e blogs), citados nas referências, e de conhecimento prático pessoal.

Este guia possui opiniões pessoais e não deve ser utilizado como um guia definitivo de boas práticas, porém o mesmo pode ser utilizado para padronizar o estilo dos códigos em C++, bem como apresentar alguns conceitos básicos da linguagens.

Achei importante criar este material em PT_BR pois a maioria dos materiais encontrados estão escritos na língua do Tio Sam, o que dificulta um pouco o entendimento, principalmente para os iniciantes. Além disso, tentei resumir de forma bem prática e direta alguns conceitos básicos de forma que este material possa ser utilizado como um guia de consulta rápida.

Caso você não concorde com algo ou tenha alguma informação a acrescentar, sinta-se à vontade para criar issues ou enviar pull requests.

# Estilo de Código

Todo projeto possui seu estilo de código, alguns com algumas práticas mais avançadas e outros praticamente sem nenhum padrão. Porém, o estilo de código tem um grande impacto na legibilidade do mesmo. Sendo assim, é importante investir algumas horas do seu tempo para estudar um pouco sobre isso, além de realizar revisões de código sempre que possível, garantindo um código mais fácil de manter e evoluir.

## Nomes de Variáveis

Variáveis devem sempre começar com letra minúscula, por exemplo:

![#c5f015](https://placehold.it/12/c5f015/000000?text=+) Bom
```c++
string myWeirdVariable;
// ou
string my_weird_variable;
```

![#f03c15](https://placehold.it/12/f03c15/000000?text=+) Ruim
```c++
string MyWeird_Variable2;
// ou
string My_weirdVariable_3;
```

Utilize um padrão já conhecido para a declaração das variáveis, como por exemplo:

- [CamelCase][1]
- [snake_case][2]

Eu pessoalmente prefiro utilizar o padrão **CamelCase** e vejo muita gente utilizando ele também. Mas isso não significa que você deva necessariamente utilizá-lo. O mais importante é manter a consistência na declaração das variáveis.

## Nomes de Constantes

Constantes devem ser declaradas sempre em letras maiúsculas (caixa alta):

![#c5f015](https://placehold.it/12/c5f015/000000?text=+) Bom
```c++
const double PI = 3.14159;
```

![#f03c15](https://placehold.it/12/f03c15/000000?text=+) Ruim
```c++
const double pi = 3.14159;
```

## Nomes de Funções

Nomes de funções devem começar com a primeira letra minúscula, assim como as variáveis:

![#c5f015](https://placehold.it/12/c5f015/000000?text=+) Bom
```c++
void myFunction();
```

![#f03c15](https://placehold.it/12/f03c15/000000?text=+) Ruim
```c++
void MyFunction();
```

![#f03c15](https://placehold.it/12/f03c15/000000?text=+) Pior ainda
```c++
void My_Function();
```

## Nomes de Classes

Nomes de classes devem começar com a primeira letra maiúscula e seguir o padrão CamelCase (preferencialmente):

![#c5f015](https://placehold.it/12/c5f015/000000?text=+) Bom
```c++
class LinkedList
```

![#f03c15](https://placehold.it/12/f03c15/000000?text=+) Ruim
```c++
class linkedList
```

## Comentários

Utilize `//` para blocos de comentários (comentários de múltiplas linhas) dentro de funções, por exemplo:

```c++
bool equal( int value1, int value2 )
{
    // Compara dois valores e retorna
    // verdadeiro se os valores são iguais
    if( value1 == value2 )
    {
        return true;
    }
    return false;
}
```

Caso seja necessário comentar um bloco de código para debugar ou por algum outro motivo, você não terá problemas, por exemplo:

![#c5f015](https://placehold.it/12/c5f015/000000?text=+) Bom
```c++
bool equal( int value1, int value2 )
{
    /*
    // Compara dois valores e retorna
    // verdadeiro se os valores são iguais
    if( value1 == value2 )
    {
        return true;
    }
    */
    return false;
}
```

Caso contrário, não seria possível comentar o bloco de código inteiro, por exemplo:

![#f03c15](https://placehold.it/12/f03c15/000000?text=+) Ruim
```c++
bool equal( int value1, int value2 )
{
    /*
    /*
     * Compara dois valores e retorna
     * verdadeiro se os valores são iguais
     */
    if( value1 == value2 )
    {
        return true;
    }
    */
    return false;
}
```

Além disso, na minha opinião, quando é utilizado `//` para comentários de múltiplas linhas o código parece ser mais legível do que quando se utiliza `/* */`.

## Indentação

O mais comum é a indentação ou recuo de código utilizando 4 espaços, 2 espaços ou 1 tab. Isso pode mudar de projeto para projeto ou mesmo de acordo com a linguagem de programação. Eu pessoalmente costumo utilizar 4 espaços e acredito que este seja o padrão mais utilizado pelos desenvolvedores. É possível configurar a IDE ou o editor para utilizar por padrão o indentação desejada.

## Não utilize números mágicos

Não utilize números 'mágicos', por exemplo:

![#f03c15](https://placehold.it/12/f03c15/000000?text=+) Ruim
```c++
double calc( double value )
{
    return value * 3.14159;
}
```

Nestes casos opte por definir uma constante, por exemplo:

![#c5f015](https://placehold.it/12/c5f015/000000?text=+) Bom
```c++
const double PI = 3.14159;

double calc( double value )
{
    return value * PI;
}
```

Mas utilize, SIM, números, quando isso fizer sentido, por exemplo:

![#c5f015](https://placehold.it/12/c5f015/000000?text=+) Bom
```c++
double calc( double value )
{
    return value * 2;
}
```

![#f03c15](https://placehold.it/12/f03c15/000000?text=+) Ruim
```c++
#define TWO 2

double calc( double value )
{
    return value * TWO;
}
```

# Dicas

## Lembre-se de deletar os ponteiros

Lembre-se de sempre deletar os ponteiros para liberar a memória alocada. Além de deletar o ponteiro, eu costumo definir ele como `NULL` para evitar [comportamento indefinido][3] (isso faz mais sentido quando o ponteiro está no escopo da classe e não da função).

![#c5f015](https://placehold.it/12/c5f015/000000?text=+) Bom
```c++
double myFunction(double value1, double value2)
{
    Calculator *calc = new Calculator();
    
    double result = calc->sum(value1, value2);

    delete calc;
    calc = NULL;

    return result;
}
```

![#f03c15](https://placehold.it/12/f03c15/000000?text=+) Ruim
```c++
double myFunction(double value1, double value2)
{
    Calculator *calc = new Calculator();
    return calc->sum(value1, value2);
}
```

Contudo, opte por utilizar [ponteiros inteligentes][4] (próximo tópico) sempre que possível.

## Utilize ponteiros inteligentes

Sempre que possível utilize ponteiros inteligentes (smart pointers) ao invés de utilizar os ponteiros tradicionais (raw pointers). O uso de ponteiros inteligentes pode evitar diversos problemas, dentre eles o [vazamento de memória][5] (memory leak).

![#c5f015](https://placehold.it/12/c5f015/000000?text=+) Bom
```c++
void ponteiroInteligente()
{
    // Declare um ponteiro inteligente na pilha e passe o ponteiro tradicional (ponteiro bruto)
    unique_ptr<Song> pSong(new Song(L"Nothing on You", L"Bruno Mars"));

    // Utilize pSong...
    // Exemplo: pSong->duration();
    // pSong é deletado automaticamente ao fim da função
}
```

![#f03c15](https://placehold.it/12/f03c15/000000?text=+) Ruim
```c++
void ponteiroTradicional()
{
    // Utilizando ponteiro tradicional (ponteiro bruto)
    Song* pSong = new Song(L"Nothing on You", L"Bruno Mars"); 

    // Utilize pSong...
    // Exemplo: pSong->duration();

    // Não esqueça de deletar o ponteiro
    delete pSong;   
}
```

Exemplo modificado de: https://msdn.microsoft.com/pt-br/library/hh279674.aspx

## Códigos não utilizados devem ser deletados

Códigos não mais utilizados (comentados) devem ser deletados, por exemplo:

![#f03c15](https://placehold.it/12/f03c15/000000?text=+) Ruim
```c++
bool equal( int value1, int value2 )
{
    /*
    if( value1 < value2 || value1 > value2 )
    {
        return false; 
    }
    else
    {
        return true;
    }
    */
    // Compara dois valores e retorna
    // verdadeiro se os valores são iguais
    if( value1 == value2 )
    {
        return true;
    }
    return false;
}
```

![#c5f015](https://placehold.it/12/c5f015/000000?text=+) Bom
```c++
bool equal( int value1, int value2 )
{
    // Compara dois valores e retorna
    // verdadeiro se os valores são iguais
    if( value1 == value2 )
    {
        return true;
    }
    return false;
}
```

Assim o código fica mais limpo e mais fácil de compreender.

## Evite métodos com muitos parâmetros

Sempre que possível evite a utilização de muitos parâmetros em métodos. Métodos com muitos parâmetros são geralmente difíceis de compreender. Se necessário refatore o método.

## Utilize espaços em branco para melhor a visualização

Utilize espaços em branco para melhor a visualização, por exemplo:

![#c5f015](https://placehold.it/12/c5f015/000000?text=+) Bom
```c++
if( (majorVersion == 2 && minorVersion == 5) || majorVersion >= 3 )
```

![#f03c15](https://placehold.it/12/f03c15/000000?text=+) Ruim
```c++
if((majorVersion==2 && minorVersion==5) || majorVersion>=3)
```

![#f03c15](https://placehold.it/12/f03c15/000000?text=+) Pior ainda
```c++
if((majorVersion==2&&minorVersion==5)||majorVersion>=3)
```

## Pare e dê uma volta

Sempre que estiver empacado na solução de um problema, respire fundo e vá dar uma volta ou fazer alguma outra atividade por um certo período de tempo. Isso ajuda a esfriar um pouco a cabeça e pensar em uma solução mais claramente.

# Referências

**C++ Best Practices**: https://www.gitbook.com/book/lefticus/cpp-best-practices/details

**Google C++ Style Guide**: https://google.github.io/styleguide/cppguide.html

**10 most voted C++ best practices**: http://codergears.com/Blog/?p=1957

 [1]: https://pt.wikipedia.org/wiki/CamelCase
 [2]: https://en.wikipedia.org/wiki/Snake_case
 [3]: https://pt.wikipedia.org/wiki/Comportamento_indefinido
 [4]: https://pt.wikipedia.org/wiki/Ponteiro_inteligente
 [5]: https://pt.wikipedia.org/wiki/Vazamento_de_mem%C3%B3ria
