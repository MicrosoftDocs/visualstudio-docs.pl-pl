---
title: Tworzenie pierwszej aplikacji konsoli języka C# za pomocą programu Visual Studio
titleSuffix: ''
description: Dowiedz się, jak utworzyć prostą aplikację konsoli Hello World w programie Visual Studio w języku C#, krok po kroku.
ms.custom: seodec18
ms.date: 03/23/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: quickstart
ms.devlang: vb
author: ornellaalt
ms.author: ornella
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 20b2cf2bf12e9b24ca12d0a73b43e4a56e8246f4
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579489"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-c-console-app"></a>Szybki start: tworzenie pierwszej aplikacji konsoli języka C# za pomocą programu Visual Studio

W tym 5-10 minut wprowadzenie do środowiska programistycznego zintegrowanego programu Visual Studio (IDE), utworzysz prostą aplikację języka C#, która działa na konsoli.

::: moniker range="vs-2017"

Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [pobierania programu Visual Studio,](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) aby zainstalować ją bezpłatnie.

::: moniker-end

::: moniker range="vs-2019"

Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [pobierania programu Visual Studio,](https://visualstudio.microsoft.com/downloads) aby zainstalować ją bezpłatnie.

::: moniker-end

## <a name="create-a-project"></a>Tworzenie projektu

Najpierw utworzysz projekt aplikacji języka C#. Typ projektu zawiera wszystkie potrzebne pliki szablonów, zanim jeszcze cokolwiek dodasz!

::: moniker range="vs-2017"

1. Otwórz program Visual Studio 2017.

2. Na górnym pasku menu wybierz pozycję **Plik** > **nowego** > **projektu**.

3. W oknie dialogowym **Nowy projekt** w lewym okienku rozwiń węzeł **C#**, a następnie wybierz pozycję **.NET Core**. W środkowym okienku wybierz pozycję **Aplikacja konsoli (.NET Core)**. Następnie nazwij projekt *HelloWorld*.

   ![Szablon projektu aplikacji konsoli (.NET Core) w oknie dialogowym Nowy projekt w programie Visual Studio IDE](../ide/media/new-project-csharp-dotnetcore-helloworld-console-app.png)

     Jeśli nie widzisz szablonu projektu **aplikacji konsoli (NET Core),** wybierz łącze **Otwórz Instalator programu Visual Studio** w lewym okienku okna dialogowego Nowy **projekt.**

   ![Wybieranie łącza Instalator programu Visual Studio w oknie dialogowym Nowy projekt](../ide/media/csharp-open-visual-studio-installer-hello-world.png)

     Uruchamia instalator programu Visual Studio. Wybierz **wieloplatformowe obciążenie programistyczne .NET Core,** a następnie wybierz pozycję **Modyfikuj**.

     ![Wieloplatformowe obciążenie programowe programu .NET Core w Instalatorze programu Visual Studio](../ide/media/dot-net-core-xplat-dev-workload.png)

::: moniker-end

::: moniker range="vs-2019"

1. Otwórz program Visual Studio 2019.

1. W oknie początkowym wybierz pozycję **Utwórz nowy projekt**.

   ![Okno "Tworzenie nowego projektu"](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. W oknie **Utwórz nowy projekt** wprowadź lub wpisz *konsolę* w polu wyszukiwania. Następnie wybierz **pozycję C#** z listy Język, a następnie wybierz pozycję **Windows** z listy Platforma. 

   Po zastosowaniu filtrów językowych i platformowych wybierz szablon **Aplikacji konsoli (NET Core),** a następnie wybierz pozycję **Dalej**.

   ![Wybierz szablon C# dla aplikacji konsoli (.NET Framework)](../get-started/csharp/media/vs-2019/csharp-create-new-project-search-console-net-core-filtered.png)

   > [!NOTE]
   > Jeśli nie widzisz szablonu **aplikacji konsoli (.NET Core),** możesz go zainstalować w oknie **Utwórz nowy projekt.** W komunikacie **Nie znajdowanie tego, czego szukasz?** **Install more tools and features**
   >
   > ![Link "Zainstaluj więcej narzędzi i funkcji" z komunikatu "Nie znajdując tego, czego szukasz" w oknie "Utwórz nowy projekt"](../get-started/media/vs-2019/not-finding-what-looking-for.png) 
   > 
   > Następnie w Instalatorze programu Visual Studio wybierz obciążenie **programistyczne .NET Core na różnych platformach.**
   >
   > ![Wieloplatformowe obciążenie programowe programu .NET Core w Instalatorze programu Visual Studio](./media/dot-net-core-xplat-dev-workload.png)
   >
   > Następnie wybierz przycisk **Modyfikuj** w Instalatorze programu Visual Studio. Może zostać wyświetlony monit o zapisanie pracy; jeśli tak, zrób to. Następnie wybierz pozycję **Kontynuuj,** aby zainstalować obciążenie. Następnie wróć do kroku 2 w tej procedurze["Utwórz projekt".](#create-a-project)

1. W oknie **Konfigurowanie nowego projektu** wpisz lub wprowadź *helloworld* w polu **Nazwa projektu.** Następnie wybierz pozycję **Utwórz**.

   ![w oknie "Skonfiguruj nowy projekt" nazwij swój projekt "HelloWorld"](../get-started/csharp/media/vs-2019/csharp-name-your-helloworld-project.png)

   Visual Studio otwiera nowy projekt.
   
::: moniker-end

## <a name="create-the-application"></a>Tworzenie aplikacji

::: moniker range="vs-2017"

Po wybraniu szablonu projektu języka C# i nazwa projektu visual studio tworzy prostą aplikację "Hello World" dla Ciebie.

::: moniker-end

::: moniker range="vs-2019"

Visual Studio zawiera domyślny kod "Hello World" w projekcie.

::: moniker-end

(Aby to zrobić, <xref:System.Console.WriteLine%2A> wywołuje metodę wyświetlania dosłownego ciągu "Hello World!" w oknie konsoli).)

   ![Wyświetlanie domyślnego kodu Hello World z szablonu](../ide/media/csharp-console-helloworld-template.png)

Po naciśnięciu **klawisza F5**program można uruchomić w trybie debugowania. Jednak okno konsoli jest widoczne tylko przez chwilę przed zamknięciem.

(To zachowanie występuje, `Main` ponieważ metoda kończy się po wykonaniu pojedynczej instrukcji, a więc aplikacja kończy się.)

### <a name="add-some-code"></a>Dodaj kod

Dodajmy kod, aby wstrzymać aplikację, aby okno konsoli nie zostało zamknięte, dopóki nie naciśniesz **klawisz ENTER**.

1. Dodaj następujący kod natychmiast po <xref:System.Console.WriteLine%2A> wywołaniu metody:

   ```csharp
   Console.ReadLine();
   ```

1. Sprawdź, czy wygląda to tak w edytorze kodu:

   ![Dodawanie kodu w celu wstrzymania aplikacji Hello World](../ide/media/csharp-console-helloworld-add-code.png)

## <a name="run-the-application"></a>Uruchamianie aplikacji

1. Wybierz przycisk **HelloWorld** na pasku narzędzi, aby uruchomić aplikację w trybie debugowania. (Lub, można nacisnąć **klawisz F5**.)

   ![Wybierz przycisk Hello World, aby uruchomić aplikację z paska narzędzi](../ide/media/csharp-console-hello-world-button.png)

1. Wyświetl aplikację w oknie konsoli.

   ![Okno konsoli z hello world!](../ide/media/csharp-console-hello-world.png)

### <a name="close-the-application"></a>Zamykanie aplikacji

1. Naciśnij **klawisz ENTER,** aby zamknąć okno konsoli.

1. Zamknij okienko **dane wyjściowe** w programie Visual Studio.

   ![Zamykanie okienka dane wyjściowe w programie Visual Studio](../ide/media/csharp-hello-world-close-output-pane.png)

1. Zamknij program Visual Studio.

## <a name="next-steps"></a>Następne kroki

Gratulujemy ukończenia tego szybkiego startu! Mamy nadzieję, że dowiedziałeś się trochę o C# i ide programu Visual Studio. Aby dowiedzieć się więcej, przejdź do poniższych samouczków.

> [!div class="nextstepaction"]
> [Wprowadzenie do aplikacji konsoli języka C# w programie Visual Studio](../get-started/csharp/tutorial-console.md)
