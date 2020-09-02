---
title: 'Przewodnik: używanie IntelliTrace | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: e1c9c91a-0009-4c4e-9b4f-c9ab3a6022a7
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 96d18ae0684dab5b6dc5c4001b93804bb13aa75e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64844186"
---
# <a name="walkthrough-using-intellitrace"></a>Przewodnik: Używanie funkcji IntelliTrace
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Za pomocą IntelliTrace można zbierać informacje o określonych zdarzeniach lub kategoriach zdarzeń albo o pojedynczych wywołaniach funkcji oprócz zdarzeń. Poniższe procedury pokazują, jak to zrobić.  
  
 Możesz użyć IntelliTrace w wersji Visual Studio Enterprise (ale nie wersji Professional lub Community).  
  
## <a name="using-intellitrace-with-events-only"></a><a name="GettingStarted"></a> Używanie IntelliTrace z tylko zdarzeniami  
 Możesz wypróbować debugowanie za pomocą tylko zdarzeń IntelliTrace. Zdarzenia IntelliTrace to zdarzenia debugera, wyjątki, zdarzenia .NET Framework i inne zdarzenia systemowe. Należy włączyć lub wyłączyć określone zdarzenia, aby kontrolować zdarzenia, które IntelliTrace rekordy przed rozpoczęciem debugowania. Aby uzyskać więcej informacji, zobacz [IntelliTrace Features](../debugger/intellitrace-features.md).  
  
 Poniższe kroki pokazują, jak debugować tylko przy użyciu zdarzeń IntelliTrace:  
  
1. Włącz zdarzenie IntelliTrace, aby uzyskać dostęp do plików. Przejdź do strony **Narzędzia/Opcje/IntelliTrace/IntelliTrace zdarzenia** i rozwiń kategorię **plik** . Sprawdź kategorię zdarzenia **pliku** . Powoduje to sprawdzenie wszystkich zdarzeń plików (dostęp, zamykanie, usuwanie).  
  
2. Utwórz aplikację konsolową języka C#. W pliku Program.cs Dodaj następującą `using` instrukcję:  
  
    ```csharp  
    using System.IO;  
    ```  
  
3. Utwórz <xref:System.IO.FileStream> w metodzie Main, Odczytaj z niej, zamknij ją i Usuń plik. Dodaj kolejny wiersz, aby ustawić punkt przerwania:  
  
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
  
4. Ustaw punkt przerwania na `Console.WriteLine("done");`  
  
5. Rozpocznij debugowanie w zwykły sposób. (Naciśnij klawisz **F5** lub kliknij pozycję **Debuguj/Rozpocznij debugowanie**.  
  
    > [!TIP]
    > Zachowaj otwarte okna **lokalne** i **Autotekstu** w trakcie debugowania, aby zobaczyć i zapisać wartości w tych oknach.  
  
6. Wykonywanie jest zatrzymane w punkcie przerwania. Jeśli nie widzisz okna **Narzędzia diagnostyczne** , kliknij polecenie **Debuguj/zdarzenia systemu Windows/IntelliTrace**.  
  
     W oknie **Narzędzia diagnostyczne** Znajdź kartę **zdarzenia** (powinny być widoczne 3 karty, **zdarzenia**, **użycie pamięci**i **użycie procesora**). Karta **zdarzenia** zawiera chronologiczną listę zdarzeń kończącą się ostatnim zdarzeniem, zanim debuger przerwał wykonywanie operacji. Powinno zostać wyświetlone zdarzenie o nazwie **WordSearchInputs.txtdostępu **.  
  
     Poniższy zrzut ekranu pochodzi z programu Visual Studio 2015 Update 1.  
  
     ![IntelliTrace&#45;Update1](../debugger/media/intellitrace-update1.png "IntelliTrace — Update1")  
  
7. Wybierz zdarzenie, aby rozwinąć jego szczegóły.  
  
     Poniższy zrzut ekranu pochodzi z programu Visual Studio 2015 Update 1.  
  
     ![IntelliTraceUpdate1&#45;SingleEvent](../debugger/media/intellitraceupdate1-singleevent.png "IntelliTraceUpdate1-SingleEvent")  
  
     Możesz wybrać link ścieżki, aby otworzyć plik. Jeśli pełna nazwa ścieżki jest niedostępna, pojawi się okno dialogowe **Otwórz plik** .  
  
     Kliknij pozycję **Aktywuj debugowanie historyczne**, które ustawia kontekst debugera na czas zebrania wybranego zdarzenia, pokazując dane historyczne w **stosie wywołań**, **zmiennych lokalnych** i innych oknach debugera. Jeśli kod źródłowy jest dostępny, program Visual Studio przesuwa wskaźnik do odpowiedniego kodu w oknie źródłowym, aby można było go przeanalizować.  
  
     Poniższy zrzut ekranu pochodzi z programu Visual Studio 2015 Update 1.  
  
     ![HistoricalDebugging&#45;Update1](../debugger/media/historicaldebugging-update1.png "HistoricalDebugging — Update1")  
  
8. Jeśli usterka nie została znaleziona, spróbuj sprawdzić inne zdarzenia prowadzące do błędu. Istnieje również możliwość rejestrowania informacji o wywołaniach IntelliTrace, dzięki czemu można przechodzić przez wywołania funkcji.  
  
## <a name="using-intellitrace-with-events-and-function-calls"></a>Korzystanie z IntelliTrace z wywołaniami zdarzeń i funkcji  
 IntelliTrace może rejestrować wywołania funkcji wraz ze zdarzeniami. Dzięki temu można zobaczyć historię stosu wywołań i przejść do tyłu i do przodu przez wywołania w kodzie. IntelliTrace rejestruje dane, takie jak nazwy funkcji, wprowadzanie funkcji i punkty wyjścia oraz pewne wartości parametrów i wartości zwracane. Zobacz [Funkcje IntelliTrace](../debugger/intellitrace-features.md).  
  
1. Włącz zbieranie wywołań. (W obszarze **Narzędzia/Opcje/IntelliTrace/ogólne**wybierz pozycję **zdarzenia IntelliTrace i informacje o wywołaniu**. IntelliTrace rozpocznie zbieranie tych informacji po rozpoczęciu następnej sesji debugowania.  
  
    > [!TIP]
    > Może to spowolnić aplikację i zwiększyć rozmiar wszystkich plików dziennika IntelliTrace (pliki iTrace), które są zapisywane na dysku. Aby uzyskać większość danych wywołań, ale zminimalizować efekty, należy zarejestrować dane tylko z tych, które są interesujące. Aby zmienić maksymalny rozmiar plików. iTrace, przejdź do pozycji **Narzędzia/Opcje/IntelliTrace/zaawansowane**i Określ maksymalną ilość miejsca na dysku. Wartość domyślna to 250 MB.  
  
2. Rozpocznij debugowanie aplikacji konsolowej C# utworzonej w poprzedniej sekcji. Wykonywanie jest zatrzymane w punkcie przerwania. Jeśli nie widzisz okna **Narzędzia diagnostyczne** , kliknij polecenie **Debuguj/zdarzenia systemu Windows/IntelliTrace**.  
  
3. Przejdź do karty **wywołania** .  
  
     Teraz zobaczysz wywołania funkcji aplikacji, rozpoczynając od wywołania głównego (w bieżącym rozwiązaniu, głównym punkcie wejścia) i kończąc na miejscu, w którym wykonywanie zostało zerwane.  
  
     Wybierz jedno z wywołań funkcji i kliknij je dwukrotnie. Powinny zostać wyświetlone punkty wejścia i wyjścia funkcji oraz wywołania, które bieżące wywołanie do innych funkcji i zdarzenia IntelliTrace wywoływane przez wywołanie. Jeśli nie masz włączonej debugowania historycznego, ta akcja spowoduje jego włączenie. Aby dowiedzieć się więcej na temat debugowania historycznego, zobacz [debugowanie historyczne](../debugger/historical-debugging.md).  
  
    > [!NOTE]
    > Może się okazać, że niektóre wywołania są wygaszone. Wynika to z faktu, że IntelliTrace nie zarejestrował danych z odpowiednich modułów. Aby wyświetlić te dane, IntelliTrace Zbieraj dane z tych modułów. Informacje o określaniu modułów można znaleźć w temacie [IntelliTrace Features](../debugger/intellitrace-features.md).  
  
## <a name="next-steps"></a>Następne kroki
