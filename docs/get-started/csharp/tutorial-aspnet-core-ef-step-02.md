---
title: Krok 2. Tworzenie pierwszej aplikacji sieci Web platformy ASP.NET Core
description: Utwórz swoją pierwszą aplikację sieci Web platformy ASP.NET Core z tego samouczka wideo, a instrukcje krok po kroku.
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
ms.openlocfilehash: 5e9cc4f579b5913d5be3030828cad1a799efcd72
ms.sourcegitcommit: 509fc3a324b7748f96a072d0023572f8a645bffc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58859149"
---
# <a name="step-2-create-your-first-aspnet-core-web-app"></a>Krok 2. Tworzenie pierwszej aplikacji sieci web platformy ASP.NET Core

Utwórz swoją pierwszą aplikację sieci Web platformy ASP.NET Core z tego samouczka wideo, a instrukcje krok po kroku.

_Obejrzyj ten film wideo i postępuj zgodnie z integracją programów, aby utworzyć swoją pierwszą aplikację ASP.NET Core._

> [!VIDEO https://www.youtube.com/embed/-79RkpyFB6E]

## <a name="start-visual-studio-2019-and-create-a-new-project"></a>Uruchom program Visual Studio 2019 r i Utwórz nowy projekt

Uruchom program Visual Studio 2019 r, a następnie kliknij przycisk **Tworzenie nowego projektu**. Wybierz **aplikacji sieci Web platformy ASP.NET Core**. Wybierz **aplikacji sieci Web** szablonu i zachowaj domyślne projektu, nazwę i lokalizację. Kliknij przycisk **Utwórz**. Aby uzyskać szczegółowe instrukcje, zobacz [poprzedniego wideo w tej serii samouczków](tutorial-aspnet-core-ef-step-01.md).

![Visual Studio 2019 Choose ASP.NET Core Project Options](media/vs-2019/vs2019-choose-aspnetcore-project.png)

## <a name="explore-the-new-project"></a>Poznaj nowy projekt

W oknie Eksplorator rozwiązań po prawej stronie można wyświetlić zawartość nowego projektu. Są opisane w tym miejscu.

![Visual Studio 2019 ASP.NET Core Project](media/vs-2019/vs2019-solution-explorer.png)

### <a name="wwwroot"></a>wwwroot

*Wwwroot* folder zawiera pliki statyczne, które będą znajdować się publicznie dostępny z poziomu aplikacji sieci web. Zawiera zazwyczaj arkusze stylów, pliki skryptów po stronie klienta i obrazy.

### <a name="pages"></a>Strony

*Stron* folder zawiera witrynę stron Razor. Szablon domyślny zawiera kilka stron, w tym *Index.cshtml* strona aplikacji strony głównej, a także jak około, skontaktuj się z pomocą i tak dalej.

### <a name="appsettingsjson"></a>appsettings.json

Ten plik zawiera ustawienia konfiguracji dla witryny, w formacie JSON.

### <a name="programcs"></a>Program.cs

Ten plik działa jako punkt wejścia dla aplikacji. Gdy aplikacja jest uruchamiana, jego metody Main jest pierwszą metodę, która działa i odpowiada za tworzenie hosta sieci Web, która będzie zawierała aplikację.

### <a name="startupcs"></a>Startup.cs

Host sieci Web utworzone w *Program.cs* odwołuje się do klasy uruchamiania i wywołuje jego metod, aby skonfigurować aplikację. Metoda ConfigureServices jest odpowiedzialny za konfigurowanie wszystkie usługi, których aplikacja będzie używać. `Configure` Metoda Konfiguruje potok żądań HTTP w aplikacji. Każde żądanie przechodzi przez ten potok interakcji z każdego z nich *oprogramowania pośredniczącego* tak samo jak.

### <a name="indexcshtml"></a>Index.cshtml

Strona główna witryny zawiera niektóre kod znaczników HTML i kodu Razor po stronie serwera. Użyto Razor do określenia modelu strony `IndexModel`, który znajduje się w skojarzonej *Index.cshtml.cs* pliku. Ustawia również tytuł strony, ustawiając wartość w ViewData. Ta wartość ViewData mogą być odczytywane w  *\_Layout.cshtml* pliku, znajdującego się w folderze współdzielona znajdujące się w folderze stron. Plik układu jest współużytkowany przez wiele stron Razor i udostępnia typowe wygląd i działanie aplikacji. Każda strona zawartości jest renderowany w języku HTML plik układu.

## <a name="run-the-application"></a>Uruchamianie aplikacji

Teraz uruchom aplikację i wyświetlić je w przeglądarce. Można uruchomić aplikacji przy użyciu **Ctrl**+**F5** lub wybierając **debugowania** > **Rozpocznij bez debugowania**z menu programu Visual Studio.

## <a name="customize-the-application"></a>Dostosowywanie aplikacji

Dodaj właściwość do *Index.cshtml.cs* pliku i ustawić jej wartość na bieżącą godzinę w `OnGet` procedury obsługi:

```csharp
public string Time { get; set; }
public void OnGet()
{
    Time = DateTime.Today.ToShortTimeString();
}
```

Zastąp `<div>` zawartość *Index.cshtml* o ten kod znaczników:

```cshtml
<h2>It's @Model.Time right now on the server!</h2>
```

Uruchom ponownie aplikację. Powinien zostać wyświetlony zostanie teraz wyświetlona strona bieżący czas, że zawsze oznacza północ! To nie jest odpowiednie.

![Projektu programu Visual Studio 2019 platformy ASP.NET Core w przeglądarce](media/vs-2019/vs2019-app-in-browser.png)

## <a name="debug-the-application"></a>Debugowanie aplikacji

Dodaj punkt przerwania, aby `OnGet` metoda gdzie one przypisywanie wartości do `Time` i ten czas rozpoczęcia debugowania aplikacji.

Zatrzymuje wykonywanie na wierszu, zobaczyć, że `DateTime.Today` zawiera datę, ale czas jest zawsze północy, ponieważ nie zawiera danych czasowych. 

![Projektu programu Visual Studio 2019 platformy ASP.NET Core w przeglądarce](media/vs-2019/vs2019-breakpoint.png)

Zmień go do korzystania ze `DateTime.Now` i kontynuuj wykonywanie. Nowy kod dla `OnGet` powinno być:

```csharp
public void OnGet()
{
    Time = DateTime.Now.ToShortTimeString();
}
```

Powinna zostać wyświetlona godzina używanego serwera w przeglądarce po przejściu do aplikacji.

![Projektu programu Visual Studio 2019 platformy ASP.NET Core w przeglądarce](media/vs-2019/vs2019-app-fixed-in-browser.png)

## <a name="next-steps"></a>Następne kroki

W następnym filmie wideo dowiesz się, jak dodać obsługę danych do aplikacji.

[Samouczek: Praca z danymi w aplikacji platformy ASP.NET Core](tutorial-aspnet-core-ef-step-03.md)

## <a name="see-also"></a>Zobacz także

- [Samouczek: Tworzenie aplikacji internetowej strony Razor za pomocą programu ASP.NET Core](/aspnet/core/tutorials/razor-pages/?view=aspnetcore-2.1)
