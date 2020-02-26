---
title: Tworzenie pierwszej aplikacji konsolowej przy użyciu Visual Basic
description: Dowiedz się, jak utworzyć prostą aplikację konsolową Hello world w programie Visual Studio z Visual Basic, krok po kroku.
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
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579500"
---
# <a name="quickstart-create-your-first-console-app-in-visual-studio-with-visual-basic"></a>Szybki Start: Tworzenie pierwszej aplikacji konsolowej w programie Visual Studio przy użyciu Visual Basic

W tym 5-10 minutowym wprowadzeniu do zintegrowanego środowiska programistycznego (IDE) programu Visual Studio utworzysz prostą Visual Basic aplikację, która działa w konsoli programu.

::: moniker range="vs-2017"

Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) , aby zainstalować ją bezpłatnie.

::: moniker-end

::: moniker range="vs-2019"

Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/downloads) , aby zainstalować ją bezpłatnie.

::: moniker-end

## <a name="create-a-project"></a>Tworzenie projektu

Najpierw utworzysz projekt aplikacji w języku Visual Basic. Typ projektu jest dostarczany ze wszystkimi plikami szablonu, które będą potrzebne, zanim będzie można nawet dodać wszystko.

::: moniker range="vs-2017"

1. Otwórz program Visual Studio 2017.

2. Na górnym pasku menu wybierz kolejno pozycje **plik** > **Nowy** > **projekt**.

3. W oknie dialogowym **Nowy projekt** w lewym okienku rozwiń węzeł **Visual Basic**, a następnie wybierz pozycję **.NET Core**. W środkowym okienku wybierz pozycję **aplikacja konsoli (.NET Core)** . Następnie nadaj nazwę projekt *HelloWorld*.

   ![Szablon projektu aplikacji konsolowej (.NET Core) w oknie dialogowym Nowy projekt w programie Visual Studio IDE](../ide/media/new-project-vb-dotnetcore-helloworld-console-app.png)

     Jeśli szablon projektu **aplikacja konsoli (.NET Core)** nie jest widoczny, kliknij link **Otwórz Instalator programu Visual Studio** w lewym okienku okna dialogowego **Nowy projekt** .

   ![Kliknij link Otwórz Instalator programu Visual Studio w oknie dialogowym Nowy projekt](../ide/media/vb-open-visual-studio-installer-hello-world.png)

     Uruchamia Instalatora programu Visual Studio. Wybierz obciążenie dla **wielu platform platformy .NET Core** , a następnie wybierz **Modyfikuj**.

     ![Obciążenie Międzyplatformowe dla platformy .NET Core w Instalator programu Visual Studio](../ide/media/dot-net-core-xplat-dev-workload.png)

::: moniker-end

::: moniker range="vs-2019"

> [!NOTE]
> Niektóre zrzuty ekranu w tym przewodniku szybki start używają ciemnego motywu. Jeśli nie używasz ciemnego motywu, ale chcesz, zobacz stronę [personalizowanie środowiska IDE i edytora programu Visual Studio](quickstart-personalize-the-ide.md) , aby dowiedzieć się, jak.

1. Open Visual Studio 2019.

1. W oknie uruchamiania wybierz pozycję **Utwórz nowy projekt**.

   ![Wyświetl okno "Tworzenie nowego projektu"](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. W oknie **Tworzenie nowego projektu** w polu wyszukiwania wpisz lub wpisz *Console* . Następnie wybierz **Visual Basic** z listy język, a następnie wybierz pozycję **Windows** z listy platform. 

   Po zastosowaniu filtrów języka i platformy wybierz szablon **Aplikacja konsolowa (.NET Core)** , a następnie wybierz przycisk **dalej**.

   ![Wybierz szablon Visual Basic dla aplikacji konsolowej (.NET Framework)](../get-started/visual-basic/media/vs-2019/vb-create-new-project-search-console-net-core-filtered.png)

   > [!NOTE]
   > Jeśli nie widzisz szablonu **Aplikacja konsolowa (.NET Core)** , możesz go zainstalować z okna **Utwórz nowy projekt** . W obszarze **nie można znaleźć tego, czego szukasz?** komunikat wybierz łącze **Zainstaluj więcej narzędzi i funkcji** .
   >
   > ![Link "Zainstaluj więcej narzędzi i funkcji" z komunikatu "nie można odnaleźć szukanego elementu" w oknie "Tworzenie nowego projektu"](../get-started/media/vs-2019/not-finding-what-looking-for.png) 
   > 
   > Następnie w Instalator programu Visual Studio wybierz obciążenie dla **wielu platform platformy .NET Core** .
   >
   > ![Obciążenie Międzyplatformowe dla platformy .NET Core w Instalator programu Visual Studio](../get-started/media/dot-net-core-xplat-dev-workload.png)
   >
   > Następnie wybierz przycisk **Modyfikuj** w Instalator programu Visual Studio. Może zostać wyświetlony monit o zapisanie pracy; Jeśli tak, zrób to. Następnie wybierz pozycję **Kontynuuj** , aby zainstalować obciążenie. Następnie wróć do kroku 2 w tej procedurze "[Create a Project](#create-a-project)".

1. W oknie **Konfigurowanie nowego projektu** wpisz lub wprowadź *WhatIsYourName* w polu **Nazwa projektu** . Następnie wybierz pozycję **Utwórz**.

   ![w oknie "Konfigurowanie nowego projektu" nazwij projekt "WhatIsYourName"](../get-started/visual-basic/media/vs-2019/vb-name-your-project-whatname.png)

   Program Visual Studio otwiera nowy projekt.

::: moniker-end

## <a name="create-the-application"></a>Tworzenie aplikacji

Po wybraniu szablonu projektu Visual Basic i Nazwij swój projekt, program Visual Studio utworzy prostą aplikację "Hello world". Wywołuje metodę <xref:System.Console.WriteLine%2A>, aby wyświetlić ciąg literału "Hello world!" w oknie konsoli.

![Wyświetl domyślny kod Hello world z szablonu](../ide/media/vb-console-helloworld-template.png)

Jeśli klikniesz przycisk **HelloWorld** w IDE, możesz uruchomić program w trybie debugowania.

  ![Kliknij przycisk Hello world, aby uruchomić program w trybie debugowania](../ide/media/vb-console-hello-world-button.png)

Po wykonaniu tej czynności okno konsoli jest widoczne tylko przez chwilę przed zamknięciem. Dzieje się tak, ponieważ metoda `Main` kończy się po wykonaniu jednej instrukcji i dlatego aplikacja kończy działanie.

### <a name="add-some-code"></a>Dodaj kod

Dodajmy kod, aby wstrzymać aplikację, a następnie poproszony o wprowadzenie danych przez użytkownika.

1. Dodaj następujący kod bezpośrednio po wywołaniu metody <xref:System.Console.WriteLine%2A>:

   ```vb
   Console.Write("Press any key to continue...")
   Console.ReadKey(true)
   ```

    Powoduje to wstrzymanie programu do momentu naciśnięcia klawisza.

2. Na pasku menu wybierz kolejno opcje **kompiluj** > **Kompiluj rozwiązanie**.

   Spowoduje to skompilowanie programu do języka pośredniego (IL), który jest konwertowany na kod binarny przez kompilator just-in-Time (JIT).

## <a name="run-the-application"></a>Uruchamianie aplikacji

1. Kliknij przycisk **HelloWorld** na pasku narzędzi.

   ![Kliknij przycisk Hello world, aby uruchomić program z paska narzędzi](../ide/media/vb-console-hello-world-button.png)

2. Naciśnij dowolny klawisz, aby zamknąć okno konsoli.

   ![Okno konsoli zawierające Hello world i naciśnij dowolny klawisz, aby kontynuować](../ide/media/vb-console-hello-world-press-any-key.png)

## <a name="next-steps"></a>Następne kroki

Gratulujemy ukończenie tego przewodnika Szybki Start! Mamy nadzieję, że wiesz już nieco Visual Basic i Visual Studio IDE. Aby dowiedzieć się więcej, przejdź do następującego samouczka.

> [!div class="nextstepaction"]
> [Wprowadzenie do Visual Basic w programie Visual Studio](../get-started/visual-basic/tutorial-console.md)
