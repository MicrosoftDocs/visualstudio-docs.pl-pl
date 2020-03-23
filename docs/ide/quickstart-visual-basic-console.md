---
title: Tworzenie pierwszej aplikacji konsoli za pomocą języka Visual Basic
description: Dowiedz się, jak utworzyć prostą aplikację konsoli Hello World w programie Visual Studio za pomocą programu Visual Basic krok po kroku.
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
- vb
ms.workload:
- multiple
ms.openlocfilehash: 34f3dc8642e2cf8e965e2ad303bed79931d2645c
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579500"
---
# <a name="quickstart-create-your-first-console-app-in-visual-studio-with-visual-basic"></a>Szybki start: tworzenie pierwszej aplikacji konsoli w programie Visual Studio za pomocą języka Visual Basic

W tym 5-10 minut wprowadzenie do środowiska programistycznego zintegrowanego programu Visual Studio (IDE) utworzysz prostą aplikację języka Visual Basic, która jest uruchamiana na konsoli.

::: moniker range="vs-2017"

Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [pobierania programu Visual Studio,](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) aby zainstalować ją bezpłatnie.

::: moniker-end

::: moniker range="vs-2019"

Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [pobierania programu Visual Studio,](https://visualstudio.microsoft.com/downloads) aby zainstalować ją bezpłatnie.

::: moniker-end

## <a name="create-a-project"></a>Tworzenie projektu

Najpierw utworzysz projekt aplikacji języka Visual Basic. Typ projektu zawiera wszystkie potrzebne pliki szablonów, zanim jeszcze cokolwiek dodasz!

::: moniker range="vs-2017"

1. Otwórz program Visual Studio 2017.

2. Na górnym pasku menu wybierz pozycję **Plik** > **nowego** > **projektu**.

3. W oknie dialogowym **Nowy projekt** w lewym okienku rozwiń rozwiń pozycję **Visual Basic**, a następnie wybierz pozycję **.NET Core**. W środkowym okienku wybierz pozycję **Aplikacja konsoli (.NET Core)**. Następnie nazwij projekt *HelloWorld*.

   ![Szablon projektu aplikacji konsoli (.NET Core) w oknie dialogowym Nowy projekt w programie Visual Studio IDE](../ide/media/new-project-vb-dotnetcore-helloworld-console-app.png)

     Jeśli nie widzisz szablonu projektu **aplikacji konsoli (NET Core),** kliknij łącze **Otwórz instalator programu Visual Studio** w lewym okienku okna dialogowego Nowy **projekt.**

   ![Kliknij łącze Otwórz instalator programu Visual Studio w oknie dialogowym Nowy projekt](../ide/media/vb-open-visual-studio-installer-hello-world.png)

     Uruchamia instalator programu Visual Studio. Wybierz **wieloplatformowe obciążenie programistyczne .NET Core,** a następnie wybierz pozycję **Modyfikuj**.

     ![Wieloplatformowe obciążenie programowe programu .NET Core w Instalatorze programu Visual Studio](../ide/media/dot-net-core-xplat-dev-workload.png)

::: moniker-end

::: moniker range="vs-2019"

> [!NOTE]
> Niektóre zrzuty ekranu w tym przewodniku Szybki start używają ciemnego motywu. Jeśli nie używasz ciemnego motywu, ale chcesz, zobacz [Personalizuj ide programu Visual Studio i edytora](quickstart-personalize-the-ide.md) strony, aby dowiedzieć się, jak to zrobić.

1. Otwórz program Visual Studio 2019.

1. W oknie początkowym wybierz pozycję **Utwórz nowy projekt**.

   ![Wyświetlanie okna "Tworzenie nowego projektu"](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. W oknie **Utwórz nowy projekt** wprowadź lub wpisz *konsolę* w polu wyszukiwania. Następnie wybierz pozycję **Visual Basic** z listy Język, a następnie wybierz pozycję **Windows** z listy Platforma. 

   Po zastosowaniu filtrów językowych i platformowych wybierz szablon **Aplikacji konsoli (NET Core),** a następnie wybierz pozycję **Dalej**.

   ![Wybieranie szablonu języka Visual Basic dla aplikacji konsoli (.NET Framework)](../get-started/visual-basic/media/vs-2019/vb-create-new-project-search-console-net-core-filtered.png)

   > [!NOTE]
   > Jeśli nie widzisz szablonu **aplikacji konsoli (.NET Core),** możesz go zainstalować w oknie **Utwórz nowy projekt.** W komunikacie **Nie znajdowanie tego, czego szukasz?** **Install more tools and features**
   >
   > ![Link "Zainstaluj więcej narzędzi i funkcji" z komunikatu "Nie znajdując tego, czego szukasz" w oknie "Utwórz nowy projekt"](../get-started/media/vs-2019/not-finding-what-looking-for.png) 
   > 
   > Następnie w Instalatorze programu Visual Studio wybierz obciążenie **programistyczne .NET Core na różnych platformach.**
   >
   > ![Wieloplatformowe obciążenie programowe programu .NET Core w Instalatorze programu Visual Studio](../get-started/media/dot-net-core-xplat-dev-workload.png)
   >
   > Następnie wybierz przycisk **Modyfikuj** w Instalatorze programu Visual Studio. Może zostać wyświetlony monit o zapisanie pracy; jeśli tak, zrób to. Następnie wybierz pozycję **Kontynuuj,** aby zainstalować obciążenie. Następnie wróć do kroku 2 w tej procedurze["Utwórz projekt".](#create-a-project)

1. W oknie **Konfigurowanie nowego projektu** wpisz lub wpisz *WhatIsYourName* w polu **Nazwa projektu.** Następnie wybierz pozycję **Utwórz**.

   ![w oknie "Skonfiguruj nowy projekt" nazwij swój projekt "WhatIsYourName"](../get-started/visual-basic/media/vs-2019/vb-name-your-project-whatname.png)

   Visual Studio otwiera nowy projekt.

::: moniker-end

## <a name="create-the-application"></a>Tworzenie aplikacji

Po wybraniu szablonu projektu języka Visual Basic i nazwa projektu visual studio tworzy prostą aplikację "Hello World" dla Ciebie. Wywołuje <xref:System.Console.WriteLine%2A> metodę wyświetlania dosłownego ciągu "Hello World!" w oknie konsoli.

![Wyświetlanie domyślnego kodu Hello World z szablonu](../ide/media/vb-console-helloworld-template.png)

Po kliknięciu przycisku **HelloWorld** w IDE, można uruchomić program w trybie debugowania.

  ![Kliknij przycisk Hello World, aby uruchomić program w trybie debugowania](../ide/media/vb-console-hello-world-button.png)

Po wykonaniu tej tej usługi okno konsoli jest widoczne tylko przez chwilę przed jego zamknięciem. Dzieje się `Main` tak, ponieważ metoda kończy się po jego pojedynczej instrukcji wykonuje i tak kończy się aplikacja.

### <a name="add-some-code"></a>Dodaj kod

Dodajmy kod, aby wstrzymać aplikację, a następnie poprosić o dane wejściowe użytkownika.

1. Dodaj następujący kod natychmiast po <xref:System.Console.WriteLine%2A> wywołaniu metody:

   ```vb
   Console.Write("Press any key to continue...")
   Console.ReadKey(true)
   ```

    Spowoduje to wstrzymanie programu do momentu naciśnięcia klawisza.

2. Na pasku menu wybierz pozycję **Build** > **Build Solution**.

   To kompiluje program do języka pośredniego (IL), który jest konwertowany na kod binarny przez kompilator just-in-time (JIT).

## <a name="run-the-application"></a>Uruchamianie aplikacji

1. Kliknij przycisk **HelloWorld** na pasku narzędzi.

   ![Kliknij przycisk Hello World, aby uruchomić program z paska narzędzi](../ide/media/vb-console-hello-world-button.png)

2. Naciśnij dowolny klawisz, aby zamknąć okno konsoli.

   ![Okno konsoli z hello world i naciśnij dowolny klawisz, aby kontynuować](../ide/media/vb-console-hello-world-press-any-key.png)

## <a name="next-steps"></a>Następne kroki

Gratulujemy ukończenia tego szybkiego startu! Mamy nadzieję, że dowiedziałeś się trochę o języku Visual Basic i ide programu Visual Studio. Aby dowiedzieć się więcej, przejdź do następującego samouczka.

> [!div class="nextstepaction"]
> [Wprowadzenie do programu Visual Basic w programie Visual Studio](../get-started/visual-basic/tutorial-console.md)
