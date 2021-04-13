---
title: Tworzenie pierwszej aplikacji konsolowej w języku C# za pomocą programu Visual Studio
titleSuffix: ''
description: Dowiedz się, jak utworzyć prostą aplikację konsolową Hello world w programie Visual Studio przy użyciu języka C#, krok po kroku.
ms.custom: seodec18
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
ms.openlocfilehash: 0f51e3e6617578236d31090b23e8cb7c661d6043
ms.sourcegitcommit: 6d88913a8b5a9e5eda01d3f95205b4d138f440f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2021
ms.locfileid: "107296797"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-c-console-app"></a>Szybki Start: Tworzenie pierwszej aplikacji konsolowej w języku C# za pomocą programu Visual Studio

W tym 5-10 minutowym wprowadzeniu do zintegrowanego środowiska programistycznego (IDE) programu Visual Studio utworzysz prostą aplikację w języku C#, która działa w konsoli programu.

::: moniker range="vs-2017"

Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) , aby zainstalować ją bezpłatnie.

::: moniker-end

::: moniker range="vs-2019"

Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/downloads) , aby zainstalować ją bezpłatnie.

::: moniker-end

## <a name="create-a-project"></a>Tworzenie projektu

Najpierw utworzysz projekt aplikacji w języku C#. Typ projektu jest dostarczany ze wszystkimi plikami szablonu, które będą potrzebne, zanim będzie można nawet dodać wszystko.

::: moniker range="vs-2017"

1. Otwórz program Visual Studio 2017.

2. Na górnym pasku menu wybierz pozycję **plik** > **Nowy** > **projekt**.

3. W oknie dialogowym **Nowy projekt** w okienku po lewej stronie rozwiń pozycję **C#**, a następnie wybierz pozycję **.NET Core**. W środkowym okienku wybierz pozycję **aplikacja konsoli (.NET Core)**. Następnie nadaj nazwę projekt *HelloWorld*.

   ![Szablon projektu aplikacji konsolowej (.NET Core) w oknie dialogowym Nowy projekt w programie Visual Studio IDE](../ide/media/new-project-csharp-dotnetcore-helloworld-console-app.png)

     Jeśli szablon projektu **aplikacja konsoli (.NET Core)** nie jest widoczny, wybierz link **Otwórz Instalator programu Visual Studio** w lewym okienku okna dialogowego **Nowy projekt** .

   ![Wybierz łącze Otwórz Instalator programu Visual Studio w oknie dialogowym Nowy projekt](../ide/media/csharp-open-visual-studio-installer-hello-world.png)

     Zostanie uruchomiona Instalator programu Visual Studio. Wybierz obciążenie dla **wielu platform platformy .NET Core** , a następnie wybierz **Modyfikuj**.

     ![Obciążenie Międzyplatformowe dla platformy .NET Core w Instalator programu Visual Studio](../ide/media/dot-net-core-xplat-dev-workload.png)

::: moniker-end

::: moniker range="vs-2019"

1. Otwórz program Visual Studio 2019.

1. W oknie uruchamiania wybierz pozycję **Utwórz nowy projekt**.

   ![Okno "Tworzenie nowego projektu"](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. W oknie **Tworzenie nowego projektu** w polu wyszukiwania wpisz lub wpisz *Console* . Następnie wybierz pozycję **C#** z listy język, a następnie wybierz pozycję **Windows** z listy platform. 

   Po zastosowaniu filtrów języka i platformy wybierz szablon **Aplikacja konsolowa (.NET Core)** , a następnie wybierz przycisk **dalej**.

   ![Wybieranie szablonu C# dla aplikacji konsolowej (.NET Framework)](../get-started/csharp/media/vs-2019/csharp-create-new-project-search-console-net-core-filtered.png)

   > [!NOTE]
   > Jeśli nie widzisz szablonu **Aplikacja konsolowa (.NET Core)** , możesz go zainstalować z okna **Utwórz nowy projekt** . W obszarze **nie można znaleźć tego, czego szukasz?** komunikat wybierz łącze **Zainstaluj więcej narzędzi i funkcji** .
   >
   > ![Link "Zainstaluj więcej narzędzi i funkcji" z komunikatu "nie można odnaleźć szukanego elementu" w oknie "Tworzenie nowego projektu"](../get-started/media/vs-2019/not-finding-what-looking-for.png) 
   > 
   > Następnie w Instalator programu Visual Studio wybierz obciążenie dla **wielu platform platformy .NET Core** .
   >
   > ![Obciążenie Międzyplatformowe dla platformy .NET Core w Instalator programu Visual Studio](./media/dot-net-core-xplat-dev-workload.png)
   >
   > Następnie wybierz przycisk **Modyfikuj** w Instalator programu Visual Studio. Może zostać wyświetlony monit o zapisanie pracy; Jeśli tak, zrób to. Następnie wybierz pozycję **Kontynuuj** , aby zainstalować obciążenie. Następnie wróć do kroku 2 w tej procedurze "[Create a Project](#create-a-project)".

1. W oknie **Konfigurowanie nowego projektu** wpisz lub wprowadź *HelloWorld* w polu **Nazwa projektu** . Następnie wybierz pozycję **Utwórz**.

   ![w oknie "Konfigurowanie nowego projektu" Nazwij swój projekt "HelloWorld"](../get-started/csharp/media/vs-2019/csharp-name-your-helloworld-project.png)

   Program Visual Studio otwiera nowy projekt.
   
::: moniker-end

## <a name="create-the-application"></a>Tworzenie aplikacji

::: moniker range="vs-2017"

Po wybraniu szablonu projektu C# i nazwij projekt, program Visual Studio tworzy prostą aplikację "Hello world".

::: moniker-end

::: moniker range="vs-2019"

Program Visual Studio zawiera domyślny kod "Hello world" w projekcie.

::: moniker-end

(W tym celu wywołuje <xref:System.Console.WriteLine%2A> metodę w celu wyświetlenia ciągu literału "Hello World!" w oknie konsoli).

   ![Wyświetl domyślny kod Hello world z szablonu](../ide/media/csharp-console-helloworld-template.png)

Po naciśnięciu klawisza **F5** można uruchomić program w trybie debugowania. Jednak okno konsoli jest widoczne tylko przez chwilę przed zamknięciem.

(Takie zachowanie ma miejsce `Main` , ponieważ metoda kończy się po wykonaniu jednej instrukcji i dlatego aplikacja kończy się).

### <a name="add-some-code"></a>Dodaj kod

Dodajmy kod w celu wstrzymania aplikacji, aby okno konsoli nie było zamykane do momentu naciśnięcia klawisza **Enter**.

1. Dodaj następujący kod bezpośrednio po wywołaniu <xref:System.Console.WriteLine%2A> metody:

   ```csharp
   Console.ReadLine();
   ```

1. Sprawdź, czy wygląda to w edytorze kodu:

   ![Dodawanie kodu w celu wstrzymania aplikacji Hello world](../ide/media/csharp-console-helloworld-add-code.png)

## <a name="run-the-application"></a>Uruchamianie aplikacji

1. Wybierz przycisk **HelloWorld** na pasku narzędzi, aby uruchomić aplikację w trybie debugowania. (Lub naciśnij klawisz **F5**).

   ![Wybierz przycisk Hello world, aby uruchomić aplikację z paska narzędzi](../ide/media/csharp-console-hello-world-button.png)

1. Wyświetl aplikację w oknie konsoli.

   ![Okno konsoli zawierające Hello world!](../ide/media/csharp-console-hello-world.png)

### <a name="close-the-application"></a>Zamknij aplikację

1. Naciśnij klawisz **Enter** , aby zamknąć okno konsoli.

1. Zamknij okienko **danych wyjściowych** w programie Visual Studio.

   ![Zamknij okienko danych wyjściowych w programie Visual Studio](../ide/media/csharp-hello-world-close-output-pane.png)

1. Zamknij program Visual Studio.

## <a name="next-steps"></a>Następne kroki

Gratulujemy zakończenia tego przewodnika Szybki Start! Mamy nadzieję, że uczysz się nieco na temat języka C# i środowiska IDE programu Visual Studio. Aby dowiedzieć się więcej, przejdź do poniższych samouczków.

> [!div class="nextstepaction"]
> [Wprowadzenie do aplikacji konsolowej C# w programie Visual Studio](../get-started/csharp/tutorial-console.md)
