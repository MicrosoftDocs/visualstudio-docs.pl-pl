---
title: 'Przewodnik: Używanie funkcji IntelliTrace | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e1c9c91a-0009-4c4e-9b4f-c9ab3a6022a7
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cc1e2b40e16a14da505243aeb11542df3adfb18d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51781312"
---
# <a name="walkthrough-using-intellitrace"></a>Przewodnik: Używanie funkcji IntelliTrace
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dodatkowo do zebrania informacji dotyczących określonych zdarzeń lub kategorie zdarzeń, lub wywołania funkcji poszczególnych zdarzeń, można użyć funkcji IntelliTrace. Poniższe procedury pokazują, jak to zrobić.  
  
 Za pomocą funkcji IntelliTrace w programie Visual Studio Enterprise (ale nie w wersjach Professional lub Community).  
  
##  <a name="GettingStarted"></a> Za pomocą funkcji IntelliTrace z tylko zdarzenia  
 Możesz spróbować debugowania tylko zdarzeń IntelliTrace. Zdarzenia IntelliTrace są zdarzeniami debugera, wyjątki, zdarzenia .NET Framework i inne zdarzenia systemowe. Należy włączyć lub wyłączyć określone zdarzenia, aby kontrolować zdarzenia przez IntelliTrace, przed rozpoczęciem debugowania. Aby uzyskać więcej informacji, zobacz [funkcji IntelliTrace](../debugger/intellitrace-features.md).  
  
 Poniższe kroki pokazują sposób debugowania tylko zdarzeń IntelliTrace:  
  
1.  Włącz zdarzenia funkcji IntelliTrace przy dostępie do plików. Przejdź do **narzędzia / Opcje / IntelliTrace / zdarzenia IntelliTrace** stronie, a następnie rozwiń **pliku** kategorii. Sprawdź **pliku** kategorii zdarzenia. To powoduje, że wszystkie pliku zdarzenia (dostęp, Zamknij, delete) do sprawdzenia.  
  
2.  Utwórz aplikację konsolową języka C#. W pliku Program.cs Dodaj następujące `using` instrukcji:  
  
    ```csharp  
    using System.IO;  
    ```  
  
3.  Utwórz <xref:System.IO.FileStream> metody Main, odczytanie z niego, zamknij je i usuń plik. Dodaj kolejny wiersz po prostu zapewnienie miejsca ustawienia punktu przerwania:  
  
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
  
4.  Ustawianie punktu przerwania `Console.WriteLine("done");`  
  
5.  Rozpocznij standardowe debugowanie. (Naciśnij klawisz **F5** lub kliknij przycisk **debugowania / uruchamiania debugowania**.  
  
    > [!TIP]
    >  Zachowaj **lokalne** i **Autos** otwarte okna podczas debugowania można zobaczyć i zapisać wartości w tych oknach.  
  
6.  Zatrzymuje wykonywanie w punkcie przerwania. Jeśli nie widzisz **narzędzia diagnostyczne** okna, kliknij przycisk **debugowanie / Windows / zdarzenia IntelliTrace**.  
  
     W **narzędzia diagnostyczne** oknie Znajdź **zdarzenia** kartę (powinien zostać wyświetlony 3 karty **zdarzenia**, **użycie pamięci**, i **procesora CPU Użycie**). **Zdarzenia** karta przedstawia chronologiczną listę zdarzeń, kończąc ostatniego zdarzenia, zanim Debuger przerwał wykonywanie. Powinien zostać wyświetlony zdarzenie o nazwie **WordSearchInputs.txt dostępu**.  
  
     Poniższy zrzut ekranu pochodzi z programu Visual Studio 2015 Update 1.  
  
     ![IntelliTrace&#45;Update1](../debugger/media/intellitrace-update1.png "IntelliTrace-Update1")  
  
7.  Wybierz zdarzenie, aby rozwinąć jego szczegóły.  
  
     Poniższy zrzut ekranu pochodzi z programu Visual Studio 2015 Update 1.  
  
     ![IntelliTraceUpdate1&#45;SingleEvent](../debugger/media/intellitraceupdate1-singleevent.png "IntelliTraceUpdate1-SingleEvent")  
  
     Możesz wybrać ścieżki, aby otworzyć plik. Jeśli pełna nazwa ścieżki nie jest dostępna, **Otwórz plik** pojawi się okno dialogowe.  
  
     Kliknij przycisk **Uaktywnij debugowanie historyczne**, która ustawia kontekst debugera do chwili, gdy zostało wybrane zdarzenie zbieranych, wyświetlanie danych historycznych w **stos wywołań**, **zmiennychlokalnych** i innych uczestniczących debugera systemu windows. Jeśli kod źródłowy jest dostępny, Visual Studio przesuwa wskaźnik myszy do odpowiedniego kodu w oknie źródłowym, aby można było go sprawdzić.  
  
     Poniższy zrzut ekranu pochodzi z programu Visual Studio 2015 Update 1.  
  
     ![HistoricalDebugging&#45;Update1](../debugger/media/historicaldebugging-update1.png "HistoricalDebugging-Update1")  
  
8.  Jeśli nie możesz znaleźć błędu, spróbuj sprawdzić inne zdarzenia, które doprowadziły do usterki. Informacje na temat rekordów wywołań funkcji IntelliTrace może mieć również, aby można było przechodzić przez wywołania funkcji.  
  
## <a name="using-intellitrace-with-events-and-function-calls"></a>Za pomocą funkcji IntelliTrace przy użyciu zdarzenia i wywołania funkcji  
 IntelliTrace może zapisać wywołania funkcji wraz z wydarzeniami. Dzięki temu można wyświetlić historię stosu wywołań, poruszać i wywołań w kodzie. IntelliTrace zapisuje dane, takie jak nazwy funkcji, punkty wejścia i wyjścia funkcji i określone wartości parametrów i zwracanych wartości. Zobacz [funkcji IntelliTrace](../debugger/intellitrace-features.md).  
  
1.  Włącz kolekcję wywołań. (Na **narzędzia / Opcje / IntelliTrace / ogólne**, wybierz opcję **zdarzenia IntelliTrace i wywołania informacji**. IntelliTrace rozpocznie się zbieranie tych informacji, po rozpoczęciu następnej sesji debugowania.  
  
    > [!TIP]
    >  Może to spowolnić aplikację i zwiększyć rozmiar wszystkich plików dziennika IntelliTrace (itrace) zapisywanych na dysku. Aby uzyskać większość danych wywołań, ale zminimalizować skutki, Zapisz dane tylko z tych modułów, które Cię interesują. Aby zmienić maksymalny rozmiar plików itrace, przejdź do **narzędzia / Opcje / IntelliTrace / zaawansowane**, a następnie określ maksymalną ilość miejsca na dysku. Wartość domyślna to 250 MB.  
  
2.  Rozpocznij debugowanie aplikacji konsolowej C# utworzony w poprzedniej sekcji. Zatrzymuje wykonywanie w punkcie przerwania. Jeśli nie widzisz **narzędzia diagnostyczne** okna, kliknij przycisk **debugowanie / Windows / zdarzenia IntelliTrace**.  
  
3.  Przełącz się do **wywołania** kartę.  
  
     Zostanie wyświetlona wywołań funkcji aplikacji, począwszy od wywołania głównego (w bieżącym rozwiązaniu główny punkt wejścia), a kończąc na lokalizację, w których wykonanie Przerwano.  
  
     Wybierz jedną z wywołania funkcji, a następnie kliknij go dwukrotnie. Punkty wejścia i wyjścia funkcji, a także wywołania, bieżącego wywołania innych funkcji i zdarzenia IntelliTrace wygenerowane przez wywołanie powinno być widoczne. Jeśli nie masz, debugowanie historyczne włączona, ta akcja powoduje włączenie. Aby dowiedzieć się więcej na temat debugowania historycznego, zobacz [debugowania historycznego](../debugger/historical-debugging.md).  
  
    > [!NOTE]
    >  Możesz zobaczyć, że niektóre połączenia są wygaszone. Jest to spowodowane IntelliTrace nie zapisał danych z odpowiednich modułów. Aby wyświetlić te dane, należy mieć IntelliTrace zebrał dane z tych modułów. Aby uzyskać informacji na temat określania modułów, zobacz [funkcji IntelliTrace](../debugger/intellitrace-features.md).  
  
## <a name="next-steps"></a>Następne kroki






