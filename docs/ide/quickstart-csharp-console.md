---
title: Tworzenie pierwszej Visual Studio konsoli w języku C# za pomocą Visual Studio aplikacji
titleSuffix: ''
description: Dowiedz się, jak utworzyć prostą Hello world konsolową w języku Visual Studio, korzystając z języka C#, krok po kroku.
ms.custom: acquisition, seodec18
ms.date: 03/23/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: quickstart
ms.devlang: vb
author: j-martens
ms.author: jmartens
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 21cab6f8fd8f4ff6a86a780774d031e60b03e780
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308002"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-c-console-app"></a>Szybki start: używanie Visual Studio do tworzenia pierwszej aplikacji konsolowej C#

W tym 5–10-minutowym wprowadzeniu do zintegrowanego środowiska projektowego (IDE) Visual Studio utworzysz prostą aplikację w języku C# uruchomioną w konsoli.

::: moniker range="vs-2017"

Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [pobierania](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) Visual Studio, aby zainstalować ją bezpłatnie.

::: moniker-end

::: moniker range="vs-2019"

Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [pobierania](https://visualstudio.microsoft.com/downloads) Visual Studio, aby zainstalować ją bezpłatnie.

::: moniker-end

::: moniker range="vs-2022"

Jeśli jeszcze nie zainstalowano programu Visual Studio 2022 (wersja zapoznawcza), przejdź do strony pobierania programu [Visual Studio 2022 Preview,](https://visualstudio.microsoft.com/vs/preview/vs2022) aby zainstalować ją bezpłatnie.

::: moniker-end

## <a name="create-a-project"></a>Tworzenie projektu

Najpierw utworzysz projekt aplikacji w języku C#. Typ projektu zawiera wszystkie potrzebne pliki szablonów, zanim jeszcze cokolwiek do ciebie dodano.

::: moniker range="vs-2017"

1. Otwórz program Visual Studio 2017.

2. Na górnym pasku menu wybierz pozycję **File** New Project > **(Plik nowy** > **projekt).**

3. W **oknie dialogowym Nowy** projekt w okienku po lewej stronie rozwiń pozycję **C#,** a następnie wybierz **pozycję .NET Core.** W środkowym okienku wybierz pozycję **Aplikacja konsoli (.NET Core).** Następnie nadaj *projektowi nazwę HelloWorld*.

   ![Szablon projektu aplikacja konsolowa (.NET Core) w oknie dialogowym Nowy projekt w Visual Studio IDE](../ide/media/new-project-csharp-dotnetcore-helloworld-console-app.png)

     Jeśli nie widzisz szablonu projektu Aplikacja konsoli **(.NET Core),** wybierz **link** Otwórz Instalator programu Visual Studio w lewym okienku okna **dialogowego Nowy** projekt.

   ![Wybierz link Otwórz Instalator programu Visual Studio w oknie dialogowym Nowy projekt](../ide/media/csharp-open-visual-studio-installer-hello-world.png)

     Uruchomienie Instalator programu Visual Studio. Wybierz obciążenie Tworzenie aplikacji dla wielu platform na platformie **.NET Core,** a następnie wybierz pozycję **Modyfikuj.**

     ![Międzyplatformowe obciążenie programowe platformy .NET Core w Instalator programu Visual Studio](../ide/media/dot-net-core-xplat-dev-workload.png)

::: moniker-end

::: moniker range=">=vs-2019"

1. Otwórz program Visual Studio.

1. W oknie uruchamiania wybierz pozycję **Utwórz nowy projekt.**

   ![Okno "Tworzenie nowego projektu"](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. W **oknie Tworzenie nowego projektu** wprowadź lub wpisz *konsolę* w polu wyszukiwania. Następnie wybierz **pozycję C#** z listy Język, a następnie wybierz pozycję **Windows** z listy Platforma. 

   Po zastosowaniu filtrów języka i platformy wybierz szablon **Aplikacja konsolowa (.NET Core),** a następnie wybierz pozycję **Dalej.**

   ![Wybieranie szablonu języka C# dla aplikacji konsoli (.NET Framework)](../get-started/csharp/media/vs-2019/csharp-create-new-project-search-console-net-core-filtered.png)

   > [!NOTE]
   > Jeśli nie widzisz szablonu **Aplikacja konsoli (.NET Core),** możesz go zainstalować w oknie Tworzenie **nowego** projektu. W **komunikacie Nie można znaleźć tego,** czego szukasz? wybierz link Zainstaluj więcej narzędzi **i** funkcji.
   >
   > ![Link "Zainstaluj więcej narzędzi i funkcji" w komunikacie "Nie można znaleźć tego, czego szukasz" w oknie "Tworzenie nowego projektu"](../get-started/media/vs-2019/not-finding-what-looking-for.png) 
   > 
   > Następnie w chmurze Instalator programu Visual Studio obciążenie tworzenie aplikacji dla wielu platform na **platformie .NET Core.**
   >
   > ![Międzyplatformowe obciążenie programowe platformy .NET Core w Instalator programu Visual Studio](./media/dot-net-core-xplat-dev-workload.png)
   >
   > Następnie wybierz przycisk **Modyfikuj** w Instalator programu Visual Studio. Może zostać wyświetlony monit o zapisanie pracy. Jeśli tak, zrób to. Następnie wybierz pozycję **Kontynuuj,** aby zainstalować obciążenie. Następnie wróć do kroku 2 w tej procedurze["Tworzenie projektu".](#create-a-project)

1. W **oknie Konfigurowanie nowego projektu** wpisz lub wprowadź *HelloWorld* w **polu Nazwa** projektu. Następnie wybierz pozycję **Utwórz**.

   ![W oknie "Konfigurowanie nowego projektu" nadaj projektowi nazwę "HelloWorld"](../get-started/csharp/media/vs-2019/csharp-name-your-helloworld-project.png)

   Visual Studio otwiera nowy projekt.
   
::: moniker-end

## <a name="create-the-application"></a>Tworzenie aplikacji

::: moniker range="vs-2017"

Po wybraniu szablonu projektu w języku C# i nazwaniu projektu Visual Studio aplikację "Hello world".

::: moniker-end

::: moniker range=">=vs-2019"

Visual Studio zawiera domyślny Hello world "Hello world" w projekcie.

::: moniker-end

(W tym celu wywołuje metodę , aby <xref:System.Console.WriteLine%2A> wyświetlić ciąg literału "Hello world!" w oknie konsoli).

   ![Wyświetlanie domyślnego Hello world kodu z szablonu](../ide/media/csharp-console-helloworld-template.png)

Po naciśnięciu **klawisza F5** możesz uruchomić program w trybie debugowania. Jednak okno konsoli jest widoczne tylko przez chwilę przed jego zamknięciem.

(To zachowanie występuje, ponieważ metoda kończy działanie po wykonaniu jej pojedynczej `Main` instrukcji, a więc kończy się aplikacja).

### <a name="add-some-code"></a>Dodawanie kodu

Dodajmy kod w celu wstrzymania aplikacji, aby okno konsoli nie było zamykane, dopóki nie naciśniesz **klawisza ENTER.**

1. Dodaj następujący kod bezpośrednio po wywołaniu <xref:System.Console.WriteLine%2A> metody :

   ```csharp
   Console.ReadLine();
   ```

1. Sprawdź, czy w edytorze kodu wygląda to następująco:

   ![Dodawanie kodu w celu wstrzymania Hello world aplikacji](../ide/media/csharp-console-helloworld-add-code.png)

## <a name="run-the-application"></a>Uruchamianie aplikacji

1. Wybierz przycisk **HelloWorld** na pasku narzędzi, aby uruchomić aplikację w trybie debugowania. (Możesz też nacisnąć klawisz **F5).**

   ![Wybierz przycisk Hello world, aby uruchomić aplikację na pasku narzędzi](../ide/media/csharp-console-hello-world-button.png)

1. Wyświetl aplikację w oknie konsoli.

   ![Okno konsoli z Hello world!](../ide/media/csharp-console-hello-world.png)

### <a name="close-the-application"></a>Zamykanie aplikacji

1. Naciśnij **klawisz ENTER,** aby zamknąć okno konsoli.

1. Zamknij okienko **Dane** wyjściowe w Visual Studio.

   ![Zamknij okienko Dane wyjściowe w Visual Studio](../ide/media/csharp-hello-world-close-output-pane.png)

1. Zamknij program Visual Studio.

## <a name="next-steps"></a>Następne kroki

Gratulujemy ukończenia tego przewodnika Szybki start! Mamy nadzieję, że nieco wiesz o języku C# i Visual Studio IDE. Aby dowiedzieć się więcej, przejdź do następujących samouczków.

> [!div class="nextstepaction"]
> [Wprowadzenie do aplikacji konsolowej C# w Visual Studio](../get-started/csharp/tutorial-console.md)
