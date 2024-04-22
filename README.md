# Criando-um-APP-Simples-de-Cadastro-de-S-ries-em-.NET

Criar um aplicativo de cadastro de séries em .NET é uma ótima maneira de praticar a programação orientada a objetos. Aqui está um exemplo de como você pode começar a estruturar seu aplicativo:

```csharp
using System;
using System.Collections.Generic;

namespace CadastroDeSeries
{
    class Program
    {
        static SerieRepositorio repositorio = new SerieRepositorio();
        static void Main(string[] args)
        {
            string opcaoUsuario = ObterOpcaoUsuario();

            while (opcaoUsuario.ToUpper() != "X")
            {
                switch (opcaoUsuario)
                {
                    case "1":
                        ListarSeries();
                        break;
                    case "2":
                        InserirSerie();
                        break;
                    case "3":
                        // ... adicione mais opções conforme necessário
                        break;
                    default:
                        throw new ArgumentOutOfRangeException();
                }

                opcaoUsuario = ObterOpcaoUsuario();
            }
        }

        private static void ListarSeries()
        {
            // ... implementação para listar séries
        }

        private static void InserirSerie()
        {
            // ... implementação para inserir nova série
        }

        private static string ObterOpcaoUsuario()
        {
            Console.WriteLine();
            Console.WriteLine("Informe a opção desejada:");
            Console.WriteLine("1- Listar séries");
            Console.WriteLine("2- Inserir nova série");
            Console.WriteLine("3- Atualizar série");
            // ... adicione mais opções conforme necessário
            Console.WriteLine("X- Sair");
            Console.WriteLine();

            string opcaoUsuario = Console.ReadLine().ToUpper();
            Console.WriteLine();
            return opcaoUsuario;
        }
    }
}
```

Este é apenas um esqueleto básico. Você precisará implementar os métodos `ListarSeries`, `InserirSerie`, e outros métodos que achar necessário. Além disso, você vai querer criar classes para representar suas séries e um repositório para gerenciar a coleção de séries.

Lembre-se de aplicar os princípios de orientação a objetos, como encapsulamento, herança e polimorfismo, conforme você expande seu projeto. 

Aqui está um exemplo de uma classe em C# que você poderia usar para representar uma série no seu aplicativo:

```csharp
using System;

namespace CadastroDeSeries
{
    public enum Genero
    {
        Acao = 1,
        Aventura = 2,
        Comedia = 3,
        Documentario = 4,
        Drama = 5,
        Espionagem = 6,
        Faroeste = 7,
        Fantasia = 8,
        Ficcao_Cientifica = 9,
        Musical = 10,
        Romance = 11,
        Suspense = 12,
        Terror = 13
    }

    public class Serie
    {
        public int Id { get; private set; }
        public Genero Genero { get; private set; }
        public string Titulo { get; private set; }
        public string Descricao { get; private set; }
        public int Ano { get; private set; }
        public bool Excluido { get; private set; }

        public Serie(int id, Genero genero, string titulo, string descricao, int ano)
        {
            this.Id = id;
            this.Genero = genero;
            this.Titulo = titulo;
            this.Descricao = descricao;
            this.Ano = ano;
            this.Excluido = false;
        }

        public void Excluir()
        {
            this.Excluido = true;
        }

        public override string ToString()
        {
            return $"Gênero: {this.Genero}\nTítulo: {this.Titulo}\nDescrição: {this.Descricao}\nAno de Início: {this.Ano}\nExcluído: {(this.Excluido ? "Sim" : "Não")}";
        }
    }
}
```

Essa classe `Serie` possui propriedades para armazenar informações como gênero, título, descrição, ano e um status para verificar se a série foi excluída. O método `Excluir` é usado para marcar uma série como excluída sem removê-la fisicamente da coleção. O método `ToString` é sobrescrito para fornecer uma string formatada com as informações da série.

Você também pode notar o uso de um `enum` para os gêneros, o que ajuda a manter o código organizado e facilita a manutenção.

https://github.com/elizarp/dio-dotnet-poo-lab-2
