---
title: 'Samouczek: Wprowadzenie do języka Visual Basic'
description: Dowiedz się, jak tworzyć aplikacje konsoli visual basic w programie Visual Studio krok po kroku.
ms.custom: seodec18, get-started
ms.date: 09/11/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
ms.devlang: vb
author: ornellaalt
ms.author: ornella
manager: jillfra
dev_langs:
- vb
ms.workload:
- multiple
ms.openlocfilehash: 279bfb00a2466120d21c5c868c0987ec19202acc
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579935"
---
# <a name="tutorial-get-started-with-visual-basic-in-visual-studio"></a>Samouczek: Wprowadzenie do języka Visual Basic w programie Visual Studio

W tym samouczku dla języka Visual Basic (VB) użyjesz programu Visual Studio do tworzenia i uruchamiania kilku różnych aplikacji konsoli i eksplorowania niektórych funkcji [zintegrowanego środowiska programistycznego programu Visual Studio (IDE)](visual-studio-ide.md) podczas wykonywania tej operacji.

::: moniker range="vs-2017"

Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [pobierania programu Visual Studio,](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) aby zainstalować ją bezpłatnie.

::: moniker-end

::: moniker range="vs-2019"

Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [pobierania programu Visual Studio,](https://visualstudio.microsoft.com/downloads) aby zainstalować ją bezpłatnie.

::: moniker-end

## <a name="create-a-project"></a>Tworzenie projektu

Najpierw utworzymy projekt aplikacji języka Visual Basic. Typ projektu zawiera wszystkie potrzebne pliki szablonów, zanim jeszcze cokolwiek dodasz!

::: moniker range="vs-2017"

1. Otwórz program Visual Studio 2017.

2. Na górnym pasku menu wybierz pozycję **Plik** > **nowego** > **projektu**.

3. W oknie dialogowym **Nowy projekt** w lewym okienku rozwiń rozwiń pozycję **Visual Basic**, a następnie wybierz pozycję **.NET Core**. W środkowym okienku wybierz pozycję **Aplikacja konsoli (.NET Core)**. Następnie nazwij projekt *WhatIsYourName*.

   ![Szablon projektu aplikacji konsoli (.NET Core) w oknie dialogowym Nowy projekt w programie Visual Studio IDE](media/new-project-vb-dotnetcore-whatisyourname-console-app.png)

### <a name="add-a-workload-optional"></a>Dodawanie obciążenia (opcjonalnie)

Jeśli nie widzisz szablonu projektu **aplikacji konsoli (.NET Core),** możesz go uzyskać, dodając obciążenie **programistyczne .NET Core dla różnych platform.** To obciążenie można dodać w jeden z dwóch następujących sposobów, w zależności od tego, które aktualizacje programu Visual Studio 2017 są zainstalowane na komputerze.

#### <a name="option-1-use-the-new-project-dialog-box"></a>Opcja 1: Korzystanie z okna dialogowego Nowy projekt

1. Kliknij łącze **Otwórz instalator programu Visual Studio** w lewym okienku okna dialogowego Nowy **projekt.**

   ![Kliknij łącze Otwórz instalator programu Visual Studio w oknie dialogowym Nowy projekt](../media/vs-open-visual-studio-installer-generic.png)

1. Uruchamia instalator programu Visual Studio. Wybierz **wieloplatformowe obciążenie programistyczne .NET Core,** a następnie wybierz pozycję **Modyfikuj**.

   ![Wieloplatformowe obciążenie programowe programu .NET Core w Instalatorze programu Visual Studio](../media/tutorial-aspnet-workload.png)

#### <a name="option-2-use-the-tools-menu-bar"></a>Opcja 2: Użyj paska menu Narzędzia

1. Anulowanie z okna dialogowego **Nowy projekt** i na górnym pasku menu wybierz pozycję **Narzędzia** > **Pobierz narzędzia i funkcje**.

1. Uruchamia instalator programu Visual Studio. Wybierz **wieloplatformowe obciążenie programistyczne .NET Core,** a następnie wybierz pozycję **Modyfikuj**.

::: moniker-end

::: moniker range="vs-2019"

> [!NOTE]
> Niektóre zrzuty ekranu w tym samouczku używają ciemnego motywu. Jeśli nie używasz ciemnego motywu, ale chcesz, zobacz [Personalizuj ide programu Visual Studio i edytora](../../ide/quickstart-personalize-the-ide.md) strony, aby dowiedzieć się, jak to zrobić.

1. Otwórz program Visual Studio 2019.

1. W oknie początkowym wybierz pozycję **Utwórz nowy projekt**.

   ![Wyświetlanie okna "Tworzenie nowego projektu"](../../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. W oknie **Utwórz nowy projekt** wprowadź lub wpisz *konsolę* w polu wyszukiwania. Następnie wybierz pozycję **Visual Basic** z listy Język, a następnie wybierz pozycję **Windows** z listy Platforma. 

   Po zastosowaniu filtrów językowych i platformowych wybierz szablon **Aplikacji konsoli (NET Core),** a następnie wybierz pozycję **Dalej**.

   ![Wybieranie szablonu języka Visual Basic dla aplikacji konsoli (.NET Framework)](./media/vs-2019/vb-create-new-project-search-console-net-core-filtered.png)

   > [!NOTE]
   > Jeśli nie widzisz szablonu **aplikacji konsoli (.NET Core),** możesz go zainstalować w oknie **Utwórz nowy projekt.** W komunikacie **Nie znajdowanie tego, czego szukasz?** **Install more tools and features**
   >
   > ![Link "Zainstaluj więcej narzędzi i funkcji" z komunikatu "Nie znajdując tego, czego szukasz" w oknie "Utwórz nowy projekt"](../../get-started/media/vs-2019/not-finding-what-looking-for.png) 
   > 
   > Następnie w Instalatorze programu Visual Studio wybierz obciążenie **programistyczne .NET Core na różnych platformach.**
   >
   > ![Wieloplatformowe obciążenie programowe programu .NET Core w Instalatorze programu Visual Studio](../../get-started/media/dot-net-core-xplat-dev-workload.png)
   >
   > Następnie wybierz przycisk **Modyfikuj** w Instalatorze programu Visual Studio. Może zostać wyświetlony monit o zapisanie pracy; jeśli tak, zrób to. Następnie wybierz pozycję **Kontynuuj,** aby zainstalować obciążenie. Następnie wróć do kroku 2 w tej procedurze["Utwórz projekt".](#create-a-project)

1. W oknie **Konfigurowanie nowego projektu** wpisz lub wpisz *WhatIsYourName* w polu **Nazwa projektu.** Następnie wybierz pozycję **Utwórz**.

   ![w oknie "Skonfiguruj nowy projekt" nazwij swój projekt "WhatIsYourName"](./media/vs-2019/vb-name-your-project-whatname.png)

   Visual Studio otwiera nowy projekt.

::: moniker-end

## <a name="create-a-what-is-your-name-application"></a>Utwórz aplikację "Jak się nazywasz"

Utwórzmy aplikację, która wyświetli monit o podanie imienia i nazwiska, a następnie wyświetli ją wraz z datą i godziną. Oto kroki tej procedury:

 ::: moniker range="vs-2017"

1. Jeśli nie jest jeszcze otwarty, otwórz projekt *WhatIsYourName.*

1. Wprowadź następujący kod języka Visual Basic bezpośrednio `Sub Main(args As String())` za nawiasem `End Sub` otwierającym, który następuje po wierszu i przed wierszem:

     ```vb
     Console.WriteLine(vbCrLf + "What is your name? ")
     Dim name = Console.ReadLine()
     Dim currentDate = DateTime.Now
     Console.WriteLine($"{vbCrLf}Hello, {name}, on {currentDate:d} at {currentDate:t}")
     Console.Write(vbCrLf + "Press any key to exit... ")
     Console.ReadKey(True)
    ```

    Ten kod zastępuje <xref:System.Console.WriteLine%2A>istniejące <xref:System.Console.Write%2A>, <xref:System.Console.ReadKey%2A> i instrukcje.

   ![Okno kodu z kodem What Is Your Name](./media/vs-2019/vb-codewindow-what-name-dark.png)

1. Użyj zielonego przycisku **Start** lub naciśnij **klawisz F5,** aby utworzyć i uruchomić pierwszą aplikację.

1. Po otwarciu okna konsoli wprowadź swoje imię i nazwisko. Okno konsoli powinno wyglądać podobnie do następującego zrzutu ekranu:

   ![Okno konsoli z informacją, jaka jest Twoja nazwa, godzina i data, oraz naciśnij dowolny klawisz, aby kontynuować wiadomość](media/vb-console-what-name.png)

1. Naciśnij dowolny klawisz, aby zamknąć okno konsoli.

::: moniker-end

::: moniker range="vs-2019"

1. W projekcie *WhatIsYourName* wprowadź następujący kod języka Visual Basic bezpośrednio `Sub Main(args As String())` po nawiasie otwierającym, który następuje po wierszu i przed wierszem: `End Sub`

     ```vb
     Console.WriteLine(vbCrLf + "What is your name? ")
     Dim name = Console.ReadLine()
     Dim currentDate = DateTime.Now
     Console.WriteLine($"{vbCrLf}Hello, {name}, on {currentDate:d} at {currentDate:t}!")
     Console.Write(vbCrLf + "Press any key to exit... ")
     Console.ReadKey(True)
    ```

    Ten kod zastępuje <xref:System.Console.WriteLine%2A>istniejące <xref:System.Console.Write%2A>, <xref:System.Console.ReadKey%2A> i instrukcje.

   ![Okno kodu z kodem What Is Your Name](./media/vs-2019/vb-codewindow-what-name-dark.png)

1. Użyj zielonego przycisku **Start** lub naciśnij **klawisz F5,** aby utworzyć i uruchomić pierwszą aplikację.

1. Po otwarciu okna konsoli wprowadź swoje imię i nazwisko. Okno konsoli powinno wyglądać podobnie do następującego zrzutu ekranu:

   ![Okno konsoli z informacją, jaka jest Twoja nazwa, godzina i data, oraz naciśnij dowolny klawisz, aby kontynuować wiadomość](media/vb-console-what-name.png)

1. Naciśnij dowolny klawisz, aby zamknąć okno konsoli.

 ::: moniker-end

## <a name="create-a-calculate-this-application"></a>Tworzenie aplikacji "Oblicz to"

::: moniker range="vs-2017"

1. Otwórz program Visual Studio 2017, a następnie z górnego paska menu wybierz pozycję **Plik** > **nowego** > **projektu**.

1. W oknie dialogowym **Nowy projekt** w lewym okienku rozwiń rozwiń pozycję **Visual Basic**, a następnie wybierz pozycję **.NET Core**. W środkowym okienku wybierz pozycję **Aplikacja konsoli (.NET Core)**. Następnie nazwij plik *CalculateThis*.

1. Wprowadź następujący kod `Module Program` między `End Module` wierszem a wierszem:

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

   Okno kodu powinno wyglądać następująco:

   ![Okno kodu z kodem CalculateThis](media/vb-codewindow-calculate-this.png)

1. Kliknij **pozycję Oblicz,** aby uruchomić program. Okno konsoli powinno wyglądać podobnie do następującego zrzutu ekranu:

    ![Okno konsoli z wyświetlaną aplikacją CalculateThis, która zawiera monity o podjęcie czynności.](media/vb-console-calculate-this.png)

::: moniker-end 

::: moniker range="vs-2019"

1. W oknie początkowym wybierz pozycję **Utwórz nowy projekt**. 

1. W oknie **Utwórz nowy projekt** wprowadź lub wpisz *konsolę* w polu wyszukiwania. Następnie wybierz pozycję **Visual Basic** z listy Język, a następnie wybierz pozycję **Windows** z listy Platforma. 

1. Po zastosowaniu filtrów językowych i platformowych wybierz szablon **Aplikacji konsoli (NET Core),** a następnie wybierz pozycję **Dalej**.

   Następnie w oknie **Konfigurowanie nowego projektu** wpisz lub wprowadź *CalculateThis* w polu **Nazwa projektu.** Następnie wybierz pozycję **Utwórz**.

1. Wprowadź następujący kod `Module Program` między `End Module` wierszem a wierszem:

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

   Okno kodu powinno wyglądać następująco:

   ![Okno kodu z kodem CalculateThis](media/vb-codewindow-calculate-this.png)

1. Kliknij **pozycję Oblicz,** aby uruchomić program. Okno konsoli powinno wyglądać podobnie do następującego zrzutu ekranu:

    ![Okno konsoli z wyświetlaną aplikacją CalculateThis, która zawiera monity o podjęcie czynności.](media/vb-console-calculate-this.png)

::: moniker-end

## <a name="quick-answers-faq"></a>Szybkie odpowiedzi często zadawane pytania

Oto krótkie często zadawane pytania, aby wyróżnić kilka kluczowych pojęć.

### <a name="what-is-visual-basic"></a>Co to jest visual basic?

Visual Basic to bezpieczny dla typu język programowania, który został zaprojektowany tak, aby był łatwy do nauczenia. Pochodzi od BASIC, co oznacza "Uniwersalny symboliczny kod instrukcji dla początkujących".

### <a name="what-is-visual-studio"></a>Co to jest program Visual Studio?

Visual Studio to zintegrowany pakiet narzędzi deweloperskich dla deweloperów. Pomyśl o tym jako o programie, którego można używać do tworzenia programów i aplikacji.

### <a name="what-is-a-console-app"></a>Co to jest aplikacja konsoli?

Aplikacja konsoli pobiera dane wejściowe i wyświetla dane wyjściowe w oknie wiersza polecenia, vel konsoli.

### <a name="what-is-net-core"></a>Co to jest .NET Core?

.NET Core jest ewolucyjnym następnym krokiem programu .NET Framework. Gdzie .NET Framework umożliwia udostępnianie kodu w językach programowania, .NET Core dodaje możliwość udostępniania kodu na różnych platformach. Co więcej, jest to open source. (Zarówno .NET Framework i .NET Core obejmują biblioteki wstępnie utworzonej funkcji, a także wspólnego środowiska wykonawczego języka (CLR), który działa jako maszyna wirtualna, w której do uruchomienia kodu.)

## <a name="next-steps"></a>Następne kroki

Gratulujemy ukończenia tego samouczka! Aby dowiedzieć się więcej, zobacz poniższy samouczek.

> [!div class="nextstepaction"]
> [Tworzenie biblioteki za pomocą języka Visual Basic i rdzenia SDK .NET w programie Visual Studio](/dotnet/core/tutorials/vb-library-with-visual-studio)

## <a name="see-also"></a>Zobacz też

* [Wskazówki dotyczące języka języka Visual Basic](/dotnet/visual-basic/walkthroughs)
* [Dokumentacja języka Visual Basic](/dotnet/visual-basic/language-reference/index)
* [Pliki kodu IntelliSense for Visual Basic](../../ide/visual-basic-specific-intellisense.md)
