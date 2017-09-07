# Guia Rápido de Boas Práticas em C++

## Introdução

Este documento apresenta um guia rápido de boas práticas em C++ e é voltado para usuário iniciantes e/ou intermediários.

As informações apresentadas neste guia foram obtidas de alguns materiais (livros e blogs), citados nas referências, e de conhecimento prático pessoal.

Este guia possui opiniões pessoais e não deve ser utilizado como um guia definitivo de boas práticas, porém o mesmo pode ser utilizado para padronizar o estilo dos códigos em C++, bem como apresentar alguns conceitos básicos da linguagens.

Caso você não concorde com algo ou tenha alguma informação a acrescentar, sinta-se à vontade para criar issues ou enviar pull requests.

## Estilo de Código

### Nomes de Variáveis

Variáveis devem sempre começar com letra minúscula, por exemplo:

![#c5f015](https://placehold.it/12/c5f015/000000?text=+) Bom
```c++
string myWeirdVariable;
// ou
string my_weird_variable;
```

![#f03c15](https://placehold.it/12/f03c15/000000?text=+) Ruim
```c++
string myWeird_Variable2;
// ou
string my_weirdVariable_3;
```

Utilize um padrão já conhecido para a declaração das variáveis, como por exemplo:

- [CamelCase][1]
- [snake_case][2]

Eu pessoalmente prefiro utilizar o padrão **CamelCase** e vejo muita gente utilizando ele também. Mas isso não significa que você deva necessariamente utilizá-lo. O mais importante é manter a consistência na declaração das variáveis.

### Nomes de Constantes

Constantes devem ser declaradas sempre em letras maiúsculas (caixa alta):

![#c5f015](https://placehold.it/12/c5f015/000000?text=+) Bom
```c++
const double PI = 3.14159;
```

![#f03c15](https://placehold.it/12/f03c15/000000?text=+) Ruim
```c++
const double pi = 3.14159;
```

### Nomes de Funções

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

### Nomes de Classes

Nomes de classes devem começar com a primeira letra maiúscula e seguir o padrão CamelCase (preferencialmente):

![#c5f015](https://placehold.it/12/c5f015/000000?text=+) Bom
```c++
class LinkedList
```

![#f03c15](https://placehold.it/12/f03c15/000000?text=+) Ruim
```c++
class linkedList
```

### Comentários

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

## Boas Práticas

## Dicas

## Referências

http://codergears.com/Blog/?p=1957

https://www.gitbook.com/book/lefticus/cpp-best-practices/details

http://www.cplusplus.com/forum/lounge/6195/

https://google.github.io/styleguide/cppguide.html

 [1]: https://pt.wikipedia.org/wiki/CamelCase
 [2]: https://en.wikipedia.org/wiki/Snake_case
