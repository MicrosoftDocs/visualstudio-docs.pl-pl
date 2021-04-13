---
title: 'Samouczek: wprowadzenie do Visual Basic'
description: Dowiedz się, jak tworzyć aplikacje konsolowe Visual Basic w programie Visual Studio, krok po kroku.
ms.custom: seodec18, get-started
ms.date: 02/10/2021
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
ms.devlang: vb
author: j-martens
ms.author: jmartens
manager: jmartens
dev_langs:
- vb
ms.workload:
- multiple
ms.openlocfilehash: 075c84433e5784106bbe1f9c6ac6f58d9613bfdb
ms.sourcegitcommit: 6d88913a8b5a9e5eda01d3f95205b4d138f440f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2021
ms.locfileid: "107295497"
---
# <a name="tutorial-get-started-with-visual-basic-in-visual-studio"></a>Samouczek: wprowadzenie do Visual Basic w programie Visual Studio

W tym samouczku dla Visual Basic (VB) będziesz używać programu Visual Studio do tworzenia i uruchamiania kilku różnych aplikacji konsolowych oraz eksplorowania niektórych funkcji [zintegrowanego środowiska programistycznego (IDE) programu Visual Studio](visual-studio-ide.md) .

::: moniker range="vs-2017"

Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) , aby zainstalować ją bezpłatnie.

::: moniker-end

::: moniker range="vs-2019"

Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/downloads) , aby zainstalować ją bezpłatnie.

::: moniker-end

## <a name="create-a-project"></a>Tworzenie projektu

Najpierw utworzymy projekt aplikacji Visual Basic. Typ projektu jest dostarczany ze wszystkimi plikami szablonu, które będą potrzebne, zanim będzie można nawet dodać wszystko.

::: moniker range="vs-2017"

1. Otwórz program Visual Studio 2017.

2. Na górnym pasku menu wybierz pozycję **plik** > **Nowy** > **projekt**.

3. W oknie dialogowym **Nowy projekt** w lewym okienku rozwiń węzeł **Visual Basic**, a następnie wybierz pozycję **.NET Core**. W środkowym okienku wybierz pozycję **aplikacja konsoli (.NET Core)**. Następnie nadaj nazwę projektowi *WhatIsYourName*.

   ![Szablon projektu aplikacji konsolowej (.NET Core) w oknie dialogowym Nowy projekt w programie Visual Studio IDE](media/new-project-vb-dotnetcore-whatisyourname-console-app.png)

### <a name="add-a-workload-optional"></a>Dodaj obciążenie (opcjonalnie)

Jeśli szablon projektu **Aplikacja konsolowa (.NET Core)** nie jest widoczny, można go uzyskać, dodając obciążenie **Międzyplatformowe platformy .NET Core** . Możesz dodać to obciążenie jeden z dwóch poniższych sposobów, w zależności od tego, które aktualizacje programu Visual Studio 2017 są zainstalowane na maszynie.

#### <a name="option-1-use-the-new-project-dialog-box"></a>Opcja 1: korzystanie z okna dialogowego Nowy projekt

1. Kliknij link **otwórz Instalator programu Visual Studio** w lewym okienku okna dialogowego **Nowy projekt** .

   ![Kliknij link Otwórz Instalator programu Visual Studio w oknie dialogowym Nowy projekt](../media/vs-open-visual-studio-installer-generic.png)

1. Zostanie uruchomiona Instalator programu Visual Studio. Wybierz obciążenie dla **wielu platform platformy .NET Core** , a następnie wybierz **Modyfikuj**.

   ![Obciążenie Międzyplatformowe dla platformy .NET Core w Instalator programu Visual Studio](../media/tutorial-aspnet-workload.png)

#### <a name="option-2-use-the-tools-menu-bar"></a>Opcja 2. Korzystanie z paska menu narzędzi

1. Anuluj okno dialogowe **Nowy projekt** , a następnie z górnego paska menu wybierz kolejno opcje **Narzędzia** > **Pobierz narzędzia i funkcje**.

1. Zostanie uruchomiona Instalator programu Visual Studio. Wybierz obciążenie dla **wielu platform platformy .NET Core** , a następnie wybierz **Modyfikuj**.

::: moniker-end

::: moniker range="vs-2019"

> [!NOTE]
> Niektóre zrzuty ekranu w tym samouczku używają ciemnego motywu. Jeśli nie używasz ciemnego motywu, ale chcesz, zobacz stronę [personalizowanie środowiska IDE i edytora programu Visual Studio](../../ide/quickstart-personalize-the-ide.md) , aby dowiedzieć się, jak.

1. Otwórz program Visual Studio 2019.

1. W oknie uruchamiania wybierz pozycję **Utwórz nowy projekt**.

   ![Wyświetl okno "Tworzenie nowego projektu"](../../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. W oknie **Tworzenie nowego projektu** wybierz **Visual Basic** z listy język. Następnie z listy typów projektów wybierz pozycję **Windows** z listy platform i **konsoli** .

   Po zastosowaniu filtrów języka, platformy i typu projektu wybierz szablon **Aplikacja konsolowa** , a następnie wybierz **dalej**.

   :::image type="content" source="./media/vs-2019/vb-create-new-project-console-net-core.png" alt-text="Wybierz szablon Visual Basic dla aplikacji konsolowej":::

   > [!NOTE]
   > Jeśli szablon **aplikacji konsolowej** nie jest wyświetlany, można go zainstalować za pomocą okna **Utwórz nowy projekt** . W obszarze **nie można znaleźć tego, czego szukasz?** komunikat wybierz łącze **Zainstaluj więcej narzędzi i funkcji** .
   >
   > ![Link "Zainstaluj więcej narzędzi i funkcji" z komunikatu "nie można odnaleźć szukanego elementu" w oknie "Tworzenie nowego projektu"](../../get-started/media/vs-2019/not-finding-what-looking-for.png) 
   > 
   > Następnie w Instalator programu Visual Studio wybierz obciążenie dla **wielu platform platformy .NET Core** .
   >
   > ![Obciążenie Międzyplatformowe dla platformy .NET Core w Instalator programu Visual Studio](../../get-started/media/dot-net-core-xplat-dev-workload.png)
   >
   > Następnie wybierz przycisk **Modyfikuj** w Instalator programu Visual Studio. Może zostać wyświetlony monit o zapisanie pracy; Jeśli tak, zrób to. Następnie wybierz pozycję **Kontynuuj** , aby zainstalować obciążenie. Następnie wróć do kroku 2 w tej procedurze "[Create a Project](#create-a-project)".

1. W oknie **Konfigurowanie nowego projektu** wpisz lub wprowadź *WhatIsYourName* w polu **Nazwa projektu** . Następnie wybierz przycisk **dalej**.

   :::image type="content" source="./media/vs-2019/vb-name-your-project-whatname.png" alt-text="w oknie &quot;Konfigurowanie nowego projektu&quot; nazwij projekt &quot;WhatIsYourName&quot;":::

1. W oknie **Informacje dodatkowe** należy wybrać **platformę .NET Core 3,1** dla platformy docelowej. W przeciwnym razie wybierz pozycję **.NET Core 3,1**. Następnie wybierz pozycję **Utwórz**.

   :::image type="content" source="./media/vs-2019/vb-target-framework.png" alt-text="W oknie &quot;dodatkowe informacje&quot; Upewnij się, że wybrano opcję .NET Core 3,1":::

   Program Visual Studio otwiera nowy projekt.

::: moniker-end

## <a name="create-a-what-is-your-name-application"></a>Tworzenie aplikacji "co to jest Twoja nazwa"

Utwórzmy aplikację, która wyświetli komunikat z prośbą o Twoją nazwę, a następnie wyświetli ją wraz z datą i godziną. Oto kroki tej procedury:

 ::: moniker range="vs-2017"

1. Jeśli nie jest jeszcze otwarty, Otwórz projekt *WhatIsYourName* .

1. Wprowadź następujący kod Visual Basic bezpośrednio po nawiasie otwierającym, który następuje po `Sub Main(args As String())` wierszu i przed `End Sub` wierszem:

     ```vb
     Console.WriteLine(vbCrLf + "What is your name? ")
     Dim name = Console.ReadLine()
     Dim currentDate = DateTime.Now
     Console.WriteLine($"{vbCrLf}Hello, {name}, on {currentDate:d} at {currentDate:t}")
     Console.Write(vbCrLf + "Press any key to exit... ")
     Console.ReadKey(True)
    ```

    Ten kod zastępuje istniejące <xref:System.Console.WriteLine%2A> instrukcje, <xref:System.Console.Write%2A> i <xref:System.Console.ReadKey%2A> .

   ![Okno kodu z informacjami o kodzie swojej nazwy](./media/vs-2019/vb-codewindow-what-name-dark.png)

1. Użyj zielonego przycisku **Start** lub naciśnij klawisz **F5** , aby skompilować i uruchomić swoją pierwszą aplikację.

1. Po otwarciu okna konsoli wprowadź swoją nazwę. Okno konsoli powinno wyglądać podobnie do poniższego zrzutu ekranu:

   ![Okno konsoli, w którym jest wyświetlana nazwa, Data i godzina, i naciśnij dowolny klawisz, aby kontynuować komunikat](media/vb-console-what-name.png)

1. Naciśnij dowolny klawisz, aby zamknąć okno konsoli.

::: moniker-end

::: moniker range="vs-2019"

1. W projekcie *WhatIsYourName* wprowadź następujący kod Visual Basic bezpośrednio po nawiasie otwierającym, który następuje po `Sub Main(args As String())` wierszu i przed `End Sub` wierszem:

     ```vb
     Console.WriteLine(vbCrLf + "What is your name? ")
     Dim name = Console.ReadLine()
     Dim currentDate = DateTime.Now
     Console.WriteLine($"{vbCrLf}Hello, {name}, on {currentDate:d} at {currentDate:t}!")
     Console.Write(vbCrLf + "Press any key to exit... ")
     Console.ReadKey(True)
    ```

    Ten kod zastępuje istniejące <xref:System.Console.WriteLine%2A> instrukcje, <xref:System.Console.Write%2A> i <xref:System.Console.ReadKey%2A> .

   ![Okno kodu z informacjami o kodzie swojej nazwy](./media/vs-2019/vb-codewindow-what-name-dark.png)

1. Użyj zielonego przycisku **Start** lub naciśnij klawisz **F5** , aby skompilować i uruchomić swoją pierwszą aplikację.

1. Po otwarciu okna konsoli wprowadź swoją nazwę. Okno konsoli powinno wyglądać podobnie do poniższego zrzutu ekranu:

   ![Okno konsoli, w którym jest wyświetlana nazwa, Data i godzina, i naciśnij dowolny klawisz, aby kontynuować komunikat](media/vb-console-what-name.png)

1. Naciśnij dowolny klawisz, aby zamknąć okno konsoli.

 ::: moniker-end

## <a name="create-a-calculate-this-application"></a>Tworzenie aplikacji "Oblicz tę"

::: moniker range="vs-2017"

1. Otwórz program Visual Studio 2017, a następnie z górnego paska menu wybierz pozycję **plik** > **Nowy** > **projekt**.

1. W oknie dialogowym **Nowy projekt** w lewym okienku rozwiń węzeł **Visual Basic**, a następnie wybierz pozycję **.NET Core**. W środkowym okienku wybierz pozycję **aplikacja konsoli (.NET Core)**. Następnie Nazwij plik *CalculateThis*.

1. Wprowadź następujący kod między `Module Program` wierszem a `End Module` wierszem:

   ```vb
   Public num1 As Integer
   Public num2 As Integer
   Public answer As Integer
   Sub Main()
       Console.WriteLine("Type a number and press Enter")
       num1 = Console.ReadLine()
       Console.WriteLine("Type another number to add to it and press Enter")
       num2 = Console.ReadLine()
       answer = num1 + num2
       Console.WriteLine("The answer is " & answer)
       Console.ReadLine()
   End Sub
   ```

   Okno kodu powinno wyglądać podobnie do poniższego zrzutu ekranu:

   ![Okno kodu przedstawiające kod CalculateThis](media/vb-codewindow-calculate-this.png)

1. Kliknij pozycję **CalculateThis** , aby uruchomić program. Okno konsoli powinno wyglądać podobnie do poniższego zrzutu ekranu:

    ![Okno konsoli z aplikacją CalculateThis, która zawiera monity o akcje do wykonania.](media/vb-console-calculate-this.png)

::: moniker-end 

::: moniker range="vs-2019"

1. W oknie uruchamiania wybierz pozycję **Utwórz nowy projekt**. 

1. W oknie **Tworzenie nowego projektu** wybierz **Visual Basic** z listy język. Następnie z listy typów projektów wybierz pozycję **Windows** z listy platform i **konsoli** .

1. Po zastosowaniu filtrów języka, platformy i typu projektu wybierz szablon **Aplikacja konsolowa** , a następnie wybierz **dalej**.

   Następnie w oknie **Konfigurowanie nowego projektu** wpisz lub wprowadź *CalculateThis* w polu **Nazwa projektu** . Następnie wybierz przycisk **dalej**.

1. W oknie **Informacje dodatkowe** należy wybrać **platformę .NET Core 3,1** dla platformy docelowej. W przeciwnym razie wybierz pozycję **.NET Core 3,1**. Następnie wybierz pozycję **Utwórz**.

1. Wprowadź następujący kod między `Module Program` wierszem a `End Module` wierszem:

   ```vb
   Public num1 As Integer
   Public num2 As Integer
   Public answer As Integer
   Sub Main()
       Console.WriteLine("Type a number and press Enter")
       num1 = Console.ReadLine()
       Console.WriteLine("Type another number to add to it and press Enter")
       num2 = Console.ReadLine()
       answer = num1 + num2
       Console.WriteLine("The answer is " & answer)
       Console.ReadLine()
   End Sub
   ```

   Okno kodu powinno wyglądać podobnie do poniższego zrzutu ekranu:

   ![Okno kodu przedstawiające kod CalculateThis](media/vb-codewindow-calculate-this.png)

1. Kliknij pozycję **CalculateThis** , aby uruchomić program. Okno konsoli powinno wyglądać podobnie do poniższego zrzutu ekranu:

    ![Okno konsoli z aplikacją CalculateThis, która zawiera monity o akcje do wykonania.](media/vb-console-calculate-this.png)

::: moniker-end

## <a name="quick-answers-faq"></a>Szybkie odpowiedzi — często zadawane pytania

Oto krótkie często zadawane pytania, aby wyróżnić niektóre kluczowe pojęcia.

### <a name="what-is-visual-basic"></a>Co to jest Visual Basic?

Visual Basic to bezpieczny dla typu język programowania, który został zaprojektowany, aby ułatwić naukę. Jest on oparty na warstwie Podstawowa, co oznacza "kod instrukcji symbolicznych całego celu".

### <a name="what-is-visual-studio"></a>Co to jest Visual Studio?

Program Visual Studio to zintegrowany pakiet programistyczny narzędzi do tworzenia produktywności dla deweloperów. Zastanów się, że program służy do tworzenia programów i aplikacji.

### <a name="what-is-a-console-app"></a>Co to jest Aplikacja konsolowa?

Aplikacja konsolowa pobiera dane wejściowe i wyświetla dane wyjściowe w oknie wiersza polecenia, nazywane również konsolą.

### <a name="what-is-net-core"></a>Co to jest .NET Core?

.NET Core to kolejny krok ewolucji .NET Framework. Gdy .NET Framework może udostępniać kod w różnych językach programowania, program .NET Core dodaje możliwość udostępniania kodu na różnych platformach. Jeszcze lepszym rozwiązaniem jest funkcja Open Source. (Zarówno .NET Framework, jak i .NET Core obejmują biblioteki wstępnie utworzonych funkcji, a także środowisko uruchomieniowe języka wspólnego (CLR), które działa jako maszyna wirtualna, w której ma być uruchamiany kod.)

## <a name="next-steps"></a>Następne kroki

Gratulujemy ukończenia tego samouczka. Aby dowiedzieć się więcej, zobacz poniższy samouczek.

> [!div class="nextstepaction"]
> [Kompilowanie biblioteki przy użyciu Visual Basic i zestaw .NET Core SDK w programie Visual Studio](/dotnet/core/tutorials/vb-library-with-visual-studio)

## <a name="see-also"></a>Zobacz też

* [Wskazówki dotyczące języka Visual Basic](/dotnet/visual-basic/walkthroughs)
* [Dokumentacja języka Visual Basic](/dotnet/visual-basic/language-reference/index)
* [Funkcja IntelliSense dla plików kodu Visual Basic](../../ide/visual-basic-specific-intellisense.md)
