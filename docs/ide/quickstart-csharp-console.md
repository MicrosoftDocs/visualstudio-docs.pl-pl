---
title: Tworzenie pierwszej Visual Studio konsoli w języku C# przy użyciu Visual Studio
titleSuffix: ''
description: Dowiedz się, jak utworzyć prostą Hello world konsoli usługi Visual Studio użyciu języka C# i krok po kroku.
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
ms.openlocfilehash: 31759f3ae6359c9e366157012f6321c62085f8f9
ms.sourcegitcommit: 1f27f33852112702ee35fbc0c02fba37899e4cf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/15/2021
ms.locfileid: "112113219"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-c-console-app"></a>Szybki start: tworzenie Visual Studio konsoli w języku C# za pomocą usługi Visual Studio

W tym 5–10-minutowym wprowadzeniu do zintegrowanego środowiska projektowego (IDE Visual Studio) utworzysz prostą aplikację w języku C# uruchomioną w konsoli.

::: moniker range="vs-2017"

Jeśli jeszcze nie zainstalowano aplikacji Visual Studio, przejdź [](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) do strony pobierania Visual Studio, aby zainstalować ją bezpłatnie.

::: moniker-end

::: moniker range="vs-2019"

Jeśli jeszcze nie zainstalowano aplikacji Visual Studio, przejdź [](https://visualstudio.microsoft.com/downloads) do strony pobierania Visual Studio, aby zainstalować ją bezpłatnie.

::: moniker-end

## <a name="create-a-project"></a>Tworzenie projektu

Najpierw utworzysz projekt aplikacji w języku C#. Typ projektu zawiera wszystkie potrzebne pliki szablonów, zanim jeszcze cokolwiek dodano.

::: moniker range="vs-2017"

1. Otwórz program Visual Studio 2017.

2. Na górnym pasku menu wybierz pozycję **File** New Project > **(Plik nowy** > **projekt).**

3. W **oknie dialogowym Nowy** projekt w okienku po lewej stronie rozwiń pozycję **C#,** a następnie wybierz **pozycję .NET Core.** W środkowym okienku wybierz pozycję **Aplikacja konsoli (.NET Core).** Następnie nadaj *projektowi nazwę HelloWorld*.

   ![Szablon projektu aplikacja konsolowa (.NET Core) w oknie dialogowym Nowy projekt w Visual Studio IDE](../ide/media/new-project-csharp-dotnetcore-helloworld-console-app.png)

     Jeśli nie widzisz szablonu projektu Aplikacja konsoli **(.NET Core),** wybierz link **Otwórz** Instalator programu Visual Studio w lewym okienku **okna dialogowego Nowy** projekt.

   ![Wybierz link Otwórz Instalator programu Visual Studio w oknie dialogowym Nowy projekt](../ide/media/csharp-open-visual-studio-installer-hello-world.png)

     Ta Instalator programu Visual Studio uruchamia się. Wybierz obciążenie **Tworzenie aplikacji dla wielu platform na platformie .NET Core,** a następnie wybierz pozycję **Modyfikuj.**

     ![Międzyplatformowe obciążenie programowe platformy .NET Core w chmurze Instalator programu Visual Studio](../ide/media/dot-net-core-xplat-dev-workload.png)

::: moniker-end

::: moniker range="vs-2019"

1. Otwórz Visual Studio 2019 r.

1. W oknie uruchamiania wybierz **pozycję Utwórz nowy projekt.**

   ![Okno "Tworzenie nowego projektu"](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. W **oknie Tworzenie nowego projektu** wprowadź lub wpisz *console* w polu wyszukiwania. Następnie wybierz **pozycję C#** z listy Język, a następnie wybierz pozycję **Windows** z listy Platforma. 

   Po zastosowaniu filtrów języka i platformy wybierz szablon **Aplikacja konsolowa (.NET Core),** a następnie wybierz pozycję **Dalej.**

   ![Wybierz szablon języka C# dla aplikacji konsolowej (.NET Framework)](../get-started/csharp/media/vs-2019/csharp-create-new-project-search-console-net-core-filtered.png)

   > [!NOTE]
   > Jeśli nie widzisz szablonu **Aplikacja konsoli (.NET Core),** możesz go zainstalować w oknie **Tworzenie nowego** projektu. W **komunikacie Nie** można znaleźć tego, czego szukasz? wybierz link Zainstaluj **więcej narzędzi i** funkcji.
   >
   > ![Link "Zainstaluj więcej narzędzi i funkcji" w komunikacie "Nie można znaleźć tego, czego szukasz" w oknie "Tworzenie nowego projektu"](../get-started/media/vs-2019/not-finding-what-looking-for.png) 
   > 
   > Następnie w chmurze Instalator programu Visual Studio obciążenie Tworzenie aplikacji dla wielu platform dla **platformy .NET Core.**
   >
   > ![Międzyplatformowe obciążenie programowe platformy .NET Core w chmurze Instalator programu Visual Studio](./media/dot-net-core-xplat-dev-workload.png)
   >
   > Następnie wybierz przycisk **Modyfikuj** w Instalator programu Visual Studio. Może zostać wyświetlony monit o zapisanie pracy. Jeśli tak, zrób to. Następnie wybierz pozycję **Kontynuuj,** aby zainstalować obciążenie. Następnie wróć do kroku 2 w procedurze["Tworzenie projektu".](#create-a-project)

1. W **oknie Configure your new project (Konfigurowanie** nowego projektu) wpisz lub wprowadź *HelloWorld* w **polu Project name (Nazwa** projektu). Następnie wybierz pozycję **Utwórz.**

   ![W oknie "Konfigurowanie nowego projektu" nadaj projektowi nazwę "HelloWorld"](../get-started/csharp/media/vs-2019/csharp-name-your-helloworld-project.png)

   Visual Studio otworzy nowy projekt.
   
::: moniker-end

## <a name="create-the-application"></a>Tworzenie aplikacji

::: moniker range="vs-2017"

Po wybraniu szablonu projektu języka C# i nazwie projektu Visual Studio aplikację "Hello world".

::: moniker-end

::: moniker range="vs-2019"

Visual Studio zawiera domyślny kod Hello world "Hello world" w projekcie.

::: moniker-end

(W tym celu wywołuje metodę <xref:System.Console.WriteLine%2A> , aby wyświetlić ciąg literału "Hello world!" w oknie konsoli).

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

1. Zamknij okienko **Dane wyjściowe** w Visual Studio.

   ![Zamknij okienko Dane wyjściowe w Visual Studio](../ide/media/csharp-hello-world-close-output-pane.png)

1. Zamknij program Visual Studio.

## <a name="next-steps"></a>Następne kroki

Gratulujemy ukończenia tego przewodnika Szybki start! Mamy nadzieję, że wiesz już trochę o języku C# i Visual Studio IDE. Aby dowiedzieć się więcej, przejdź do następujących samouczków.

> [!div class="nextstepaction"]
> [Wprowadzenie do aplikacji konsolowej C# w programie Visual Studio](../get-started/csharp/tutorial-console.md)
