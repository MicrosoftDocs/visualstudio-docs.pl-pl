---
title: Krok 2. Tworzenie pierwszej aplikacji sieci Web ASP.NET Core
description: Utwórz swoją pierwszą aplikację internetową ASP.NET Core za pomocą tego samouczka wideo i instrukcji krok po kroku.
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "77580077"
---
# <a name="step-2-create-your-first-aspnet-core-web-app"></a>Krok 2. Tworzenie pierwszej aplikacji sieci Web ASP.NET Core

Utwórz swoją pierwszą aplikację internetową ASP.NET Core za pomocą tego samouczka wideo i instrukcji krok po kroku.

_Obejrzyj ten film wideo i postępuj zgodnie z instrukcjami, aby utworzyć swoją pierwszą aplikację ASP.NET Core._

> [!VIDEO https://www.youtube.com/embed/-79RkpyFB6E]

## <a name="start-visual-studio-2019-and-create-a-new-project"></a>Uruchom program Visual Studio 2019 i Utwórz nowy projekt

Uruchom program Visual Studio 2019 i kliknij pozycję **Utwórz nowy projekt**. Wybierz **ASP.NET Core aplikacji sieci Web**. Wybierz szablon **aplikacja sieci Web** i Zachowaj domyślną nazwę projektu i lokalizację. Na liście rozwijanej z wersją ASP.NET Core wybierz **ASP.NET Core 2,1** lub **ASP.NET Core 2,2**. Kliknij przycisk **Utwórz**. Aby uzyskać bardziej szczegółowe instrukcje, zobacz [poprzednie wideo w tej serii samouczków](tutorial-aspnet-core-ef-step-01.md).

![Visual Studio 2019 wybierz opcje projektu ASP.NET Core](media/vs-2019/vs2019-choose-aspnetcore-project.png)

> [!WARNING]
> Upewnij się, że wybrano opcję ASP .NET Core 2,1 lub ASP.NET Core 2,2. Ten samouczek nie jest zgodny z ASP.NET Core 3. x.

## <a name="explore-the-new-project"></a>Eksploruj nowy projekt

W oknie Eksploratora rozwiązań po prawej stronie można wyświetlić zawartość nowego projektu. Są one opisane tutaj.

![Projekt programu Visual Studio 2019 ASP.NET Core](media/vs-2019/vs2019-solution-explorer.png)

### <a name="wwwroot"></a>wwwroot

Folder *wwwroot* zawiera pliki statyczne, które będą dostępne publicznie z aplikacji sieci Web. Zwykle zawiera arkusze stylów, pliki skryptów po stronie klienta i obrazy.

### <a name="pages"></a>Pages

Folder *strony* zawiera Razor Pages lokacji. Szablon domyślny zawiera kilka stron, w tym stronę *index. cshtml* , która jest stroną główną aplikacji, a także informacje o kontakcie i tak dalej.

### <a name="appsettingsjson"></a>appsettings.jsna

Ten plik zawiera ustawienia konfiguracji dla witryny w formacie JSON.

### <a name="programcs"></a>Program.cs

Ten plik pełni rolę punktu wejścia dla aplikacji. Gdy aplikacja jest uruchomiona, jej główna Metoda to pierwsza metoda, która jest uruchamiana i jest odpowiedzialna za utworzenie hosta sieci Web, który będzie zawierać aplikację.

### <a name="startupcs"></a>Startup.cs

Host sieci Web utworzony w *program.cs* odwołuje się do klasy uruchomieniowej i wywołuje jej metody w celu skonfigurowania aplikacji. Metoda ConfigureServices jest odpowiedzialna za konfigurowanie wszelkich usług, które będą używane przez aplikację. `Configure`Metoda konfiguruje potok żądania HTTP aplikacji. Każde żądanie przechodzi przez ten potok, współpracując z każdą częścią *oprogramowania pośredniczącego* .

### <a name="indexcshtml"></a>Index.cshtml

Strona główna witryny zawiera część znaczników HTML i jakiś kod Razor po stronie serwera. Używa Razor do określenia modelu strony, `IndexModel` który znajduje się w skojarzonym pliku *index.cshtml.cs* . Ustawia również tytuł strony przez ustawienie wartości w ViewData. Ta wartość ViewData jest odczytywana w pliku * \_ Layout. cshtml* znajdującym się w folderze udostępnionym wewnątrz folderu strony. Plik układu jest współużytkowany przez wiele Razor Pages i zapewnia typowy wygląd i działanie aplikacji. Zawartość każdej strony jest renderowana w kodzie HTML pliku układu.

## <a name="run-the-application"></a>Uruchamianie aplikacji

Teraz uruchom aplikację i wyświetl ją w przeglądarce. Aplikację można uruchomić za pomocą **klawisza Ctrl** + **F5** lub wybierając pozycję **Debuguj**  >  **Uruchom bez debugowania** z menu programu Visual Studio.

## <a name="customize-the-application"></a>Dostosowywanie aplikacji

Dodaj właściwość do pliku *index.cshtml.cs* i ustaw jej wartość na bieżący czas w programie `OnGet` obsługi:

```csharp
public string Time { get; set; }
public void OnGet()
{
    Time = DateTime.Today.ToShortTimeString();
}
```

Zastąp `<div>` zawartość w *index. cshtml* tym znacznikiem:

```cshtml
<h2>It's @Model.Time right now on the server!</h2>
```

Uruchom ponownie aplikację. Powinna zostać wyświetlona strona, która wyświetla bieżącą godzinę, ale zawsze jest Północna! To nie jest właściwe.

![Projekt programu Visual Studio 2019 ASP.NET Core w przeglądarce](media/vs-2019/vs2019-app-in-browser.png)

## <a name="debug-the-application"></a>Debugowanie aplikacji

Dodaj punkt przerwania do `OnGet` metody, do której przypiszemy wartość `Time` , a tym razem Rozpocznij debugowanie aplikacji.

Wykonywanie jest zatrzymane w wierszu i widać, że `DateTime.Today` zawiera datę, ale czas jest zawsze północny, ponieważ nie obejmuje danych czasowych. 

![Projekt programu Visual Studio 2019 ASP.NET Core w przeglądarce](media/vs-2019/vs2019-breakpoint.png)

Zmień go na Użyj `DateTime.Now` i Kontynuuj. Nowy kod dla `OnGet` powinien:

```csharp
public void OnGet()
{
    Time = DateTime.Now.ToShortTimeString();
}
```

Po przejściu do aplikacji powinien zostać wyświetlony rzeczywisty czas serwera w przeglądarce.

> [!NOTE]
> Dane wyjściowe mogą się różnić od obrazu, ponieważ format danych wyjściowych ToShortDateTimeString zależy od bieżącego ustawienia kultury. Zobacz: <xref:System.DateTime.ToShortTimeString>.

![Projekt programu Visual Studio 2019 ASP.NET Core w przeglądarce](media/vs-2019/vs2019-app-fixed-in-browser.png)

## <a name="next-steps"></a>Następne kroki

W następnym filmie wideo dowiesz się, jak dodać obsługę danych do aplikacji.

[Samouczek: Praca z danymi w aplikacji ASP.NET Core](tutorial-aspnet-core-ef-step-03.md)

## <a name="see-also"></a>Zobacz też

- [Samouczek: Tworzenie aplikacji internetowej Razor Pages przy użyciu ASP.NET Core](/aspnet/core/tutorials/razor-pages/?view=aspnetcore-2.1)
