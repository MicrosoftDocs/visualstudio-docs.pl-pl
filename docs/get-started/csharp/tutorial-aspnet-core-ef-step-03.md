---
title: Krok 3. Praca z danymi w aplikacji ASP.NET Core
description: Rozpocznij pracę z danymi przy użyciu Entity Framework Core w aplikacji internetowej ASP.NET Core z tym samouczkiem wideo i instrukcjami krok po kroku.
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
ms.openlocfilehash: 9d01d991daf5c24c02b8cd4976663a9399b251cc
ms.sourcegitcommit: a778dffddb05d2f0f15969eadaf9081c9b466196
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2020
ms.locfileid: "91780970"
---
# <a name="step-3-work-with-data-using-entity-framework"></a>Krok 3. Współpraca z danymi przy użyciu Entity Framework

Wykonaj następujące kroki, aby rozpocząć pracę z danymi przy użyciu Entity Framework Core w aplikacji ASP.NET Core sieci Web.

_Obejrzyj ten film wideo i postępuj zgodnie z instrukcjami, aby dodać dane do pierwszej aplikacji ASP.NET Core._

> [!VIDEO https://www.youtube.com/embed/dulJCwNrqhM]

## <a name="open-your-project"></a>Otwórz projekt

Jeśli korzystasz z tych filmów wideo, Otwórz projekt aplikacji sieci Web utworzony w poprzedniej sekcji. Jeśli zaczynasz tutaj, musisz utworzyć nowy projekt i wybrać **ASP.NET aplikację sieci Web** , a następnie **aplikację sieci Web**. Pozostaw resztę opcji jako domyślne.

## <a name="add-your-model"></a>Dodaj model

Pierwszym krokiem, który należy wykonać w celu pracy z danymi w aplikacji ASP.NET Core, jest określenie, jak powinny wyglądać dane. Dzwonimy, aby utworzyć *model* rzeczy należących do problemu, który próbujesz rozwiązać. W świecie rzeczywistym aplikacje dodamy do tych modeli niestandardową logikę biznesową, dzięki czemu będą one działać w określony sposób i automatyzują zadania dla nas. Na potrzeby tego przykładu tworzymy prosty system do śledzenia gier planszowych. Potrzebujemy klasy, która reprezentuje grę i zawiera pewne właściwości, które możemy chcieć nagrać na temat tej gry, jak na przykład, ile graczy może obsłużyć. Ta klasa przejdzie do nowego folderu, który zostanie utworzony w katalogu głównym projektu sieci Web o nazwie *modele*.

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

Teraz jesteśmy gotowi do utworzenia stron, które będą używane do zarządzania naszą biblioteką gier. Może to być spowodowane zniechęcająceem, ale jest to bardzo proste. Najpierw musimy zdecydować, gdzie w naszej aplikacji powinna się znajdować ta funkcja. Otwórz folder strony w projekcie sieci Web i Dodaj do niego nowy folder. Wywołaj *gry*IT.

Teraz kliknij prawym przyciskiem myszy pozycję gry i wybierz polecenie **Dodaj**  >  **nowy element szkieletowy**. Wybierz opcję Razor Pages przy użyciu **Entity Framework (CRUD)** . CRUD oznacza "Tworzenie, odczytywanie, aktualizowanie, usuwanie" i ten szablon spowoduje utworzenie stron dla każdej z tych operacji (w tym strony "Wyświetl wszystko" i "Wyświetlanie szczegółów jednego elementu").

![Program Visual Studio 2019 ASP.NET Core Dodawanie szkieletu stron](media/vs-2019/vs2019-add-scaffold.png)

Wybierz klasę modelu gier i użyj ikony "+", aby dodać nową klasę kontekstu danych. Nadaj jej nazwę `AppDbContext`. Pozostaw resztę jako domyślne i kliknij przycisk **Dodaj**.

Zostanie wyświetlony następujący Razor Pages dodany do folderu gry:

- Create. cshtml
- Usuń. cshtml
- Details. cshtml
- Edytuj. cshtml
- Index.cshtml

![ASP.NET Core strony szkieletowe programu Visual Studio 2019](media/vs-2019/vs2019-scaffolded-pages.png)

Oprócz dodawania stron w folderze *gry* , operacja tworzenia szkieletu dodaliśmy kod do klasy my *Startup.cs* . W `ConfigureServices` metodzie w tej klasie zobaczysz, że ten kod został dodany:

```csharp
services.AddDbContext<AppDbContext>(options =>
    options.UseSqlServer(Configuration.GetConnectionString("AppDbContext")));
```

Należy również znaleźć `AppDbContext` Parametry połączenia, które zostały dodane do *appsettings.jsprojektu na* pliku.

Jeśli aplikacja zostanie uruchomiona teraz, może się nie powieść, ponieważ nie została jeszcze utworzona baza danych. W razie potrzeby można skonfigurować aplikację do automatycznego tworzenia bazy danych, [dodając kod do program.cs](/aspnet/core/data/ef-rp/intro?view=aspnetcore-2.1&tabs=visual-studio&preserve-view=true#update-main):

```csharp
public static void Main(string[] args)
{
    var host = CreateWebHostBuilder(args).Build();

    using (var scope = host.Services.CreateScope())
    {
        var services = scope.ServiceProvider;

        try
        {
            var context = services.GetRequiredService<Data.AppDbContext>();
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

Aby rozwiązać elementy TypeName w poprzednim kodzie, należy dodać następujące instrukcje using do *program.cs* na końcu istniejącego bloku instrukcji using:

```csharp
using Microsoft.Extensions.DependencyInjection;
using WebApplication1.Models;
```

Upewnij się, że używasz nazwy projektu zamiast WebApplication1 w kodzie.

Większość kodu jest tylko w przypadku obsługi błędów i zapewnienia dostępu do EF Core `AppDbContext` przed uruchomieniem aplikacji. Ważnym wierszem jest to, co mówi `context.Database.EnsureCreated()` , co spowoduje utworzenie bazy danych, jeśli jeszcze nie istnieje. Teraz aplikacja jest gotowa do uruchomienia.

## <a name="test-it-out"></a>Testowanie działania

Uruchom aplikację i przejdź do `/Games` programu na pasku adresu. Zostanie wyświetlona pusta strona listy. Kliknij przycisk **Utwórz nowy** , aby dodać nowy element `Game` do kolekcji. Wypełnij formularz i kliknij przycisk **Utwórz**. Powinien on zostać wyświetlony w widoku listy. Kliknij pozycję **szczegóły** , aby wyświetlić szczegóły pojedynczego rekordu.

Dodaj inny rekord. Możesz kliknąć przycisk *Edytuj* , aby zmienić szczegóły rekordu, lub **usunąć** , aby usunąć go, co spowoduje wyświetlenie monitu o potwierdzenie przed faktycznym usunięciem rekordu.

![ASP.NET Core strony szkieletowe w przeglądarce programu Visual Studio 2019](media/vs-2019/vs2019-game-list.png)

To wszystko miało na celu rozpoczęcie pracy z danymi w aplikacji ASP.NET Core przy użyciu EF Core i programu Visual Studio 2019.

## <a name="next-steps"></a>Następne kroki

W następnym filmie wideo dowiesz się, jak dodać obsługę interfejsu API sieci Web do aplikacji.

[Krok 4. Udostępnianie internetowego interfejsu API z poziomu aplikacji ASP.NET Core](tutorial-aspnet-core-ef-step-04.md)

## <a name="see-also"></a>Zobacz też

- [Razor Pages z Entity Framework Core w ASP.NET Core](/aspnet/core/data/ef-rp/intro?view=aspnetcore-2.1&tabs=visual-studio&preserve-view=true)
- [ASP.NET Core Razor Pages z EF Core](/aspnet/core/data/?view=aspnetcore-2.1&preserve-view=true)
