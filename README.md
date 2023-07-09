# O Princípio da Segregação de Interfaces (Interface Segregation Principle - ISP)

é um princípio de design de software que enfatiza a criação de interfaces coesas e específicas para cada cliente, em vez de interfaces grandes e genéricas. O objetivo do ISP é promover o desenvolvimento de interfaces mais granulares, adaptadas às necessidades de cada cliente, a fim de evitar que as classes implementem métodos que não são relevantes para elas.

O ISP é uma das diretrizes do Princípio de Responsabilidade Única (Single Responsibility Principle - SRP), que sugere que uma classe deve ter apenas uma razão para mudar. Ao seguir o ISP, as interfaces são projetadas de forma que cada cliente dependa apenas dos métodos que são relevantes para ele, evitando assim a necessidade de implementar métodos desnecessários ou não utilizados.

Quando as interfaces são grandes e genéricas, as classes que as implementam podem acabar herdando métodos desnecessários, resultando em um acoplamento indesejado. Além disso, quando uma interface abrange uma ampla gama de funcionalidades, torna-se mais difícil para os desenvolvedores entenderem e utilizarem corretamente a interface.

Ao criar interfaces coesas e específicas, o ISP ajuda a melhorar a legibilidade, a manutenção e a extensibilidade do código. Cada cliente pode depender apenas dos métodos necessários, tornando o código mais claro e reduzindo o risco de efeitos colaterais indesejados.

Aqui está um exemplo de um possível código em C# que demonstra o princípio da segregação de interfaces:

```csharp
// Interface segregada em interfaces menores e mais específicas
interface ICalculadora
{
    int Somar(int a, int b);
    int Subtrair(int a, int b);
}

interface ICalculadoraCientifica
{
    double ElevarAoQuadrado(double x);
    double CalcularRaizQuadrada(double x);
}

// Classes que implementam apenas as interfaces relevantes para elas
class CalculadoraBasica : ICalculadora
{
    public int Somar(int a, int b)
    {
        return a + b;
    }

    public int Subtrair(int a, int b)
    {
        return a - b;
    }
}

class CalculadoraAvancada : ICalculadora, ICalculadoraCientifica
{
    public int Somar(int a, int b)
    {
        return a + b;
    }

    public int Subtrair(int a, int b)
    {
        return a - b;
    }

    public double ElevarAoQuadrado(double x)
    {
        return x * x;
    }

    public double CalcularRaizQuadrada(double x)
    {
        return Math.Sqrt(x);
    }
}

class Program
{
    static void Main(string[] args)
    {
        ICalculadora calculadoraBasica = new CalculadoraBasica();
        int resultado = calculadoraBasica.Somar(2, 3);
        Console.WriteLine("Resultado da soma: " + resultado);

        ICalculadoraCientifica calculadoraAvancada = new CalculadoraAvancada();
        double quadrado = calculadoraAvancada.ElevarAoQuadrado(4);
        Console.WriteLine("Quadrado de 4: " + quadrado);
    }
}
```
Neste exemplo, temos duas interfaces segregadas: ICalculadora e ICalculadoraCientifica. A classe CalculadoraBasica implementa apenas a interface ICalculadora, pois não precisa dos métodos da interface ICalculadoraCientifica. Já a classe CalculadoraAvancada implementa ambas as interfaces, pois precisa dos métodos de ambas.

Ao utilizar interfaces segregadas, cada cliente pode depender apenas das interfaces e métodos relevantes para ele. Isso resulta em um código mais coeso e de fácil manutenção, evitando a necessidade de implementar métodos não utilizados ou desnecessários.

## Livro
![Imagem](https://m.media-amazon.com/images/I/51YTqGVOD7L._SY425_.jpg)
