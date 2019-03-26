---
title: 'Samouczek: Wprowadzenie do języka Visual Basic'
description: Dowiedz się, jak tworzyć aplikacje konsoli języka Visual Basic w programie Visual Studio krok po kroku.
ms.custom: seodec18, get-started
ms.date: 03/23/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
ms.devlang: vb
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- vb
ms.workload:
- multiple
ms.openlocfilehash: ee6866e2f40f70e2f804dc9b61b0db21c213232f
ms.sourcegitcommit: 489aca71046fb6e4aafd0a4509cd7dc149d707b1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2019
ms.locfileid: "58416172"
---
# <a name="tutorial-get-started-with-visual-basic-in-visual-studio"></a>Samouczek: Wprowadzenie do języka Visual Basic w programie Visual Studio

W ramach tego samouczka dla języka Visual Basic (VB), użyjesz programu Visual Studio, aby utworzyć i uruchomić kilka aplikacji konsolowych różnych i zapoznaj się z niektórymi funkcjami [środowiska zintegrowanego rozwoju Visual Studio (IDE)](visual-studio-ide.md) podczas możesz to zrobić.

::: moniker range="vs-2017"

Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [program Visual Studio pobiera](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) strony, aby zainstalować go za darmo.

::: moniker-end

::: moniker range="vs-2019"

Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [program Visual Studio pobiera](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019+rc) strony, aby zainstalować go za darmo.

::: moniker-end

## <a name="create-a-project"></a>Tworzenie projektu

Najpierw utworzymy projekt aplikacji w języku Visual Basic. Typ projektu jest dostarczany z wszystkie pliki szablonu, które będą potrzebne, zanim dodaniu jeszcze nic!

::: moniker range="vs-2017"

1. Otwórz program Visual Studio 2017.

2. Na pasku menu u góry wybierz **pliku** > **New** > **projektu**.

3. W **nowy projekt** okno dialogowe w okienku po lewej stronie rozwiń **języka Visual Basic**, a następnie wybierz **platformy .NET Core**. W środkowym okienku wybierz **Aplikacja konsoli (.NET Core)**. Następnie Nazwij plik *HelloWorld*.

   ![Szablon projektu aplikacji (.NET Core) w oknie dialogowym Nowy projekt w programie Visual Studio IDE konsoli](media/new-project-vb-dotnetcore-whatisyourname-console-app.png)

### <a name="add-a-workload-optional"></a>Dodaj obciążenie (opcjonalnie)

Jeśli nie widzisz **Aplikacja konsoli (.NET Core)** szablon projektu, możesz ją uzyskać, dodając **programowanie dla wielu platform .NET Core** obciążenia. Można dodać tego obciążenia w jednej z dwóch sposobów, zależności od tego, które aktualizacje programu Visual Studio 2017 są instalowane na komputerze.

#### <a name="option-1-use-the-new-project-dialog-box"></a>Option 1: Użyj okna dialogowego Nowy projekt

1. Kliknij przycisk **Otwórz Instalator programu Visual Studio** łącze w okienku po lewej stronie **nowy projekt** okno dialogowe.

   ![Kliknij link Otwórz Instalator programu Visual Studio z okna dialogowego Nowy projekt](../media/vs-open-visual-studio-installer-generic.png)

1. Uruchamia Instalatora programu Visual Studio. Wybierz **programowanie dla wielu platform .NET Core** obciążenia, a następnie wybierz **Modyfikuj**.

   ![Obciążenia programowanie dla wielu platform .NET core w Instalatorze programu Visual Studio](../media/tutorial-aspnet-workload.png)

#### <a name="option-2-use-the-tools-menu-bar"></a>Option 2: Użyj paska menu Narzędzia

1. Anuluj poza **nowy projekt** okna dialogowego pole, a następnie na pasku menu u góry wybierz **narzędzia** > **Pobierz narzędzia i funkcje**.

1. Uruchamia Instalatora programu Visual Studio. Wybierz **programowanie dla wielu platform .NET Core** obciążenia, a następnie wybierz **Modyfikuj**.

::: moniker-end

::: moniker range="vs-2019"

> [!NOTE]
> Niektóre zrzuty ekranu, w tym samouczku Użyj ciemnego motywu. Jeśli nie używasz motyw ciemny, ale aby zobaczyć [Personalizowanie programu Visual Studio IDE i edytorem](../../ide/quickstart-personalize-the-ide.md) strony, aby dowiedzieć się, jak.

1. Open Visual Studio 2019.

1. W oknie rozpoczęcia wybierz **Utwórz nowy projekt**.

   ![Wyświetlanie w oknie "Tworzenie nowego projektu"](../../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. Na **Utwórz nowy projekt** oknie wprowadź lub wpisz *konsoli* w polu wyszukiwania. Następnie wybierz pozycję **języka Visual Basic** od języka, a następnie wybierz **Windows** z listy Platform. 

   Po zastosowaniu filtrów języka i platformy, wybierz **Aplikacja konsoli (.NET Core)** szablonu, a następnie wybierz **dalej**.

   ![Wybierz szablon języka Visual Basic dla aplikacji konsoli (.NET Framework)](./media/vs-2019/vb-create-new-project-search-console-net-core-filtered.png)

   > [!NOTE]
   > Jeśli nie widzisz **Aplikacja konsoli (.NET Core)** szablonu, można zainstalować go z **Utwórz nowy projekt** okna. W **nie znaleźć, czego szukasz?** komunikatu, wybierz polecenie **zainstalować więcej narzędzi i funkcji** łącza.
   >
   > ![Łącza "Zainstaluj więcej narzędzi i funkcji" komunikat "Nie możesz znaleźć teraz wyszukiwanie" w oknie "Tworzenie nowego projektu"](../../get-started/media/vs-2019/not-finding-what-looking-for.png) 
   > 
   > Następnie w Instalatorze programu Visual Studio, wybierz **programowanie dla wielu platform .NET Core** obciążenia.
   >
   > ![Obciążenia programowanie dla wielu platform .NET core w Instalatorze programu Visual Studio](../../get-started/media/dot-net-core-xplat-dev-workload.png)
   >
   > Następnie należy wybrać **Modyfikuj** przycisku w Instalatorze programu Visual Studio. Może zostać wyświetlony monit, aby zapisać swoją pracę; Jeśli tak, należy to zrobić. Następnie wybierz pozycję **Kontynuuj** do zainstalowania z obciążeniem. Następnie wróć do kroku 2, w tym "[Utwórz projekt](#create-a-project)" procedury.

1. W **konfigurowania nowego projektu** oknie wpisz lub wprowadź *WhatIsYourName* w **Nazwa projektu** pole. Następnie wybierz **Utwórz**.

   ![w oknie "Konfigurowanie nowego projektu" nazwij swój projekt "WhatIsYourName"](./media/vs-2019/vb-name-your-project.-whatname.png)

   Visual Studio otwiera nowy projekt.

::: moniker-end

## <a name="create-a-what-is-your-name-application"></a>Tworzenie aplikacji "Co to jest Twój Name"

Utwórz aplikację, która wyświetli monit o podanie nazwy użytkownika i wyświetla go wraz z daty i godziny. Oto jak:

 ::: moniker range="vs-2017"

1. Jeśli jeszcze nie jest otwarty kolejno swoje *WhatIsYourName* projektu.

1. Wprowadź następujący kod w języku Visual Basic natychmiast po nawiasie otwierającym, który następuje po `Sub Main(args As String())` wierszu i przed `End Sub` wiersza:

     ```vb
     Console.WriteLine(vbCrLf + "What is your name? ")
     Dim name = Console.ReadLine()
     Dim currentDate = DateTime.Now
     Console.WriteLine($"{vbCrLf}Hello, {name}, on {currentDate:d} at {currentDate:t}")
     Console.Write(vbCrLf + "Press any key to exit... ")
     Console.ReadKey(True)
    ```

    Ten kod zastępuje istniejące <xref:System.Console.WriteLine%2A>, <xref:System.Console.Write%2A>, i <xref:System.Console.ReadKey%2A> instrukcji.

   ![Okno kodu, kod co to jest nazwa użytkownika](./media/vs-2019/vb-codewindow-what-name-dark.png)

1. Po otwarciu okna konsoli, wprowadź nazwę. Okna konsoli powinien wyglądać podobnie do poniższej zrzut ekranu:

   ![Wyświetlana co to jest imię i nazwisko, datę i godzinę w oknie konsoli, a następnie naciśnij dowolny klawisz, aby kontynuować, wiadomości](media/vb-console-what-name.png)

1. Naciśnij dowolny klawisz, aby zamknąć okno konsoli.

::: moniker-end

::: moniker range="vs-2019"

1. W *WhatIsYourName* projektu, wprowadź następujący kod w języku Visual Basic natychmiast po nawiasie otwierającym, który następuje po `Sub Main(args As String())` wierszu i przed `End Sub` wiersza:

     ```vb
     Console.WriteLine(vbCrLf + "What is your name? ")
     Dim name = Console.ReadLine()
     Dim currentDate = DateTime.Now
     Console.WriteLine($"{vbCrLf}Hello, {name}, on {currentDate:d} at {currentDate:t}")
     Console.Write(vbCrLf + "Press any key to exit... ")
     Console.ReadKey(True)
    ```

    Ten kod zastępuje istniejące <xref:System.Console.WriteLine%2A>, <xref:System.Console.Write%2A>, i <xref:System.Console.ReadKey%2A> instrukcji.

   ![Okno kodu, kod co to jest nazwa użytkownika](./media/vs-2019/vb-codewindow-what-name-dark.png)

1. Po otwarciu okna konsoli, wprowadź nazwę. Okna konsoli powinien wyglądać podobnie do poniższej zrzut ekranu:

   ![Wyświetlana co to jest imię i nazwisko, datę i godzinę w oknie konsoli, a następnie naciśnij dowolny klawisz, aby kontynuować, wiadomości](media/vb-console-what-name.png)

1. Naciśnij dowolny klawisz, aby zamknąć okno konsoli.

 ::: moniker-end

## <a name="create-a-calculate-this-application"></a>Tworzenie aplikacji "Oblicz to"

::: moniker range="vs-2017"

1. Otwórz program Visual Studio 2017, a następnie na pasku menu u góry wybierz **pliku** > **New** > **projektu**.

1. W **nowy projekt** okno dialogowe w okienku po lewej stronie rozwiń **języka Visual Basic**, a następnie wybierz **platformy .NET Core**. W środkowym okienku wybierz **Aplikacja konsoli (.NET Core)**. Następnie Nazwij plik *CalculateThis*.

1. Wprowadź następujący kod między `Module Program` wiersza i `End Module` wiersza:

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

   W oknie Kod powinien wyglądać podobnie Poniższy zrzut ekranu:

   ![Okno kodu, kod CalculateThis](media/vb-codewindow-calculate-this.png)

1. Kliknij przycisk **CalculateThis** Aby uruchomić program. Okna konsoli powinien wyglądać podobnie do poniższej zrzut ekranu:

    ![Okno konsoli przedstawiający aplikację CalculateThis, która obejmuje monity w przypadku działania, które należy podjąć.](media/vb-console-calculate-this.png)

::: moniker-end 

::: moniker range="vs-2019"

1. W oknie rozpoczęcia wybierz **Utwórz nowy projekt**. 

1. Na **Utwórz nowy projekt** oknie wprowadź lub wpisz *konsoli* w polu wyszukiwania. Następnie wybierz pozycję **języka Visual Basic** od języka, a następnie wybierz **Windows** z listy Platform. 

1. Po zastosowaniu filtrów języka i platformy, wybierz **Aplikacja konsoli (.NET Core)** szablonu, a następnie wybierz **dalej**.

   Następnie w **konfigurowania nowego projektu** oknie wpisz lub wprowadź *WhatIsYourName* w **Nazwa projektu** pole. Następnie wybierz pozycję **Utwórz**.

1. Wprowadź następujący kod między `Module Program` wiersza i `End Module` wiersza:

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

   W oknie Kod powinien wyglądać podobnie Poniższy zrzut ekranu:

   ![Okno kodu, kod CalculateThis](media/vb-codewindow-calculate-this.png)

1. Kliknij przycisk **CalculateThis** Aby uruchomić program. Okna konsoli powinien wyglądać podobnie do poniższej zrzut ekranu:

    ![Okno konsoli przedstawiający aplikację CalculateThis, która obejmuje monity w przypadku działania, które należy podjąć.](media/vb-console-calculate-this.png)

::: moniker-end

## <a name="quick-answers-faq"></a>Szybkie odpowiedzi na często zadawane pytania

Poniżej przedstawiono listę często zadawanych PYTAŃ szybkiego aby zaznaczyć kilka podstawowych pojęć.

### <a name="what-is-visual-basic"></a>Co to jest Visual Basic?

Visual Basic to bezpieczny typowo język programowania, który ustalono, aby były łatwe dowiedzieć się więcej. Jest on uzyskiwany z BASIC, co oznacza "Dla początkujących uniwersalny symboliczne instrukcji kod".

### <a name="what-is-visual-studio"></a>Co to jest program Visual Studio?

Program Visual Studio jest zintegrowanego rozwoju pakietu narzędzi zwiększających produktywność dla deweloperów. Go traktować jako program, który służy do tworzenia aplikacji i programów.

### <a name="what-is-a-console-app"></a>Co to jest aplikacją konsoli?

Aplikacja konsoli akceptuje dane wejściowe i wyświetla dane wyjściowe w oknie wiersza polecenia, zwanego również Konsola.

### <a name="what-is-net-core"></a>Co to jest .NET Core?

Platforma .NET core to ewolucyjny następnym krokiem programu .NET Framework. Gdzie programu .NET Framework mogą pozwala na udostępnianie kodu w językach programowania .NET Core dodaje możliwość udostępniania kodu między platformami. Jeszcze lepiej jest "open source". (.NET Framework i .NET Core zawierają biblioteki, wbudowanych funkcji, jak również środowisko uruchomieniowe języka wspólnego (CLR), który działa jako maszyna wirtualna, w którym ma być uruchamiany kod).

## <a name="next-steps"></a>Następne kroki

Gratulujemy wykonanie kroków tego samouczka! Aby uzyskać jeszcze więcej, zobacz następujące samouczki.

> [!div class="nextstepaction"]
> [Tworzenie biblioteki w języku Visual Basic i .NET Core SDK w programie Visual Studio](/dotnet/core/tutorials/vb-library-with-visual-studio)

## <a name="see-also"></a>Zobacz także

* [Wskazówki dotyczące języka Visual Basic](/dotnet/visual-basic/walkthroughs)
* [Odwołanie językowe Visual Basic](/dotnet/visual-basic/language-reference/index)
* [Funkcja IntelliSense w plikach kodu języka Visual Basic](../../ide/visual-basic-specific-intellisense.md)
