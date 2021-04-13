---
title: Tworzenie pierwszej aplikacji konsolowej przy użyciu Visual Basic
description: Dowiedz się, jak utworzyć prostą aplikację konsolową Hello world w programie Visual Studio z Visual Basic, krok po kroku.
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
- vb
ms.workload:
- multiple
ms.openlocfilehash: 3a103c672b6539f5893cf52a6e83acde6c87176d
ms.sourcegitcommit: 6d88913a8b5a9e5eda01d3f95205b4d138f440f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2021
ms.locfileid: "107296641"
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

Najpierw utworzysz projekt aplikacji Visual Basic. Typ projektu jest dostarczany ze wszystkimi plikami szablonu, które będą potrzebne, zanim będzie można nawet dodać wszystko.

::: moniker range="vs-2017"

1. Otwórz program Visual Studio 2017.

2. Na górnym pasku menu wybierz pozycję **plik** > **Nowy** > **projekt**.

3. W oknie dialogowym **Nowy projekt** w lewym okienku rozwiń węzeł **Visual Basic**, a następnie wybierz pozycję **.NET Core**. W środkowym okienku wybierz pozycję **aplikacja konsoli (.NET Core)**. Następnie nadaj nazwę projekt *HelloWorld*.

   ![Szablon projektu aplikacji konsolowej (.NET Core) w oknie dialogowym Nowy projekt w programie Visual Studio IDE](../ide/media/new-project-vb-dotnetcore-helloworld-console-app.png)

     Jeśli szablon projektu **aplikacja konsoli (.NET Core)** nie jest widoczny, kliknij link **Otwórz Instalator programu Visual Studio** w lewym okienku okna dialogowego **Nowy projekt** .

   ![Kliknij link Otwórz Instalator programu Visual Studio w oknie dialogowym Nowy projekt](../ide/media/vb-open-visual-studio-installer-hello-world.png)

     Zostanie uruchomiona Instalator programu Visual Studio. Wybierz obciążenie dla **wielu platform platformy .NET Core** , a następnie wybierz **Modyfikuj**.

     ![Obciążenie Międzyplatformowe dla platformy .NET Core w Instalator programu Visual Studio](../ide/media/dot-net-core-xplat-dev-workload.png)

::: moniker-end

::: moniker range="vs-2019"

> [!NOTE]
> Niektóre zrzuty ekranu w tym przewodniku szybki start używają ciemnego motywu. Jeśli nie używasz ciemnego motywu, ale chcesz, zobacz stronę [personalizowanie środowiska IDE i edytora programu Visual Studio](quickstart-personalize-the-ide.md) , aby dowiedzieć się, jak.

1. Otwórz program Visual Studio 2019.

1. W oknie uruchamiania wybierz pozycję **Utwórz nowy projekt**.

   ![Wyświetl okno "Tworzenie nowego projektu"](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. W oknie **Tworzenie nowego projektu** wybierz **Visual Basic** z listy język. Następnie z listy typów projektów wybierz pozycję **Windows** z listy platform i **konsoli** .

   Po zastosowaniu filtrów języka, platformy i typu projektu wybierz szablon **Aplikacja konsolowa** , a następnie wybierz **dalej**.

   :::image type="content" source="../get-started/visual-basic/media/vs-2019/vb-create-new-project-console-net-core.png" alt-text="Wybierz szablon Visual Basic dla aplikacji konsolowej":::

   > [!NOTE]
   > Jeśli szablon **aplikacji konsolowej** nie jest wyświetlany, można go zainstalować za pomocą okna **Utwórz nowy projekt** . W obszarze **nie można znaleźć tego, czego szukasz?** komunikat wybierz łącze **Zainstaluj więcej narzędzi i funkcji** .
   >
   > ![Link "Zainstaluj więcej narzędzi i funkcji" z komunikatu "nie można odnaleźć szukanego elementu" w oknie "Tworzenie nowego projektu"](../get-started/media/vs-2019/not-finding-what-looking-for.png) 
   > 
   > Następnie w Instalator programu Visual Studio wybierz obciążenie dla **wielu platform platformy .NET Core** .
   >
   > ![Obciążenie Międzyplatformowe dla platformy .NET Core w Instalator programu Visual Studio](../get-started/media/dot-net-core-xplat-dev-workload.png)
   >
   > Następnie wybierz przycisk **Modyfikuj** w Instalator programu Visual Studio. Może zostać wyświetlony monit o zapisanie pracy; Jeśli tak, zrób to. Następnie wybierz pozycję **Kontynuuj** , aby zainstalować obciążenie. Następnie wróć do kroku 2 w tej procedurze "[Create a Project](#create-a-project)".

1. W oknie **Konfigurowanie nowego projektu** wpisz lub wprowadź *WhatIsYourName* w polu **Nazwa projektu** . Następnie wybierz przycisk **dalej**.

   :::image type="content" source="../get-started/visual-basic/media/vs-2019/vb-name-your-project-whatname.png" alt-text="w oknie &quot;Konfigurowanie nowego projektu&quot; nazwij projekt &quot;WhatIsYourName&quot;":::

1. W oknie **Informacje dodatkowe** należy wybrać **platformę .NET Core 3,1** dla platformy docelowej. W przeciwnym razie wybierz pozycję **.NET Core 3,1**. Następnie wybierz pozycję **Utwórz**.

   :::image type="content" source="../get-started/visual-basic/media/vs-2019/vb-target-framework.png" alt-text="W oknie &quot;dodatkowe informacje&quot; Upewnij się, że wybrano opcję .NET Core 3,1":::

   Program Visual Studio otwiera nowy projekt.

::: moniker-end

## <a name="create-the-application"></a>Tworzenie aplikacji

Po wybraniu szablonu projektu Visual Basic i Nazwij swój projekt, program Visual Studio utworzy prostą aplikację "Hello world". Wywołuje <xref:System.Console.WriteLine%2A> metodę w celu wyświetlenia ciągu literału "Hello World!" w oknie konsoli.

![Wyświetl domyślny kod Hello world z szablonu](../ide/media/vb-console-helloworld-template.png)

Jeśli klikniesz przycisk **HelloWorld** w IDE, możesz uruchomić program w trybie debugowania.

  ![Kliknij przycisk Hello world, aby uruchomić program w trybie debugowania](../ide/media/vb-console-hello-world-button.png)

Po wykonaniu tej czynności okno konsoli jest widoczne tylko przez chwilę przed zamknięciem. Dzieje się tak, ponieważ `Main` Metoda kończy się po wykonaniu jednej instrukcji i dlatego aplikacja kończy działanie.

### <a name="add-some-code&quot;></a>Dodaj kod

Dodajmy kod, aby wstrzymać aplikację, a następnie poproszony o wprowadzenie danych przez użytkownika.

1. Dodaj następujący kod bezpośrednio po wywołaniu <xref:System.Console.WriteLine%2A> metody:

   ```vb
   Console.Write(&quot;Press any key to continue...")
   Console.ReadKey(true)
   ```

    Powoduje to wstrzymanie programu do momentu naciśnięcia klawisza.

2. Na pasku menu wybierz pozycję **kompilacja** Kompiluj  >  **rozwiązanie**.

   Spowoduje to skompilowanie programu do języka pośredniego (IL), który jest konwertowany na kod binarny przez kompilator just-in-Time (JIT).

## <a name="run-the-application"></a>Uruchamianie aplikacji

1. Kliknij przycisk **HelloWorld** na pasku narzędzi.

   ![Kliknij przycisk Hello world, aby uruchomić program z paska narzędzi](../ide/media/vb-console-hello-world-button.png)

2. Naciśnij dowolny klawisz, aby zamknąć okno konsoli.

   ![Okno konsoli zawierające Hello world i naciśnij dowolny klawisz, aby kontynuować](../ide/media/vb-console-hello-world-press-any-key.png)

## <a name="next-steps"></a>Następne kroki

Gratulujemy zakończenia tego przewodnika Szybki Start! Mamy nadzieję, że uczysz się nieco o Visual Basic i IDE programu Visual Studio. Aby dowiedzieć się więcej, przejdź do następującego samouczka.

> [!div class="nextstepaction"]
> [Wprowadzenie do Visual Basic w programie Visual Studio](../get-started/visual-basic/tutorial-console.md)
