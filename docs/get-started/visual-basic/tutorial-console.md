---
title: 'Samouczek: wprowadzenie do Visual Basic'
description: Dowiedz się, jak Visual Basic konsolowe w Visual Studio, jak tworzyć aplikacje konsolowe w Visual Studio, jak to zrobić krok po kroku.
ms.custom: vs-acquisition,  get-started
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
ms.openlocfilehash: 8d34fef6251da95b6c3ac99430b87d853d4b5ba7
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390714"
---
# <a name="tutorial-get-started-with-visual-basic-in-visual-studio"></a>Samouczek: rozpoczynanie pracy z Visual Basic w Visual Studio

W tym samouczku dla programu Visual Basic (VB) użyjesz programu Visual Studio do utworzenia i uruchomienia kilku różnych aplikacji konsolowych oraz poznasz niektóre funkcje zintegrowanego środowiska projektowego [(IDE)](visual-studio-ide.md) usługi Visual Studio.

::: moniker range="vs-2017"

Jeśli jeszcze nie zainstalowano aplikacji Visual Studio, przejdź [](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) do strony pobierania Visual Studio, aby zainstalować ją bezpłatnie.

::: moniker-end

::: moniker range="vs-2019"

Jeśli jeszcze nie zainstalowano aplikacji Visual Studio, przejdź [](https://visualstudio.microsoft.com/downloads) do strony pobierania Visual Studio, aby zainstalować ją bezpłatnie.

::: moniker-end

::: moniker range="vs-2022"

Jeśli jeszcze nie zainstalowano programu Visual Studio 2022 (wersja zapoznawcza), przejdź do strony pobierania programu [Visual Studio 2022 Preview,](https://visualstudio.microsoft.com/vs/preview/vs2022) aby zainstalować ją bezpłatnie.

::: moniker-end

## <a name="create-a-project"></a>Tworzenie projektu

Najpierw utworzymy projekt aplikacji Visual Basic aplikacji. Typ projektu zawiera wszystkie potrzebne pliki szablonów, zanim jeszcze cokolwiek dodano.

::: moniker range="vs-2017"

1. Otwórz program Visual Studio 2017.

2. Na górnym pasku menu wybierz pozycję **File** New Project > **(Plik nowy** > **projekt).**

3. W **oknie dialogowym Nowy** projekt w okienku po lewej stronie **rozwiń** pozycję Visual Basic , a następnie wybierz **pozycję .NET Core.** W środkowym okienku wybierz pozycję **Aplikacja konsoli (.NET Core).** Następnie nadaj *projektowi nazwę WhatIsYourName*.

   ![Szablon projektu aplikacja konsolowa (.NET Core) w oknie dialogowym Nowy projekt w Visual Studio IDE](media/new-project-vb-dotnetcore-whatisyourname-console-app.png)

### <a name="add-a-workload-optional"></a>Dodawanie obciążenia (opcjonalnie)

Jeśli nie widzisz szablonu projektu Aplikacja konsolowa **(.NET Core),** możesz go pobrać, dodając obciążenie tworzenie aplikacji dla wielu platform na **platformie .NET Core.** To obciążenie można dodać na jeden z dwóch następujących sposobów, w zależności od tego, Visual Studio zainstalowano aktualizacje programu 2017 na maszynie.

#### <a name="option-1-use-the-new-project-dialog-box"></a>Opcja 1. Korzystanie z okna dialogowego Nowy projekt

1. Kliknij link **Otwórz Instalator programu Visual Studio** w lewym okienku okna **dialogowego Nowy** projekt.

   ![Kliknij link Otwórz Instalator programu Visual Studio w oknie dialogowym Nowy projekt](../media/vs-open-visual-studio-installer-generic.png)

1. Ta Instalator programu Visual Studio uruchamia się. Wybierz obciążenie **Tworzenie aplikacji dla wielu platform na platformie .NET Core,** a następnie wybierz pozycję **Modyfikuj.**

   ![Międzyplatformowe obciążenie programowe platformy .NET Core w chmurze Instalator programu Visual Studio](../media/tutorial-aspnet-workload.png)

#### <a name="option-2-use-the-tools-menu-bar"></a>Opcja 2. Korzystanie z paska menu Narzędzia

1. Anuluj poza oknom **dialogowym Nowy** projekt i na górnym pasku menu wybierz pozycję **Narzędzia** Pobierz narzędzia > **i funkcje.**

1. Ta Instalator programu Visual Studio uruchamia się. Wybierz obciążenie **Tworzenie aplikacji dla wielu platform na platformie .NET Core,** a następnie wybierz pozycję **Modyfikuj.**

::: moniker-end

::: moniker range=">=vs-2019"

> [!NOTE]
> Niektóre zrzuty ekranu w tym samouczku używają ciemnego motywu. Jeśli nie używasz motywu ciemnego, ale chcesz, zobacz stronę Personalizowanie środowiska [IDE](../../ide/quickstart-personalize-the-ide.md) i edytora Visual Studio, aby dowiedzieć się, jak to zrobić.

1. Otwórz program Visual Studio.

1. W oknie uruchamiania wybierz **pozycję Utwórz nowy projekt.**

   ![Wyświetlanie okna "Tworzenie nowego projektu"](../../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. W **oknie Tworzenie nowego projektu** wybierz pozycję **Visual Basic** z listy Język. Następnie wybierz pozycję **Windows** z listy Platforma i **pozycję Konsola** z listy typów projektów.

   Po zastosowaniu filtrów języka, platformy i typu projektu wybierz szablon **Aplikacja konsolowa,** a następnie wybierz pozycję **Dalej.**

   :::image type="content" source="./media/vs-2019/vb-create-new-project-console-net-core.png" alt-text="Wybieranie Visual Basic szablonu aplikacji konsolowej":::

   > [!NOTE]
   > Jeśli nie widzisz szablonu **Aplikacja konsolowa,** możesz go zainstalować w oknie Tworzenie **nowego** projektu. W **komunikacie Nie** można znaleźć tego, czego szukasz? wybierz link Zainstaluj **więcej narzędzi i** funkcji.
   >
   > ![Link "Zainstaluj więcej narzędzi i funkcji" w komunikacie "Nie można znaleźć tego, czego szukasz" w oknie "Tworzenie nowego projektu"](../../get-started/media/vs-2019/not-finding-what-looking-for.png) 
   > 
   > Następnie w chmurze Instalator programu Visual Studio obciążenie Tworzenie aplikacji dla wielu platform dla **platformy .NET Core.**
   >
   > ![Międzyplatformowe obciążenie programowe platformy .NET Core w chmurze Instalator programu Visual Studio](../../get-started/media/dot-net-core-xplat-dev-workload.png)
   >
   > Następnie wybierz przycisk **Modyfikuj** w Instalator programu Visual Studio. Może zostać wyświetlony monit o zapisanie pracy. Jeśli tak, zrób to. Następnie wybierz pozycję **Kontynuuj,** aby zainstalować obciążenie. Następnie wróć do kroku 2 w procedurze["Tworzenie projektu".](#create-a-project)

1. W **oknie Konfigurowanie nowego** projektu wpisz lub wprowadź *WhatIsYourName* w **polu Nazwa** projektu. Następnie wybierz pozycję **Dalej.**

   :::image type="content" source="./media/vs-2019/vb-name-your-project-whatname.png" alt-text="W oknie &quot;Konfigurowanie nowego projektu&quot; nadaj projektowi nazwę &quot;WhatIsYourName&quot;":::

1. W **oknie Dodatkowe informacje** dla struktury docelowej należy już wybrać platformę **.NET Core 3.1.** Jeśli nie, wybierz **pozycję .NET Core 3.1.** Następnie wybierz pozycję **Utwórz**.

   :::image type="content" source="./media/vs-2019/vb-target-framework.png" alt-text="W oknie &quot;Dodatkowe informacje&quot; upewnij się, że wybrano opcję .NET Core 3.1":::

   Visual Studio otworzy nowy projekt.

::: moniker-end

## <a name="create-a-what-is-your-name-application"></a>Tworzenie aplikacji "What Is Your Name" (Jaka jest Twoja nazwa)

Utwórzmy aplikację, która wyświetli monit o Twoją nazwę, a następnie wyświetli ją wraz z datą i godziną. Oto kroki tej procedury:

 ::: moniker range="vs-2017"

1. Jeśli nie jest jeszcze otwarty, otwórz projekt *WhatIsYourName.*

1. Wprowadź następujący kod Visual Basic bezpośrednio po nawiasie otwierającym, który następuje po wierszu `Sub Main(args As String())` i przed `End Sub` wierszem:

     ```vb
     Console.WriteLine(vbCrLf + "What is your name? ")
     Dim name = Console.ReadLine()
     Dim currentDate = DateTime.Now
     Console.WriteLine($"{vbCrLf}Hello, {name}, on {currentDate:d} at {currentDate:t}")
     Console.Write(vbCrLf + "Press any key to exit... ")
     Console.ReadKey(True)
    ```

    Ten kod zastępuje istniejące <xref:System.Console.WriteLine%2A> instrukcje <xref:System.Console.Write%2A> , i <xref:System.Console.ReadKey%2A> .

   ![Okno kodów z kodem What Is Your Name](./media/vs-2019/vb-codewindow-what-name-dark.png)

1. Użyj zielonego **przycisku Start** lub naciśnij **klawisz F5,** aby skompilować i uruchomić pierwszą aplikację.

1. Po otworowym oknie konsoli wprowadź swoją nazwę. Okno konsoli powinno wyglądać podobnie do poniższego zrzutu ekranu:

   ![Okno konsoli z wyświetlonymi informacjami What Is Your Name (Jakie jest Twoje imię, godzina i data) oraz Naciśnij dowolny klawisz, aby kontynuować komunikat](media/vb-console-what-name.png)

1. Naciśnij dowolny klawisz, aby zamknąć okno konsoli.

::: moniker-end

::: moniker range=">=vs-2019"

1. W *projekcie WhatIsYourName* wprowadź następujący kod Visual Basic bezpośrednio po nawiasie otwierającym, który następuje po wierszu i `Sub Main(args As String())` przed `End Sub` wierszem:

     ```vb
     Console.WriteLine(vbCrLf + "What is your name? ")
     Dim name = Console.ReadLine()
     Dim currentDate = DateTime.Now
     Console.WriteLine($"{vbCrLf}Hello, {name}, on {currentDate:d} at {currentDate:t}!")
     Console.Write(vbCrLf + "Press any key to exit... ")
     Console.ReadKey(True)
    ```

    Ten kod zastępuje istniejące <xref:System.Console.WriteLine%2A> instrukcje <xref:System.Console.Write%2A> , i <xref:System.Console.ReadKey%2A> .

   ![Okno kodów z kodem What Is Your Name](./media/vs-2019/vb-codewindow-what-name-dark.png)

1. Użyj zielonego **przycisku Start** lub naciśnij **klawisz F5,** aby skompilować i uruchomić pierwszą aplikację.

1. Po otworowym oknie konsoli wprowadź swoją nazwę. Okno konsoli powinno wyglądać podobnie do poniższego zrzutu ekranu:

   ![Okno konsoli z wyświetlonymi informacjami What Is Your Name (Jakie jest Twoje imię, godzina i data) oraz Naciśnij dowolny klawisz, aby kontynuować komunikat](media/vb-console-what-name.png)

1. Naciśnij dowolny klawisz, aby zamknąć okno konsoli.

 ::: moniker-end

## <a name="create-a-calculate-this-application"></a>Tworzenie aplikacji "Oblicz to"

::: moniker range="vs-2017"

1. Otwórz Visual Studio 2017 r., a następnie na górnym pasku menu wybierz pozycję File New Project **(Nowy** > **projekt:** > **plik).**

1. W **oknie dialogowym Nowy** projekt w okienku po lewej stronie **rozwiń** pozycję Visual Basic , a następnie wybierz **pozycję .NET Core.** W środkowym okienku wybierz pozycję **Aplikacja konsoli (.NET Core).** Następnie nadaj *plikowi nazwę CalculateThis*.

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

   Okno kodu powinno wyglądać jak na poniższym zrzucie ekranu:

   ![Okno kodu z kodem CalculateThis](media/vb-codewindow-calculate-this.png)

1. Kliknij **pozycję CalculateThis ,aby** uruchomić program. Okno konsoli powinno wyglądać podobnie do poniższego zrzutu ekranu:

    ![Okno konsoli z wyświetloną aplikacją CalculateThis, która zawiera monity dotyczące akcji do podjęcia.](media/vb-console-calculate-this.png)

::: moniker-end 

::: moniker range=">=vs-2019"

1. W oknie uruchamiania wybierz **pozycję Utwórz nowy projekt.** 

1. W **oknie Tworzenie nowego projektu** wybierz pozycję **Visual Basic** z listy Język. Następnie wybierz pozycję **Windows** z listy Platforma i **pozycję Konsola** z listy typów projektów.

1. Po zastosowaniu filtrów języka, platformy i typu projektu wybierz szablon **Aplikacja konsolowa,** a następnie wybierz pozycję **Dalej.**

   Następnie w **oknie Konfigurowanie nowego** projektu wpisz lub wprowadź *calculatethis* w **polu Nazwa** projektu. Następnie wybierz pozycję **Dalej.**

1. W **oknie Dodatkowe informacje** dla struktury docelowej należy już wybrać platformę **.NET Core 3.1.** Jeśli nie, wybierz **pozycję .NET Core 3.1.** Następnie wybierz pozycję **Utwórz**.

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

   Okno kodu powinno wyglądać jak na poniższym zrzucie ekranu:

   ![Okno kodu z kodem CalculateThis](media/vb-codewindow-calculate-this.png)

1. Kliknij **pozycję CalculateThis ,aby** uruchomić program. Okno konsoli powinno wyglądać podobnie do poniższego zrzutu ekranu:

    ![Okno konsoli z wyświetloną aplikacją CalculateThis, która zawiera monity dotyczące akcji do podjęcia.](media/vb-console-calculate-this.png)

::: moniker-end

## <a name="quick-answers-faq"></a>Często zadawane pytania dotyczące szybkich odpowiedzi

Poniżej znajdziesz krótkie często zadawane pytania, aby wyróżnić niektóre kluczowe pojęcia.

### <a name="what-is-visual-basic"></a>Co to jest Visual Basic?

Visual Basic to bezpieczny dla typów język programowania, który zaprojektowano tak, aby był łatwy do nauczenia się. Pochodzi od klasy BASIC, co oznacza "podstawowy kod instrukcji symbolicznej" dla początkujących.

### <a name="what-is-visual-studio"></a>Co to jest Visual Studio?

Visual Studio to zintegrowany pakiet programistów narzędzi zwiększających produktywność dla deweloperów. Pomyśl o nim jak o programie, który umożliwia tworzenie programów i aplikacji.

### <a name="what-is-a-console-app"></a>Co to jest aplikacja konsolowa?

Aplikacja konsolowa przyjmuje dane wejściowe i wyświetla dane wyjściowe w oknie wiersza polecenia, nazywanym również konsolą.

### <a name="what-is-net-core"></a>Co to jest .NET Core?

.NET Core to ewolucyjny następny krok .NET Framework. Tam, .NET Framework udostępniać kod w różnych językach programowania, program .NET Core dodaje możliwość udostępniania kodu między platformami. Jeszcze lepiej, jest to open source. (Zarówno środowisko .NET Framework, jak i .NET Core zawierają biblioteki wstępnie utworzonych funkcji, a także środowisko uruchomieniowe języka wspólnego (CLR), które działa jako maszyna wirtualna, na której ma być uruchamiany kod).

## <a name="next-steps"></a>Następne kroki

Gratulujemy ukończenia tego samouczka! Aby dowiedzieć się więcej, zobacz poniższy samouczek.

> [!div class="nextstepaction"]
> [Tworzenie biblioteki za pomocą Visual Basic i zestaw .NET Core SDK w Visual Studio](/dotnet/core/tutorials/vb-library-with-visual-studio)

## <a name="see-also"></a>Zobacz też

* [Visual Basic przewodnik po języku](/dotnet/visual-basic/walkthroughs)
* [Dokumentacja języka Visual Basic](/dotnet/visual-basic/language-reference/index)
* [Funkcja IntelliSense Visual Basic plików kodu](../../ide/visual-basic-specific-intellisense.md)
