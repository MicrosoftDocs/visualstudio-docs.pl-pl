---
title: Krok 3. Praca z danymi w aplikacji platformy ASP.NET Core
description: Rozpocznij pracę z danymi przy użyciu platformy Entity Framework Core w aplikacji internetowej ASP.NET Core za pomocą tego samouczka wideo, a instrukcje krok po kroku.
ms.custom: get-started
ms.date: 03/31/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
monikerRange: vs-2019
ms.topic: tutorial
ms.devlang: CSharp
author: ardalis
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: c1d95d7621a97a36fdf737e7d3dd4f8baf713645
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62553946"
---
# <a name="step-3-work-with-data-using-entity-framework"></a>Krok 3. Praca z danymi przy użyciu platformy Entity Framework

Wykonaj następujące kroki, aby rozpocząć pracę z danymi w aplikacji internetowej ASP.NET Core przy użyciu platformy Entity Framework Core.

_Obejrzyj ten film wideo i kontynuować pracę, aby dodać dane do pierwszej aplikacji ASP.NET Core._

> [!VIDEO https://www.youtube.com/embed/dulJCwNrqhM]

## <a name="open-your-project"></a>Otwórz projekt

Jeśli wykonujesz wraz z tych klipów wideo, otwórz projekt aplikacji sieci Web, który został utworzony w poprzedniej sekcji. Jeśli zaczynasz w tym miejscu, należy utworzyć nowy projekt i wybierz polecenie **aplikacji sieci Web ASP.NET** i następnie **aplikacji sieci Web**. Pozostaw wartości domyślne pozostałych opcji.

## <a name="add-your-model"></a>Dodawanie modelu

Pierwszą rzeczą, jaką należy wykonać, aby pracować z danymi w aplikacji ASP.NET Core jest opisują, jak powinna wyglądać dane. Nazywamy się, że tworzenie *modelu* czynności wykonywane w problem chcemy rozwiązać. W świecie rzeczywistym dodamy niestandardowej logiki biznesowej do tych modeli dzięki czemu mogą zachowywać się w określony sposób i zautomatyzować zadania dla nas. W tym przykładzie zamierzamy utworzyć prosty system do śledzenia gier. Potrzebne nam klasa, która reprezentuje gry, a następnie obejmuje kilka właściwości, które chcemy Aby nagrać o tej gry, takich jak ilu graczy, może obsługiwać. Ta klasa przechodzą do nowego folderu, który utworzymy w katalogu głównym projektu sieci web o nazwie *modeli*.

```csharp
public class Game
{
    public int Id { get; set; }
    public string Title { get; set; }
    public int PublicationYear { get; set; }
    public int MinimumPlayers { get; set; }
    public int MaximumPlayers { get; set; }
}
```

## <a name="create-the-pages-to-manage-your-game-library"></a>Tworzenie stron do zarządzania biblioteką gier

Teraz możemy przystąpić do tworzenia stron, których będziemy używać do zarządzania naszej bibliotece gry. To dźwiękowych czasochłonnym zadaniem, ale jest faktycznie niezwykle proste. Najpierw należy zdecydować, gdzie w aplikacji ta funkcja powinna na żywo. Otwórz folder stron w projekcie sieci web i Dodaj nowy folder. Wywołaj go *gry*.

Teraz kliknij prawym przyciskiem myszy gry i wybierz **Dodaj** > **nowy element szkieletu**. Wybierz ze stronami Razor przy użyciu **Entity Framework (CRUD)** opcji. Zawiera CRUD "Tworzenie, odczytywanie, aktualizowanie, usuwanie" i ten szablon utworzy stron dla każdej z tych operacji (w tym stroną "wyświetlić listę wszystkich" i "Wyświetl szczegółowe informacje o jeden element" strony).

![Visual Studio 2019 platformy ASP.NET Core Dodawanie szkieletu stron](media/vs-2019/vs2019-add-scaffold.png)

Wybierz klasy modelu gier, a następnie użyj ikony "+", aby dodać nowe klasy kontekstu danych. Nadaj mu nazwę `AppDbContext`. Pozostaw pozostałe wartości domyślne, a następnie kliknij przycisk **Dodaj**.

Zobaczysz, że następujące strony Razor dodane do Twojego folderu Gry:

- Create.cshtml
- DELETE.cshtml
- Details.cshtml
- Edit.cshtml
- Index.cshtml

![Visual Studio 2019 ASP.NET Core Scaffolded Pages](media/vs-2019/vs2019-scaffolded-pages.png)

Oprócz dodawania stron w *gry* folderu, operacja tworzenia szkieletów dodano kod w celu Moje *Startup.cs* klasy. Trwa wyszukiwanie w `ConfigureServices` metody tej klasy, zostanie wyświetlony ten kod został dodany:

```csharp
services.AddDbContext<AppDbContext>(options =>
    options.UseSqlServer(Configuration.GetConnectionString("AppDbContext")));
```

Można również znaleźć `AppDbContext` parametry połączenia został dodany do projektu *appsettings.json* pliku.

Jeśli teraz uruchomić aplikację może zakończyć się niepowodzeniem, ponieważ żadna baza danych została utworzona, jeszcze. Można skonfigurować aplikację, aby automatycznie utworzyć bazę danych, jeśli to konieczne [Dodawanie kodu do pliku Program.cs](/aspnet/core/data/ef-rp/intro?view=aspnetcore-2.1&tabs=visual-studio#update-main):

```csharp
public static void Main(string[] args)
{
    var host = CreateWebHostBuilder(args).Build();

    using (var scope = host.Services.CreateScope())
    {
        var services = scope.ServiceProvider;

        try
        {
            var context = services.GetRequiredService<SchoolContext>();
            context.Database.EnsureCreated();
        }
        catch (Exception ex)
        {
            var logger = services.GetRequiredService<ILogger<Program>>();
            logger.LogError(ex, "An error occurred creating the DB.");
        }
    }

    host.Run();
}
```

Większość kodu jest tylko do obsługi błędów i zapewniają dostęp do programu EF Core `AppDbContext` zanim aplikacja zostanie uruchomiona. Wiersz ważne jest taki, który jest wyświetlany komunikat `context.Database.EnsureCreated()`, co spowoduje utworzenie bazy danych, jeśli jeszcze nie istnieje. Teraz aplikacja jest gotowa do uruchomienia.

## <a name="test-it-out"></a>Przetestować działanie

Uruchom aplikację, a następnie przejdź do `/Games` na pasku adresu. Zostanie wyświetlona strona lista jest pusta. Kliknij przycisk **Utwórz nowy** Aby dodać nowy `Game` do kolekcji. Wypełnij formularz, a następnie kliknij przycisk **Utwórz**. Powinien zostać wyświetlony go w widoku listy. Kliknij pozycję **szczegóły** do wyświetlania szczegółów pojedynczego rekordu.

Dodaj inny rekord. Możesz kliknąć pozycję *Edytuj* zmiany szczegółów pojedynczego rekordu lub **Usuń** do usunięcia go, co spowoduje wyświetlenie monitu o potwierdzenie przed faktycznie usunięcie rekordu.

![Visual Studio 2019 platformy ASP.NET Core szkieletu strony w przeglądarce](media/vs-2019/vs2019-game-list.png)

To wszystko, jaka była potrzebna, aby rozpocząć pracę z danymi w aplikacji ASP.NET Core przy użyciu programu EF Core i Visual Studio 2019 r.

## <a name="next-steps"></a>Następne kroki

W następnym filmie wideo dowiesz się, jak dodać obsługę interfejsu API sieci web do aplikacji.

[Krok 4. Udostępnianie internetowego interfejsu API z Twojej aplikacji platformy ASP.NET Core](tutorial-aspnet-core-ef-step-04.md)

## <a name="see-also"></a>Zobacz także

- [Strony razor za pomocą platformy Entity Framework Core w programie ASP.NET Core](/aspnet/core/data/ef-rp/intro?view=aspnetcore-2.1&tabs=visual-studio)
- [Strony Razor programu ASP.NET Core z programem EF Core](/aspnet/core/data/?view=aspnetcore-2.1)
