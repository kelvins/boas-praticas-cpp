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
2.8. [Inclua guards](#inclua-guards)  
2.9. [Sempre utilize chaves](#sempre-utilize-chaves)  
2.10. [Mantenha as linhas com um comprimento razoável](#mantenha-as-linhas-com-um-comprimento-razoável)  
2.11. [Utilize aspas duplas para incluir arquivos locais](#utilize-aspas-duplas-para-incluir-arquivos-locais)  
2.12. [Utilize constantes sempre que possível](#utilize-constantes-sempre-que-possível)  
2.13. [Passe ou retorne tipos simples por valor](#passe-ou-retorne-tipos-simples-por-valor)  
2.14. [Utilize double em vez de float](#utilize-double-em-vez-de-float)  
3. [Dicas](#dicas)  
3.1. [Lembre-se de deletar os ponteiros](#lembre-se-de-deletar-os-ponteiros)  
3.2. [Utilize ponteiros inteligentes](#utilize-ponteiros-inteligentes)  
3.3. [Códigos não utilizados devem ser deletados](#códigos-não-utilizados-devem-ser-deletados)  
3.4. [Evite métodos com muitos parâmetros](#evite-métodos-com-muitos-parâmetros)  
3.5. [Utilize espaços em branco para melhor visualização](#utilize-espaços-em-branco-para-melhor-visualização)  
3.6. [Limite o escopo das variáveis](#limite-o-escopo-das-variáveis)  
3.7. [Prefira `++i` em vez de `i++`](#refira-`++i`-em-vez-de-`i++`)  
3.8. [Pare e dê uma volta](#pare-e-dê-uma-volta)  
4. [Referências](#referências)  

# Introdução

Este documento apresenta um guia rápido de boas práticas em **C++** e é voltado para iniciantes na linguagem mas também pode ser útil para desenvolvedores intermediários.

As informações apresentadas neste guia foram obtidas de alguns materiais (livros e blogs), citados nas referências, e de conhecimento prático pessoal.

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

## Inclua guards

Arquivos de cabeçalho (header files) devem utilizar guards para evitar problemas com a inclusão do mesmo arquivo múltiplas vezes e previnir conflitos com cabeçalhos de outros projetos:

![#c5f015](https://placehold.it/12/c5f015/000000?text=+) Bom
```c++
#ifndef MYCLASS_H
#define MYCLASS_H

class MyClass
{
public:
    void myFunc();
};

#endif
```

![#f03c15](https://placehold.it/12/f03c15/000000?text=+) Ruim
```c++
class MyClass
{
public:
    void myFunc();
};
```

## Sempre utilize chaves

Sempre utilize chaves mesmo quando existe apenas uma linha de código dentro de um bloco. A não utilização de chaves pode causar erros semânticos no código, por exemplo:

![#c5f015](https://placehold.it/12/c5f015/000000?text=+) Bom
```c++
int sum = 0;
for (int i = 0; i < 15; ++i)
{
    ++sum;
    std::cout << i << std::endl;
}
```

![#f03c15](https://placehold.it/12/f03c15/000000?text=+) Ruim
```c++
for (int i = 0; i < 15; ++i)
    std::cout << i << std::endl;
```

![#f03c15](https://placehold.it/12/f03c15/000000?text=+) Erro semântico
```c++
int sum = 0;
for (int i = 0; i < 15; ++i)
    ++sum;
    std::cout << i << std::endl;
```

## Mantenha as linhas com um comprimento razoável

Mantenha as linhas com um comprimento razoável. Caso a linha seja muito extensa, tenha muitos caracteres, vale a pena quebrá-la em múltiplas linhas, por exemplo:

![#f03c15](https://placehold.it/12/f03c15/000000?text=+) Ruim
```c++
if( (x == 1 && y == 2 && myFunction() == true) || (x == 0 && y == 0 && myFunction() == false) )
{

}
```

![#c5f015](https://placehold.it/12/c5f015/000000?text=+) Bom
```c++
if( (x == 1 && y == 2 && myFunction() == true) ||
    (x == 0 && y == 0 && myFunction() == false) )
{

}
```

## Utilize aspas duplas para incluir arquivos locais

Utilize aspas duplas (`""`) para incluir arquivos locais.

![#f03c15](https://placehold.it/12/f03c15/000000?text=+) Ruim
```c++
#include <string>
#include <MyHeader.hpp>
```

![#c5f015](https://placehold.it/12/c5f015/000000?text=+) Bom
```c++
#include <string>
#include "MyHeader.hpp"
```

## Utilize constantes sempre que possível

Utilize `const` sempre que possível. `const` avisa ao compilador que a variável é imutável. Isto auxilia o compilador a otimizar o código e ajuda o programador a saber se uma função tem "efeitos colaterais". Ainda, a utilização de `const &` previne o compilador de copiar dados desnecessariamente.

![#f03c15](https://placehold.it/12/f03c15/000000?text=+) Ruim
```c++
class MyClass
{
public:
    void do_something(int i);
    void do_something(std::string str);
};
```

![#c5f015](https://placehold.it/12/c5f015/000000?text=+) Bom
```c++
class MyClass
{
public:
    void do_something(const int i);
    void do_something(const std::string &str);
};
```

## Passe ou retorne tipos simples por valor

Não passe ou retorne tipos simples por referência, mas sim por valor:

![#f03c15](https://placehold.it/12/f03c15/000000?text=+) Ruim
```c++
class MyClass
{
public:
    explicit MyClass(const int& t_int_value)
        : m_int_value(t_int_value)
    {
    }

    const int& get_int_value() const
    {
        return m_int_value;
    }

private:
    int m_int_value;
}
```

Se o valor não será alterado é possível utilizar `const`.

![#c5f015](https://placehold.it/12/c5f015/000000?text=+) Bom
```c++
class MyClass
{
public:
    explicit MyClass(const int t_int_value)
        : m_int_value(t_int_value)
    {
    }

    int get_int_value() const
    {
        return m_int_value;
    }

private:
    int m_int_value;
}
```

Utilize a passagem de parâmetro por referência para objetos, vetores, etc.

## Utilize double em vez de float

A utilização de `float` irá reduzir a precisão. Porém, em operações com vetores `float` pode ser mais rápido que `double` se você puder sacrificar a precisão.

Contudo, `double` é a opção padrão recomendada já que este é o tipo padrão para valores de ponto flutuante em C++.

# Dicas

Nesta seção você irá encontrar algumas dicas importantes que podem ser úteis durante o desenvolvimento.

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

![#f03c15](https://placehold.it/12/f03c15/000000?text=+) Ruim
```c++
void showUserInformation(string firstName, string lastName, string gender, int age, double height, double weight);
```

![#c5f015](https://placehold.it/12/c5f015/000000?text=+) Bom
```c++
// Onde 'User' é um objeto/estrutura de dados
void showUserInformation(User &user);
```

## Utilize espaços em branco para melhor visualização

Utilize espaços em branco para melhor visualização, por exemplo:

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

## Limite o escopo das variáveis

Sempre que possível limite o escopo das variáveis:

![#c5f015](https://placehold.it/12/c5f015/000000?text=+) Bom
```c++
for (int i = 0; i < 15; ++i)
{
    MyObject obj(i);
    // Faça algo com obj
}
```

![#f03c15](https://placehold.it/12/f03c15/000000?text=+) Ruim
```c++
MyObject obj; // inicialização de objeto sem sentido
for (int i = 0; i < 15; ++i)
{
    obj = MyObject(i); // operação de atribuição desnecessária
    // Faça algo com obj
}
// obj ainda está ocupando memória sem motivo
```

## Prefira `++i` em vez de `i++`

Ainda que `i++` seja semanticamente correto, o pré-incremento (`++i`) é mais rápido que pós-incremento (`i++`), uma vez que não requer uma cópia do objeto.

![#f03c15](https://placehold.it/12/f03c15/000000?text=+) Ruim
```c++
for (int i = 0; i < 15; i++)
{
    std::cout << i << '\n';
}
```

![#c5f015](https://placehold.it/12/c5f015/000000?text=+) Bom
```c++
for (int i = 0; i < 15; ++i)
{
    std::cout << i << '\n';
}
```

Mesmo que os compiladores mais modernos otimizem esses dois laços para o mesmo código assembly, a utilização de `++i` ainda é uma boa prática.

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
