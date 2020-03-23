---
title: 'Krok 3: Praca z danymi w aplikacji ASP.NET Core'
description: Rozpocznij pracę z danymi przy użyciu entity framework core w aplikacji ASP.NET Core Web App z tego samouczka wideo i instrukcje krok po kroku.
ms.custom: get-started
ms.date: 03/31/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
monikerRange: vs-2019
ms.topic: tutorial
ms.devlang: CSharp
author: ardalis
ms.author: ornella
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: cef0db7e5615d08fb5b22c38604a24124c853ebd
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "77580068"
---
# <a name="step-3-work-with-data-using-entity-framework"></a>Krok 3: Praca z danymi przy użyciu entity framework

Wykonaj następujące kroki, aby rozpocząć pracę z danymi przy użyciu entity framework core w aplikacji ASP.NET Core Web App.

_Obejrzyj ten film i obserwuj, aby dodać dane do pierwszej aplikacji ASP.NET Core._

> [!VIDEO https://www.youtube.com/embed/dulJCwNrqhM]

## <a name="open-your-project"></a>Otwórz swój projekt

Jeśli obserwujesz te klipy wideo, otwórz projekt aplikacji sieci Web utworzony w poprzedniej sekcji. Jeśli zaczynasz tutaj, musisz utworzyć nowy projekt i wybrać **ASP.NET aplikacji sieci Web,** a następnie **aplikacji sieci Web**. Pozostałe opcje pozostaw jako domyślne.

## <a name="add-your-model"></a>Dodawanie modelu

Pierwszą rzeczą, którą musisz zrobić, aby pracować z danymi w aplikacji ASP.NET Core jest opisanie, jak powinny wyglądać dane. Nazywamy to stworzeniem *modelu* rzeczy związanych z problemem, który staramy się rozwiązać. W rzeczywistych aplikacjach dodamy niestandardową logikę biznesową do tych modeli, aby mogły zachowywać się w określony sposób i automatyzować zadania dla nas. W tym przykładzie stworzymy prosty system śledzenia gier planszowych. Potrzebujemy klasy, która reprezentuje grę i zawiera pewne właściwości, które możemy chcieć nagrać na temat tej gry, na przykład liczbę graczy, których może obsługiwać. Ta klasa przejdzie do nowego folderu, który utworzymy w katalogu głównym projektu sieci web o nazwie *Models*.

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

Teraz jesteśmy gotowi do tworzenia stron, których użyjemy do zarządzania naszą biblioteką gier. To może wydawać się trudne, ale to naprawdę niezwykle łatwe. Najpierw musimy zdecydować, gdzie w naszej aplikacji ta funkcja powinna żyć. Otwórz folder Strony w projekcie internetowym i dodaj tam nowy folder. Nazwijmy to *Gry*.

Teraz kliknij prawym przyciskiem myszy na Gry i wybierz **dodaj** > **nowy element rusztowania**. Wybierz opcję Razor Pages using **Entity Framework (CRUD).** CRUD oznacza "Tworzenie, czytanie, aktualizowanie, usuwanie" i ten szablon utworzy strony dla każdej z tych operacji (w tym "lista wszystkich" strony i "zobacz szczegóły jednego elementu" strony).

![Visual Studio 2019 ASP.NET core Dodaj strony szkieletu](media/vs-2019/vs2019-add-scaffold.png)

Wybierz klasę modelu gry i użyj ikony "+", aby dodać nową klasę kontekstu danych. Nadaj jej nazwę `AppDbContext`. Pozostaw resztę jako domyślną i kliknij przycisk **Dodaj**.

Do folderu Gry zostaną dodane następujące strony Razor:

- Utwórz.cshtml
- Usuń plik cshtml
- Szczegóły.cshtml
- Edytuj.cshtml
- Index.cshtml

![Visual Studio 2019 ASP.NET podstawowych stronach szkieletu](media/vs-2019/vs2019-scaffolded-pages.png)

Oprócz dodawania stron w folderze *Gry,* operacja rusztowania dodał kod do *mojej* Startup.cs klasy. Patrząc w `ConfigureServices` metodzie w tej klasie zobaczysz ten kod został dodany:

```csharp
services.AddDbContext<AppDbContext>(options =>
    options.UseSqlServer(Configuration.GetConnectionString("AppDbContext")));
```

Znajdziesz również ciąg `AppDbContext` połączenia został dodany do pliku *appsettings.json* projektu.

Jeśli uruchomisz aplikację teraz, może zakończyć się niepowodzeniem, ponieważ nie utworzono jeszcze żadnej bazy danych. Aplikację można skonfigurować tak, aby w razie potrzeby automatycznie tworzyła bazę danych, [dodając kod do Program.cs:](/aspnet/core/data/ef-rp/intro?view=aspnetcore-2.1&tabs=visual-studio#update-main)

```csharp
public static void Main(string[] args)
{
    var host = CreateWebHostBuilder(args).Build();

    using (var scope = host.Services.CreateScope())
    {
        var services = scope.ServiceProvider;

        try
        {
            var context = services.GetRequiredService<AppDbContext>();
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

Aby rozwiązać nazwy typów w poprzednim kodzie, dodaj następujące instrukcje, aby *Program.cs* na końcu istniejącego bloku przy użyciu instrukcji:

```csharp
using Microsoft.Extensions.DependencyInjection;
using WebApplication1.Models;
```

Pamiętaj, aby używać nazwy projektu zamiast WebApplication1 w kodzie.

Większość kodu jest tylko do obsługi błędów i `AppDbContext` zapewnić dostęp do ef core przed uruchomieniem aplikacji. Ważną linią jest ten, `context.Database.EnsureCreated()`który mówi , który utworzy bazę danych, jeśli jeszcze nie istnieje. Teraz aplikacja jest gotowa do uruchomienia.

## <a name="test-it-out"></a>Testowanie działania

Uruchom aplikację i `/Games` przejdź do paska adresu. Zostanie wyświetlona pusta strona listy. Kliknij **przycisk Utwórz nowy,** aby dodać nowy `Game` plik do kolekcji. Wypełnij formularz i kliknij przycisk **Utwórz**. Powinien być widoczny w widoku listy. Kliknij **szczegóły,** aby zobaczyć szczegóły pojedynczego rekordu.

Dodaj kolejny rekord. Możesz kliknąć przycisk *Edytuj,* aby zmienić szczegóły rekordu, lub **usuń** go, co spowoduje wyświetlenie monitu o potwierdzenie, zanim faktycznie usunie rekord.

![Visual Studio 2019 ASP.NET podstawowych stronach szkieletowych w przeglądarce](media/vs-2019/vs2019-game-list.png)

To wszystko, czego potrzeba, aby rozpocząć pracę z danymi w aplikacji core ASP.NET przy użyciu EF Core i Visual Studio 2019.

## <a name="next-steps"></a>Następne kroki

W następnym klipie wideo dowiesz się, jak dodać obsługę interfejsu API w sieci Web do aplikacji.

[Krok 4: Udostępnianie internetowego interfejsu API z aplikacji ASP.NET Core](tutorial-aspnet-core-ef-step-04.md)

## <a name="see-also"></a>Zobacz też

- [Strony brzytwy z entity framework core w ASP.NET Core](/aspnet/core/data/ef-rp/intro?view=aspnetcore-2.1&tabs=visual-studio)
- [ASP.NET podstawowych stron maszynki do golenia z EF Core](/aspnet/core/data/?view=aspnetcore-2.1)
