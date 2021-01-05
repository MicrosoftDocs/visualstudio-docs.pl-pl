---
title: Wyświetlanie zdarzeń za pomocą IntelliTrace | Microsoft Docs
description: Dowiedz się, jak za pomocą IntelliTrace w Visual Studio Enterprise zbierać dane dotyczące określonych zdarzeń, kategorii zdarzeń i pojedynczych wywołań funkcji.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e1c9c91a-0009-4c4e-9b4f-c9ab3a6022a7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6fef839b5473881450581db77a885da158e67bbc
ms.sourcegitcommit: 105e7b5a486262bc92939980383ceee068098a11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/30/2020
ms.locfileid: "97815753"
---
# <a name="view-events-with-intellitrace-in-visual-studio-enterprise-c-visual-basic"></a>Wyświetlanie zdarzeń za pomocą IntelliTrace w Visual Studio Enterprise (C#, Visual Basic)

Za pomocą IntelliTrace można zbierać informacje o określonych zdarzeniach lub kategoriach zdarzeń albo o pojedynczych wywołaniach funkcji oprócz zdarzeń. Poniższe procedury pokazują, jak to zrobić.

Możesz użyć IntelliTrace w wersji Visual Studio Enterprise, ale nie wersji Professional ani Community.

## <a name="configure-intellitrace"></a><a name="GettingStarted"></a> Konfigurowanie IntelliTrace

Możesz wypróbować debugowanie za pomocą tylko zdarzeń IntelliTrace. Zdarzenia IntelliTrace to zdarzenia debugera, wyjątki, zdarzenia .NET Framework i inne zdarzenia systemowe. Należy włączyć lub wyłączyć określone zdarzenia, aby kontrolować zdarzenia, które IntelliTrace rekordy przed rozpoczęciem debugowania. Aby uzyskać więcej informacji, zobacz [IntelliTrace Features](../debugger/intellitrace-features.md).

- Włącz zdarzenie IntelliTrace, aby uzyskać dostęp do plików. Przejdź do strony **narzędzia > opcje > IntelliTrace > IntelliTrace Events** i rozwiń kategorię **plik** . Sprawdź kategorię zdarzenia **pliku** . Powoduje to sprawdzenie wszystkich zdarzeń plików (dostęp, zamykanie, usuwanie).

## <a name="create-your-app"></a>Tworzenie aplikacji

1. Utwórz aplikację konsolową języka C#. W pliku Program.cs Dodaj następującą `using` instrukcję:

    ```csharp
    using System.IO;
    ```

2. Utwórz <xref:System.IO.FileStream> w metodzie Main, Odczytaj z niej, zamknij ją i Usuń plik. Dodaj kolejny wiersz, aby ustawić punkt przerwania:

    ```csharp
    static void Main(string[] args)
    {
        FileStream fs = File.Create("WordSearchInputs.txt");
        fs.ReadByte();
        fs.Close();
        File.Delete("WordSearchInputs.txt");

        Console.WriteLine("done");
    }
    ```

3. Ustaw punkt przerwania na `Console.WriteLine("done");`

## <a name="start-debugging-and-view-intellitrace-events"></a>Rozpocznij debugowanie i Wyświetl zdarzenia IntelliTrace

1. Rozpocznij debugowanie w zwykły sposób. (Naciśnij klawisz **F5** lub kliknij pozycję **Debuguj > Rozpocznij debugowanie**).

    > [!TIP]
    > Zachowaj otwarte okna **lokalne** i **Autotekstu** w trakcie debugowania, aby zobaczyć i zapisać wartości w tych oknach.

2. Wykonywanie jest zatrzymane w punkcie przerwania. Jeśli nie widzisz okna **Narzędzia diagnostyczne** , kliknij pozycję **Debuguj > zdarzenia IntelliTrace systemu Windows >**.

    W oknie **Narzędzia diagnostyczne** Znajdź kartę **zdarzenia** (powinny być widoczne 3 karty, **zdarzenia**, **użycie pamięci** i **użycie procesora**). Karta **zdarzenia** zawiera chronologiczną listę zdarzeń kończącą się ostatnim zdarzeniem, zanim debuger przerwał wykonywanie operacji. Powinno zostać wyświetlone zdarzenie o nazwie **WordSearchInputs.txtdostępu**.

    Poniższy zrzut ekranu pochodzi z programu Visual Studio 2015 Update 1.

    ![Zrzut ekranu przedstawiający okno programu Visual Studio Code. Wykonywanie jest zatrzymane w punkcie przerwania, a na karcie zdarzenia w oknie narzędzia diagnostyczne są wyświetlane zdarzenia.](../debugger/media/intellitrace-update1.png)

3. Wybierz zdarzenie, aby rozwinąć jego szczegóły.

    Poniższy zrzut ekranu pochodzi z programu Visual Studio 2015 Update 1.

    ![Zrzut ekranu przedstawiający kartę zdarzenia w oknie narzędzia diagnostyczne programu Visual Studio. Zdarzenie jest wybierane i rozwinięte, aby wyświetlić jego szczegóły.](../debugger/media/intellitraceupdate1-singleevent.png)

    Możesz wybrać link ścieżki, aby otworzyć plik. Jeśli pełna nazwa ścieżki jest niedostępna, pojawi się okno dialogowe **Otwórz plik** .

    Kliknij pozycję **Aktywuj debugowanie historyczne**, które ustawia kontekst debugera na czas zebrania wybranego zdarzenia, pokazując dane historyczne w **stosie wywołań**, **zmiennych lokalnych** i innych oknach debugera. Jeśli kod źródłowy jest dostępny, program Visual Studio przesuwa wskaźnik do odpowiedniego kodu w oknie źródłowym, aby można było go przeanalizować.

    Poniższy zrzut ekranu pochodzi z programu Visual Studio 2015 Update 1.

    ![Zrzut ekranu przedstawiający okno programu Visual Studio Code. Wykonywanie jest zatrzymane w punkcie przerwania, zdarzenie jest zaznaczone, a odpowiedni wiersz kodu jest wyróżniony.](../debugger/media/historicaldebugging-update1.png)

4. Jeśli usterka nie została znaleziona, spróbuj sprawdzić inne zdarzenia prowadzące do błędu. Istnieje również możliwość rejestrowania informacji o wywołaniach IntelliTrace, dzięki czemu można przechodzić przez wywołania funkcji.

## <a name="next-steps"></a>Następne kroki

Możesz użyć niektórych zaawansowanych funkcji IntelliTrace z debugowaniem historycznym:

- Aby wyświetlić migawki, zobacz [Inspekcja poprzednich stanów aplikacji przy użyciu IntelliTrace](../debugger/view-historical-application-state.md)
- Aby dowiedzieć się, jak zbadać zmienne i poruszać się po kodzie, zobacz [Inspekcja aplikacji za pomocą debugowania historycznego](../debugger/historical-debugging-inspect-app.md)
