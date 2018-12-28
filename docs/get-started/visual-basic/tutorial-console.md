---
title: 'Samouczek: Wprowadzenie do języka Visual Basic'
description: Dowiedz się, jak tworzyć aplikacje konsoli języka Visual Basic w programie Visual Studio krok po kroku.
ms.custom: seodec18, get-started
ms.date: 08/10/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: tutorial
ms.devlang: vb
author: TerryGLee
ms.author: tglee
manager: douge
dev_langs:
- vb
ms.workload:
- multiple
ms.openlocfilehash: 076d8ed69e742ccb228af26a10ec5f9e76767a70
ms.sourcegitcommit: a715de2ba8c703f37aa2102567b1aa2c0f05a117
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2018
ms.locfileid: "53443486"
---
# <a name="tutorial-get-started-with-visual-basic-in-visual-studio"></a>Samouczek: Wprowadzenie do języka Visual Basic w programie Visual Studio

W ramach tego samouczka dla języka Visual Basic (VB), użyjesz programu Visual Studio, aby utworzyć i uruchomić kilka aplikacji konsolowych różnych i zapoznaj się z niektórymi funkcjami [środowiska zintegrowanego rozwoju Visual Studio (IDE)](visual-studio-ide.md) podczas możesz to zrobić.

Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [program Visual Studio pobiera](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) strony, aby zainstalować go za darmo.

## <a name="create-a-project"></a>Tworzenie projektu

Najpierw utworzymy projekt aplikacji w języku Visual Basic. Typ projektu jest dostarczany z wszystkie pliki szablonu, które będą potrzebne, zanim dodaniu jeszcze nic!

1. Otwórz program Visual Studio 2017.

2. Na pasku menu u góry wybierz **pliku** > **New** > **projektu**.

3. W **nowy projekt** okno dialogowe w okienku po lewej stronie rozwiń **języka Visual Basic**, a następnie wybierz **platformy .NET Core**. W środkowym okienku wybierz **Aplikacja konsoli (.NET Core)**. Następnie Nazwij plik *HelloWorld*.

   ![Szablon projektu aplikacji (.NET Core) w oknie dialogowym Nowy projekt w programie Visual Studio IDE konsoli](media/new-project-vb-dotnetcore-whatisyourname-console-app.png)

### <a name="add-a-workgroup-optional"></a>Dodaj grupy roboczej (opcjonalnie)

Jeśli nie widzisz **Aplikacja konsoli (.NET Core)** szablon projektu, możesz ją uzyskać, dodając **programowanie dla wielu platform .NET Core** obciążenia. Można dodać tego obciążenia w jednej z dwóch sposobów, zależności od tego, które aktualizacje programu Visual Studio 2017 są instalowane na komputerze.

#### <a name="option-1-use-the-new-project-dialog-box"></a>Opcja 1: Użyj okna dialogowego Nowy projekt

1. Kliknij przycisk **Otwórz Instalator programu Visual Studio** łącze w okienku po lewej stronie **nowy projekt** okno dialogowe.

   ![Kliknij link Otwórz Instalator programu Visual Studio z okna dialogowego Nowy projekt](../media/vs-open-visual-studio-installer-generic.png)

1. Uruchamia Instalatora programu Visual Studio. Wybierz **programowanie dla wielu platform .NET Core** obciążenia, a następnie wybierz **Modyfikuj**.

   ![Obciążenia programowanie dla wielu platform .NET core w Instalatorze programu Visual Studio](../media/tutorial-aspnet-workload.png)

#### <a name="option-2-use-the-tools-menu-bar"></a>Opcja 2: Użyj paska menu Narzędzia

1. Anuluj poza **nowy projekt** okna dialogowego pole, a następnie na pasku menu u góry wybierz **narzędzia** > **Pobierz narzędzia i funkcje**.

1. Uruchamia Instalatora programu Visual Studio. Wybierz **programowanie dla wielu platform .NET Core** obciążenia, a następnie wybierz **Modyfikuj**.

## <a name="create-a-what-is-your-name-application"></a>Tworzenie aplikacji "Co to jest Twój Name"

Utwórz aplikację, która wyświetli monit o podanie nazwy użytkownika i wyświetla go wraz z daty i godziny. Oto jak:

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

   ![Okno kodu, kod co to jest nazwa użytkownika](media/vb-codewindow-what-name.png)

1. Po otwarciu okna konsoli, wprowadź nazwę. Okna konsoli powinien wyglądać podobnie do poniższej zrzut ekranu:

   ![Wyświetlana co to jest imię i nazwisko, datę i godzinę w oknie konsoli, a następnie naciśnij dowolny klawisz, aby kontynuować, wiadomości](media/vb-console-what-name.png)

1. Naciśnij dowolny klawisz, aby zamknąć okno konsoli.

## <a name="create-a-calculate-this-application"></a>Tworzenie aplikacji "Oblicz to"

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

   ![Wyświetlana Calculate ten kod w oknie kodu](media/vb-codewindow-calculate-this.png)

1. Kliknij przycisk **CalculateThis** Aby uruchomić program. Okna konsoli powinien wyglądać podobnie do poniższej zrzut ekranu:

    ![Okno konsoli przedstawiający aplikację CaluculateThis, która obejmuje monity w przypadku działania, które należy podjąć.](media/vb-console-calculate-this.png)

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
> [Samouczek wideo: Podstawy Visual Basic dla całkowicie początkujących](https://mva.microsoft.com/en-us/training-courses/visual-basic-fundamentals-for-absolute-beginners-16507)

## <a name="see-also"></a>Zobacz także

* [Co nowego w języku Visual Basic](/dotnet/visual-basic/getting-started/whats-new)
* [Funkcja IntelliSense w plikach kodu języka Visual Basic](../../ide/visual-basic-specific-intellisense.md)
* [Odwołanie językowe Visual Basic](/dotnet/visual-basic/language-reference/index)