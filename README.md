# Métricas
## Relatório de implementação e execução

### Criação do projeto

### Comandos Utilizados:
```bash
> dotnet new console
> dotnet add package System.Diagnostics.DiagnosticSource
```

### Resultado:
Adicione aqui o print do terminal mostrando a criação do projeto com `dotnet new console` e a adição do pacote `System.Diagnostics.DiagnosticSource`.

---

## Configuração inicial do ódigo

### Inserir código em `Program.cs`
```csharp
using System;
using System.Diagnostics.Metrics;
using System.Threading;

class Program
{
    static Meter s_meter = new Meter("HatCo.Store");
    static Counter<int> s_hatsSold = s_meter.CreateCounter<int>("hatco.store.hats_sold");

    static void Main(string[] args)
    {
        Console.WriteLine("Press any key to exit");
        while (!Console.KeyAvailable)
        {
            Thread.Sleep(1000); // Simula uma venda de chapéus a cada segundo
            s_hatsSold.Add(4);
        }
    }
}
```

### Resultado
Adicione aqui o print do editor com o código acima configurado no arquivo `Program.cs`.

---

## Executando o programa

```bash
> dotnet run
```

### Resultado:
Adicione aqui o print do terminal exibindo a saída do programa ao rodar o comando acima.

---

##  Monitorando métricas com `dotnet-counters`

### Instalação do `dotnet-counters`:
Caso o `dotnet-counters` não esteja instalado, utilize o seguinte comando:
```bash
> dotnet tool update -g dotnet-counters
```

### Comando para Monitorar Métricas:
Com o programa em execução, utilize o seguinte comando em outro terminal:
```bash
> dotnet-counters monitor -n metric-demo.exe --counters HatCo.Store
```

### Resultado:
Adicione aqui o print do terminal exibindo as métricas monitoradas com o `dotnet-counters`.

---

## Execução final

```bash
> dotnet run
```

### Monitoramento de Métricas:
Com o programa em execução, repita o monitoramento
```bash
> dotnet-counters monitor -n metric-demo.exe --counters HatCo.Store
```

### Resultado:
Adicione aqui o print do terminal exibindo o monitoramento atualizado, com a unidade `{hats}` exibida nas métricas.
