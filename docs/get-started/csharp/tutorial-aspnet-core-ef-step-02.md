---
title: 'Krok 2: Tworzenie pierwszej ASP.NET core web app'
description: Utwórz pierwszą ASP.NET Core Web App za pomocą tego samouczka wideo i instrukcji krok po kroku.
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
ms.openlocfilehash: 1d382e83aa9672cfdcbdca64b89be79d090f2aac
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "77580077"
---
# <a name="step-2-create-your-first-aspnet-core-web-app"></a>Krok 2: Tworzenie pierwszej aplikacji sieci web ASP.NET Core

Utwórz pierwszą ASP.NET Core Web App za pomocą tego samouczka wideo i instrukcji krok po kroku.

_Obejrzyj ten film i obserwuj, aby utworzyć pierwszą aplikację ASP.NET Core._

> [!VIDEO https://www.youtube.com/embed/-79RkpyFB6E]

## <a name="start-visual-studio-2019-and-create-a-new-project"></a>Uruchamianie programu Visual Studio 2019 i tworzenie nowego projektu

Uruchom program Visual Studio 2019 i kliknij pozycję **Utwórz nowy projekt**. Wybierz **ASP.NET podstawową aplikację sieci Web**. Wybierz szablon **aplikacji sieci Web** i zachowaj domyślną nazwę i lokalizację projektu. W rozwijanej wersji ASP.NET Core wybierz **ASP.NET Core 2.1** lub **ASP.NET Core 2.2**. Kliknij przycisk **Utwórz**. Aby uzyskać bardziej szczegółowe instrukcje, zapoznaj się [z poprzednim filmem z tej serii samouczków](tutorial-aspnet-core-ef-step-01.md).

![Visual Studio 2019 Wybierz ASP.NET podstawowe opcje projektu](media/vs-2019/vs2019-choose-aspnetcore-project.png)

> [!WARNING]
> Upewnij się, że wybrałeś program ASP .NET Core 2.1 lub ASP.NET Core 2.2. Ten samouczek nie jest zgodny z ASP.NET Core 3.x.

## <a name="explore-the-new-project"></a>Poznaj nowy projekt

W oknie Eksploratora rozwiązań po prawej stronie można wyświetlić zawartość nowego projektu. Są one opisane tutaj.

![Projekt ASP.NET Core programu Visual Studio 2019](media/vs-2019/vs2019-solution-explorer.png)

### <a name="wwwroot"></a>wwwroot

Folder *wwwroot* zawiera pliki statyczne, które będą publicznie dostępne z aplikacji internetowej. Zazwyczaj przechowuje arkusze stylów, pliki skryptów po stronie klienta i obrazy.

### <a name="pages"></a>Strony

W folderze *Strony* znajdują się strony Razor Pages witryny. Szablon domyślny zawiera kilka stron, w tym *stronę Index.cshtml,* która jest stroną główną aplikacji, a także Informacje, Kontakt i tak dalej.

### <a name="appsettingsjson"></a>appsettings.json

Ten plik zawiera ustawienia konfiguracji witryny w formacie JSON.

### <a name="programcs"></a>Program.cs

Ten plik działa jako punkt wejścia dla aplikacji. Po uruchomieniu aplikacji, jego Main metoda jest pierwszą metodą, która jest uruchamiana i jest odpowiedzialny za tworzenie hosta sieci Web, który będzie zawierał aplikację.

### <a name="startupcs"></a>Startup.cs

Host sieci Web utworzony w *Program.cs* odwołuje się do klasy Startup i wywołuje jej metody konfigurowania aplikacji. ConfigureServices Metoda jest odpowiedzialny za konfigurowanie wszystkich usług, które aplikacja będzie używać. Metoda `Configure` konfiguruje potok żądania HTTP aplikacji. Każde żądanie przechodzi przez ten potok, interakcji z każdego elementu *oprogramowania* pośredniczącego, jak to robi.

### <a name="indexcshtml"></a>Index.cshtml

Strona główna witryny zawiera znaczniki HTML i kod Razor po stronie serwera. Używa Razor, aby określić `IndexModel`model strony, który znajduje się w skojarzonym *pliku Index.cshtml.cs.* Ustawia również tytuł strony, ustawiając wartość w ViewData. Ta wartość ViewData jest odczytywana w pliku * \_Layout.cshtml,* znajdującym się w folderze Udostępnione wewnątrz folderu Strony. Plik Układu jest współużytkowana przez wiele stron Razor i zapewnia wspólny wygląd i działanie aplikacji. Zawartość każdej strony jest renderowana w formacie HTML pliku Układu.

## <a name="run-the-application"></a>Uruchamianie aplikacji

Teraz uruchom aplikację i wyświetl ją w przeglądarce. Aplikację można uruchomić przy użyciu **klawisza Ctrl**+**F5** lub wybierając polecenie **Debugowanie** > **start bez debugowania** z menu programu Visual Studio.

## <a name="customize-the-application"></a>Dostosowywanie aplikacji

Dodaj właściwość do pliku *Index.cshtml.cs* i ustaw jej wartość `OnGet` na bieżący czas w programie obsługi:

```csharp
public string Time { get; set; }
public void OnGet()
{
    Time = DateTime.Today.ToShortTimeString();
}
```

Zastąp `<div>` zawartość w *pliku Index.cshtml* tym znacznikiem:

```cshtml
<h2>It's @Model.Time right now on the server!</h2>
```

Uruchom ponownie aplikację. Powinieneś zobaczyć, że strona wyświetla teraz bieżący czas, ale zawsze jest północ! To nie prawda.

![Program Visual Studio 2019 ASP.NET podstawowy projekt w przeglądarce](media/vs-2019/vs2019-app-in-browser.png)

## <a name="debug-the-application"></a>Debugowanie aplikacji

Dodaj punkt przerwania `OnGet` do metody, w której `Time` przypisujemy wartość i tym razem rozpocząć debugowanie aplikacji.

Wykonanie zatrzymuje się w wierszu `DateTime.Today` i widać, że zawiera datę, ale godzina jest zawsze północ, ponieważ nie zawiera danych czasu. 

![Program Visual Studio 2019 ASP.NET podstawowy projekt w przeglądarce](media/vs-2019/vs2019-breakpoint.png)

Zmień go, `DateTime.Now` aby używać i kontynuować wykonywanie. Nowy kod `OnGet` powinien być:

```csharp
public void OnGet()
{
    Time = DateTime.Now.ToShortTimeString();
}
```

Podczas przechodzenia do aplikacji powinien zostać wyświetlony rzeczywisty czas serwera w przeglądarce.

> [!NOTE]
> Dane wyjściowe mogą się różnić od obrazu, ponieważ format wyjściowy ToShortDateTimeString zależy od bieżącego ustawienia kultury. Zobacz: <xref:System.DateTime.ToShortTimeString>.

![Program Visual Studio 2019 ASP.NET podstawowy projekt w przeglądarce](media/vs-2019/vs2019-app-fixed-in-browser.png)

## <a name="next-steps"></a>Następne kroki

W następnym klipie wideo dowiesz się, jak dodać obsługę danych do aplikacji.

[Samouczek: Praca z danymi w aplikacji ASP.NET Core](tutorial-aspnet-core-ef-step-03.md)

## <a name="see-also"></a>Zobacz też

- [Samouczek: Tworzenie aplikacji internetowej Razor Pages z ASP.NET Core](/aspnet/core/tutorials/razor-pages/?view=aspnetcore-2.1)
