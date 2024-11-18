# Métricas
## Relatório de implementação e execução

### Criação do projeto

### Comandos Utilizados
```bash
> dotnet new console
> dotnet add package System.Diagnostics.DiagnosticSource
```

<img width="1125" alt="Captura de Tela 2024-11-17 às 19 05 27" src="https://github.com/user-attachments/assets/169ecc53-7ab0-4f4f-a696-d54f2c55d7ba">


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

<img width="1077" alt="Captura de Tela 2024-11-17 às 19 07 05" src="https://github.com/user-attachments/assets/2a26baa1-81ff-4a41-bc7c-f8544a8b27a3">

---

## Executando o programa

```bash
> dotnet run
```
<img width="389" alt="Captura de Tela 2024-11-17 às 19 12 26" src="https://github.com/user-attachments/assets/f9d28190-7905-4398-a9fe-bd9969bfea72">


---

##  Monitorando métricas 

Com o programa em execução, utilize o seguinte comando em outro terminal:
```bash
> dotnet-counters monitor -n metric-demo.exe --counters HatCo.Store
```
<img width="699" alt="Captura de Tela 2024-11-17 às 19 15 06" src="https://github.com/user-attachments/assets/a141110c-051a-4454-97d8-ed284934ca49">


---

## Execução final

```bash
> dotnet run
```

### Monitoramento de métricas
Repita o monitoramento
```bash
> dotnet-counters monitor -n metric-demo.exe --counters HatCo.Store
```
<img width="1456" alt="Captura de Tela 2024-11-17 às 20 42 03" src="https://github.com/user-attachments/assets/e533190c-7fa9-4457-a789-1ed0d96d6201">

