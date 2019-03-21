---
title: Wyświetlanie zdarzeń za pomocą funkcji IntelliTrace | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e1c9c91a-0009-4c4e-9b4f-c9ab3a6022a7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0ffbe0b8365948dc5a69edca390f308cb55ba5a3
ms.sourcegitcommit: 3d37c2460584f6c61769be70ef29c1a67397cf14
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2019
ms.locfileid: "58323441"
---
# <a name="view-events-with-intellitrace-in-visual-studio-enterprise-c-visual-basic"></a>Wyświetlanie zdarzeń za pomocą funkcji IntelliTrace w programie Visual Studio Enterprise (C#, Visual Basic)

Dodatkowo do zebrania informacji dotyczących określonych zdarzeń lub kategorie zdarzeń, lub wywołania funkcji poszczególnych zdarzeń, można użyć funkcji IntelliTrace. Poniższe procedury pokazują, jak to zrobić.

Za pomocą funkcji IntelliTrace w programie Visual Studio Enterprise, ale nie w wersjach Professional lub Community.

## <a name="GettingStarted"></a> Konfigurowanie funkcji IntelliTrace

Możesz spróbować debugowania tylko zdarzeń IntelliTrace. Zdarzenia IntelliTrace są zdarzeniami debugera, wyjątki, zdarzenia .NET Framework i inne zdarzenia systemowe. Należy włączyć lub wyłączyć określone zdarzenia, aby kontrolować zdarzenia przez IntelliTrace, przed rozpoczęciem debugowania. Aby uzyskać więcej informacji, zobacz [funkcji IntelliTrace](../debugger/intellitrace-features.md).

- Włącz zdarzenia funkcji IntelliTrace przy dostępie do plików. Przejdź do **Narzędzia > Opcje > IntelliTrace > zdarzenia IntelliTrace** stronie, a następnie rozwiń **pliku** kategorii. Sprawdź **pliku** kategorii zdarzenia. To powoduje, że wszystkie pliku zdarzenia (dostęp, Zamknij, delete) do sprawdzenia.

## <a name="create-your-app"></a>Tworzenie aplikacji

1. Utwórz aplikację konsolową języka C#. W pliku Program.cs Dodaj następujące `using` instrukcji:

    ```csharp
    using System.IO;
    ```

2. Utwórz <xref:System.IO.FileStream> metody Main, odczytanie z niego, zamknij je i usuń plik. Dodaj kolejny wiersz po prostu zapewnienie miejsca ustawienia punktu przerwania:

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

3. Ustawianie punktu przerwania `Console.WriteLine("done");`

## <a name="start-debugging-and-view-intellitrace-events"></a>Rozpocznij debugowanie i wyświetlać zdarzenia IntelliTrace

1. Rozpocznij standardowe debugowanie. (Naciśnij klawisz **F5** lub kliknij przycisk **Debuguj > Rozpocznij debugowanie**.)

    > [!TIP]
    > Zachowaj **lokalne** i **Autos** otwarte okna podczas debugowania można zobaczyć i zapisać wartości w tych oknach.

2. Zatrzymuje wykonywanie w punkcie przerwania. Jeśli nie widzisz **narzędzia diagnostyczne** okna, kliknij przycisk **Debuguj > Windows > zdarzenia IntelliTrace**.

    W **narzędzia diagnostyczne** oknie Znajdź **zdarzenia** kartę (powinien zostać wyświetlony 3 karty **zdarzenia**, **użycie pamięci**, i **procesora CPU Użycie**). **Zdarzenia** karta przedstawia chronologiczną listę zdarzeń, kończąc ostatniego zdarzenia, zanim Debuger przerwał wykonywanie. Powinien zostać wyświetlony zdarzenie o nazwie **WordSearchInputs.txt dostępu**.

    Poniższy zrzut ekranu pochodzi z programu Visual Studio 2015 Update 1.

    ![IntelliTrace&#45;Update1](../debugger/media/intellitrace-update1.png "IntelliTrace-Update1")

3. Wybierz zdarzenie, aby rozwinąć jego szczegóły.

    Poniższy zrzut ekranu pochodzi z programu Visual Studio 2015 Update 1.

    ![IntelliTraceUpdate1&#45;SingleEvent](../debugger/media/intellitraceupdate1-singleevent.png "IntelliTraceUpdate1-SingleEvent")

    Możesz wybrać ścieżki, aby otworzyć plik. Jeśli pełna nazwa ścieżki nie jest dostępna, **Otwórz plik** pojawi się okno dialogowe.

    Kliknij przycisk **Uaktywnij debugowanie historyczne**, która ustawia kontekst debugera do chwili, gdy zostało wybrane zdarzenie zbieranych, wyświetlanie danych historycznych w **stos wywołań**, **zmiennychlokalnych** i innych uczestniczących debugera systemu windows. Jeśli kod źródłowy jest dostępny, Visual Studio przesuwa wskaźnik myszy do odpowiedniego kodu w oknie źródłowym, aby można było go sprawdzić.

    Poniższy zrzut ekranu pochodzi z programu Visual Studio 2015 Update 1.

    ![HistoricalDebugging&#45;Update1](../debugger/media/historicaldebugging-update1.png "HistoricalDebugging-Update1")

4. Jeśli nie możesz znaleźć błędu, spróbuj sprawdzić inne zdarzenia, które doprowadziły do usterki. Informacje na temat rekordów wywołań funkcji IntelliTrace może mieć również, aby można było przechodzić przez wywołania funkcji.

## <a name="next-steps"></a>Następne kroki

Za pomocą debugowania historycznego, można użyć pewnych zaawansowanych funkcji IntelliTrace:

- Aby wyświetlić migawki, zobacz [Sprawdź poprzednie Stany aplikacji za pomocą funkcji IntelliTrace](../debugger/view-historical-application-state.md)
- Aby dowiedzieć się, jak sprawdzanie zmiennych i przechodzenie do kodu, zobacz [sprawdzanie aplikacji za pomocą debugowania historycznego](../debugger/historical-debugging-inspect-app.md)
