# Prova-Eive-java-101-Exam-2
1. Por que a execução do Java é realizada em pilha?
    * Para organizar a ordem de execução do código. A pilha existe para executar algo e lembrar o que ainda precisa ser executado. Um programa Java sempre começa ser executado pelo método main().

2. Em programação, qual(is) a(s) utilidade(s) de *debugar* um código?
    * Ajuda a entender passo a passo do fluxo do programa, ver os valores em cada linha do código em tempo de execução. Dessa forma o desenvolvedor consegue analisar melhor o código e encontrar erros ou aprimorar.

3. Em Java, qual efeito as exceções possuem sobre o fluxo de execução da pilha? Por que, em muitos casos, o próprio desenvolvedor escreve códigos que intencionalmente lançam essas exceções?
    * As exceções não tratadas caem como uma bomba em cima da pilha de execução e verifica se existe algum bloco de tratamento dentro do método da pilha que criou a bomba, se não existir tratamento o método que criou a bomba é descartado e é verificado se existe algum tratamento no método abaixo na pilha de execução, o método sempre e descartado e ele verifica se existe tratamento nos próximos métodos da pilha até chegar no método main() que sempre é o primeiro a ser chamado. Se não existir tratamento para aquela exceção em nenhum método, a execução termina e será jogada no console.
    * O desenvolvedor pode lançar intencionalmente exceções se o fluxo do programa estiver entrando num lugar errado ou com valores errados que possam gerar problemas.

4. O que são e qual(is) a(s) diferença(s) entre as classes `Throwable`, `Exception` e `RuntimeException`?
    * A classe RunTimeException só possui construtores e herda da classe Exception que também só possui construtores e herda da classe Throwable.
    * Classes que herdam de RunTimeException na verdade são exceções do tipo Unchecked que podem serem lançadas na pilha de execução.
    * Classes que herdam diretamente de Exception são exceções do tipo Checked.
    * Todas as classes que no fim herdam de Throwable podem ser jogados(throw) na pilha, mas diretamente herdada da classe Throwable temos apenas as classes Exception e Error.

5. O que são e qual(is) a(s) diferença(s) entre exceções _checked_ e _unchecked_?
    * Exceções Unchecked não são verificadas pelo compilador, as Checked são.
    * O compilador não dá importância para um método que lança uma exceção Unchecked, diferente das exceções Checked que devem ser tratadas pro compilador não reclamar de erro no código antes da execução. Uma das formas de tratar as exceções Checked é através do bloco Catch ou deixar explícito no final da assinatura do método que lança a exceção usando a keyword `throws`.
    * Exceções do tipo Unchecked são exceções que herdam de RunTimeException e exceções do tipo Checked herdam diretamente da classe Exception.

6. Qual(is) a(s) diferença(s) entre uma exceção e um erro em Java?
    * Os erros são lançados automaticamente em casos críticos durante a execução e não podem ser tratados.
    * Os erros são herdados da classe Error que herda da classe Throwable.
    * Erros são causados devido a falta de recursos do sistema e Exceções por causa do código.

7. Explique as *keywods* `try`, `catch`, `finally`, `throw` e `throws`.
    * Try: Um bloco try sempre vem acompanhado de um bloco Catch ou Finally. Se der alguma exceção dentro desse bloco, ele verifica se a exceção está sendo tratada no bloco Catch.  Ou em outros casos ele chama o bloco finally para liberar alguns recursos que possam ter sido criados ou utilizados dentro do bloco Try.
    * Catch: Sempre vem após um bloco try, serve para informar quais exceções deverão ser tratadas e como deverão ser tratadas.
    * Finally: Sempre vem após um bloco try, serve para liberar recursos ou alterar algo após a execução do bloco try.
    * Throw: Serve para jogar uma exceção em algum ponto do código. Normalmente é utilizado quando o fluxo do programa entra em lugares indesejados.
    * Throws: Serve para informar explícitamente na assinatura do método que aquele método pode lançar algum tipo de exceção do tipo Checked.

8. O que é e para que serve a interface `AutoCloseable`? Como funciona o *try with resources*?
    * A interface AutoCloseable foi criada para conseguirmos trabalhar com try with resources e serve para garantir o fechamento/liberação de recursos após o seu uso, mesmo em casos de exceções. 
    * Podemos usar a instrução try with resources em blocos try, informando qual ou quais objetos deverão ser fechados/liberados após a execução do bloco try.

9. Sobre pacotes, é correto afirmar que:
   1. É boa prática nomear os pacotes na estrutura `{site_ao_contrário}.{nome_do_projeto}`;
   2. Não devemos criar muitos pacotes, pois prejudica a navegação e legibilidade dentro do projeto;
   3. O uso de pacotes corretamente está diretamente relacionado à qualidade arquitetural de um projeto, já que eles servem para organizá-lo;

2. Explique a(s) diferença(s) entre os modificadores de acesso `private`, `default` `protected` e `public` em Java.
    * Private: visível apenas dentro da própria classe.
    * Default: visível em qualquer outra classe que esteja dentro do mesmo pacote.
    * Protected: visível em qualquer outra classe que esteja dentro do mesmo pacote e subclasses herdades.
    * Public: visível em qualquer lugar dentro de qualquer pacote.

3. Qual a ordem correta dos itens abaixo, considerando a estrutura de um arquivo Java onde há somente uma importação e uma classe vazia? (considere * como _wildcard_)

   ```java
   // 1 package

   // 2 import

   // 3 class
   ```
   2. `package *;`, `import *;` e `class * {}`;

4. Explique o que é FQN (Fully Qualified Name), sua estrutura e como evitamos ter de utilizá-lo sempre que referenciamos uma classe.
    * FQN é o nome do caminho completo em que se encontra a classe ou interface que você vai utilizar, por exemplo: java.util.ArrayList. Nesse caso estamos acessando a classe ArrayList que se encontra dentro do pacote java.util.
    Pro código não ficar com muita coisa escrita e difícil de ler/entender, podemos através da keyword `import` importar a classe ArrayList do pacote java.util ex: import java.util.ArrayList; dessa forma conseguimos acessar a classe ArrayList chamando diretamente a classe sem precisar informar o caminho onde se encontra a classe.

13. O que é, para que serve, como adquirir e como utilizar um arquivo JAR?
    * É um arquivo compactado e um formato padrão do Java para distribuir códigos compilados.
    Em cada IDE existem as diferentes formas de obter o arquivo JAR, no caso do Eclipse você precisa apenas clicar com o botão direito no seu projeto no package explorer e ir na opção "export" e informar a pasta que será criado esse arquivo JAR. Para utilizar você precisa copiar o arquivo JAR para dentro de alguma pasta do seu diretório, pode ser criado uma nova pasta para isso, em seguida você precisa clicar com o botão direito no arquivo e selecionar a opção "add to build path".

14. O que é o pacote `java.lang` e por que ele é tão essencial para qualquer código Java?
    * É um pacote que possui classes essenciais para qualquer programas, não precisa ser importado explicítamente pois já vem importado por padrão.

15. O que é uma `CharSequence` e qual(is) a(s) diferença(s) entre ela e uma `String`?
    * A classe String implementa a interface CharSequence, pois uma String é uma sequência de caracteres.
    Algumas classes implementam a interface CharSequence, dando a possibilidade dessas classes trabalharem em conjunto pois implementam a mesma interface.

16. Descreva os métodos da classe String citados abaixo:

    1. `.replace(char oldChar, char newChar);`
        * Retorna uma nova String resultante da substituições de todas as ocorrências do parâmetro oldChar encontradas nesta String pelo valor passado no parâmetro newChar.

    2. `.replaceAll(String regex, String replacement)`;
        * Retorna uma nova String substituindo o que foi encontrado através da expressão regex pelo valor passado no segundo parâmetro. 

    3. `.toLowerCase()`;
        * Converte todos os caracteres da String em maiúsculos.

    4. `.concat(String str)`;
        * Concatena a String passada por parâmetro ao final da String que chamou o método.

    5. `.contains(CharSequence s)`;
        * Retorna um booleano. True no caso da String que chamou o método conter a sequência de valores passado como parâmetro.

    6. `.equals(Object anObject)`;
        * Compara a String que chamou o método com o valor passado como parâmetro considerando letras maiúsculas e minúsculas.

    7. `.equalsIgnoreCase(String anotherString)`;
        * Compara a String que chamou o método com o valor passado como parâmetro desconsiderando letras maiúsculas e minúsculas.

    8. `.isBlank()`;
        * Retorna True se a String estiver vazia("") ou se contém só espaços em branco(" ").

    9. `.matches(String regex)`;
        * Retorna True se encontrar a expressão regex dentro da String que foi chamada.

17. Qual(is) a(s) diferença(s) entre `overriding` e `overloading` de métodos? Explique-os dando exemplos úteis da aplicação de ambos.
    * Overriding: Quando eu herdo uma classe eu estou herdando todos os seus métodos e ganho a possibilidade de sobrescrever algum método da classe pai para melhor atender as minhas necessidades. Resumidamente overriding é a possibilidade de sobrescrever o comportamento de um método que foi declarado na classe pai. Um método conhecido que sobrescrevemos bastante é o toString() que é declarado e implementado na importante classe Object, todos os objetos criados herdam dessa classe.

    * Overloading: É a possibilidade de declarar vários métodos com o mesmo nome dentro da mesma classe alterando os parâmetros que cada método pode receber. Sendo assim você pode chamar o método com o mesmo nome passando diferentes parâmetros que mais irão lhe atender em determinadas situações.

18. Todas as classes Java herdam a classe `Object`, que possui três métodos comumente sobrescritos: `.equals(Object obj)`, `.hashCode()` e `.toString()`. Explique a utilidade de cada um deles.
    * .equals(Object obj): Utilizado para comparar se a referência do objeto passado por parâmetro é a mesma do objeto que chamou o método.

    * .hashCode(): Deve ser sobrescrito sempre que o método equals for sobrescrito. Esse método devolve um inteiro que permite identificar se dois objetos são iguais ou diferentes.
    A implementação desse método na classe Objet compara apenas a referência e não os valores dos objetos. Sobrescrevendo esse método conseguimos comparar se os valores dos objetos são iguais e não as referências.

    * .toString(): Por padrão retorna uma String com o nome da classe e um hash que representa o endereço na memória que o objeto ocupa. É um método muito comum de ser sobrescrito para retornar valores atuais da classe que o chamou.

19. Qual(is) das opções expressa(m) uma sintaxe correta para criar um *array* de inteiros?
    3. `int[] inteiros = new int[]{999}`;
    4. `int[] inteiros = new int[1]`;
    5. `int[] inteiros = {999}`;

20. Por que o primeiro código abaixo exibe o valor `0` no terminal, mas o segundo produz uma exceção?

    ```java
    // código 1
    class App {
        public static void main(String... args) {
            int[] inteiros = new int[1];
            System.out.println(inteiros[0]);
        }
    }
    ```
    * Funciona porque os valores do array são inicializados automaticamente se não forem informados.


    ```java
    // código 2
    class Pessoa {
        Endereco endereco;
    }

    class Endereco {
        String cep;
    }

    class App {
        public static void main(String... args) {
            Pessoa[] pessoas = new Pessoa[1];
            System.out.println(pessoas[0].endereco.cep);
        }
    }
    ```
    * Não funciona porque ao tentar acessar o atributo .cep através do atributo .endereco da classe Pessoa, não inicializamos o atributo endereco que é do tipo referência e nunca é inicializado automaticamente.

21. Sobre *type casting*, explique:
    1. *Cast* implícito;
        * Todos os tipos em java tem um tamanho, por exemplo, o tipo long possui um tamanho de 8 bytes e o tipo int o tamanho de 4 bytes, quando uma variável do tipo long recebe uma variável do tipo int ocorre um cast implícito, pois uma variável do tipo long tem um tamanho muito maior que uma variável do tipo int, sendo assim não corre o risco de explodir a variável ao fazer essa atribuição.

    2. *Cast* explícito;
        * É quando atribuimos uma variável grande em uma variável menor, seguindo o exemplo anterior, é quando atribuimos a variável do tipo long para uma variável do tipo int, dessa forma precisamos deixar explicitamente que queremos fazer isso. Após o sinal de atribuição o código ficaria da seguinte forma: `(int)variavel_tipo_int`;  

    3. `ClassCastException`;
        * É uma exceção que ocorre quando tentamos fazer o cast explícito entre dois tipos que não possuem em sua linha de herança a mesma classe.

22. Explique o que é e como utilizar o `autoboxing` e o `unboxing`.
    * Em Java todo tipo primitivo tem uma classe Wrapper. O autoboxing é quando pegamos um valor e atribuimos para uma variável de algum tipo Wrapper por exemplo: Integer i = 0;
    * Já o unboxing é o contrário disso, é quando pegamos um tipo Wrapper e atribuimos o seu valor para uma variável de tipo primitivo, exemplo: int i = new Integer(0); 

23. É possível, no momento em que é executada uma aplicação em Java, passar argumentos para a mesma. Como isso pode ser feito e como podemos acessar esses argumentos dentro do código (no método `main()`)?
    * É possível passar argumentos para a aplicação através do terminal. Você precisa navegar até a pasta onde se encontra a classe compilada que contém o método main que você deseja passar os argumentos usando o terminal, e chamar: java `{Qualified Name da classe} {Aqui passar os argumentos}`. Para acessar os argumentos podemos criar um laço na aplicação e percorrer a variável args pegando os seus valores. 

24. Ao utilizar um `array`, o tamanho máximo do mesmo deve ser declarado. Por que isso não acontece quando utilizamos `ArrayList`? E qual é o limite do que essa estrutura pode armazenar?
    * Não é necessário definir o limite de um ArrayList porque a classe ArrayList se encarrega de criar um novo vetor com tamanho maior internamente e copiar os valores atuais para esse novo vetor.
    * O limite que um ArraList pode guardar depende da memória da máquina, você vai descobrir quando ocorrer o erro OutOfMemoryError.

25. Por que, no geral, o `ArrayList` costuma ser mais utilizado que `arrays` em Java?
    * Devido as limitações dos arrays. Um ArrayList pode aumentar dinamicamente conforme a necessidade, isso não ocorre com arrays que precisam ter seu limite declarado na sua criação, além de arrays não permitir a inserção de qualquer tipo de dados.

26. Por que sempre devemos optar pelo uso de `Generics` ao declarar um `ArrayList` (declaração no formato `ArrayList<{tipo}>`)?
    * Porque um ArrayList pode guardar qualquer tipo de dado.

27. Explique os métodos `.add(E e)` e `.contains(Object o)`, da interface `Collection`?
    * .add(E e): adiciona um item e retorna true em caso de sucesso e false se o item já existir em sua collection.
    * .contains(Object o): retorna true se sua collection conter o item passado por parâmetro.


28. Explique as interfaces `Comparator<{tipo}>` e `Comparable<{tipo}>`.
    * Comparable: Interface usada para comparar dois objetos. Ao implementar o método compareTo() você consegue definir qual o critério de comparação será feito. O retorno do método é um int.
    * Comparator: Possui o método compare() que também é usado para comparar dois objetos, o retorno do método é um int.

29. Qual(is) a(s) diferença(s) entre as interfaces `List` e `Set`?
    * Set é uma lista não ordenada e não há valores repetidos, List é uma lista ordenada e aceita valores repetidos.

30. Como funciona a implementação `HashSet`? Qual a relação dela com o método `.hashCode()`?
    * A classe HashSet implementa a interface Set, a classe não garante a ordem dos elementos inseridos, não aceita valores repetidos e é mais rápido do que List. É mais rápido porque ele "categoriza" os objetos através do hashCode. Já as Lists fazem uma busca linear, por isso é mais demorado.

31. Por que é recomendado que o *overriding* dos métodos `.equals(Object obj)` e `.hashCode()` seja realizado sempre em pares (ao sobreescrever um, o outro também deve ser sobreescrito)?
    * Porque ao chamar o .equals() é chamado o método .hashCode() da classe Object que retorna um inteiro se o hash dos objetos forem iguais.
    * Ao usar o método .equals() o método .hashCode() é chamado para validar se os objetos são iguais, o método retorna um inteiro.

32. Qual é a estrutura de uma expressão *lambda*, em Java? Explique e dê um exemplo, em código.
    * A estrutura de uma expressão lambda: `{argumento} -> {corpo}`. Existem expressões lambdas sem argumentos, nesse caso a sintaxe fica da seguinte forma: `() -> {corpo}`. Expressões lambdas são funções sem declarações, não precisa de um nome, tipo de retorno e modificador de acesso, ajuda diminuir código.
    
33. Qual é a estrutura de uma expressão *lambda* utilizando *method reference*, em Java? Explique e dê um exemplo, em código.
    * Method reference é uma expressão lambda  mais compacta, utilizado quando os lambdas são curtos e servem apenas para invocar apenas um método. Exemplo de uso sem method reference: (s -> System.out.println(s)); Com method reference ficaria: (System.out::printl); Lembrando que ele não chama o método, apenas informa qual método deverá ser chamado. 

34. Qual é a estrutura de uma `stream`, em Java? Explique e dê um exemplo, em código.
    * Stream é uma interface do Java que ajuda com algumas tarefas ao trabalhar com coleções. Você consegue pegar um stream a partir de uma coleção através da estrutura: `cursos.stream();`, sendo cursos algum tipo de coleção. 

35. O que falta no código abaixo para ser considerado um teste útil?

    ```java
    // package & imports
    class CalculadoraTest {

    	@Test
    	public void deveSomarDoisValores() {
            Calculadora calculadora = new Calculadora();
            int resultado = calculadora.somar(2, 2);
    	}

    }
    ```
    * Falta importar o package Assert e chamar o método assertEquals da classe Assert passando como parâmetro o valor que o teste deveria retornar e o valor que seu método ou regra de negócios retornou. No caso ficaria da seguinte forma ao final do método deveSomarDoisValores(): Assert.assertEquals(4, resultado);

36. Como é aplicado o TDD? Qual(is) benefício(s) ele traz e quando devemos utilizá-lo?
    * TDD é o nome de uma prática de desenvolvimento de softwares, possui 3 etapas, a primeira é desenvolver o teste para determinada funcionalidade antes de qualquer coisa, dessa forma o teste irá falhar, a segunda etapa é desenvolver a funcionalidade para passar no teste e á última etapa é refatorar a funcionalidade que você desenvolveu seguindo os princípios de clean code.

37. Quais métodos podemos utilizar para validar o lançamento de exceções em testes automatizados?
    * O método assertThrows é usado para verificar se uma exception foi lançada ao chamar um método.
    A segunda forma é chamar o método a ser testado dentro de um bloco try e verificar se está entrando no bloco catch.
