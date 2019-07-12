---
title: Przy użyciu zapisanych danych funkcji IntelliTrace | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.historicaldebug.norepro
helpviewer_keywords:
- iTrace files
- IntelliTrace, log files
- IntelliTrace log files
- .iTrace files
ms.assetid: 9f2cce86-345a-4e22-84ba-91542d81e67a
caps.latest.revision: 112
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b1e22447581deee70c133dfdb4c42df6630e26ad
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2019
ms.locfileid: "67823462"
---
# <a name="using-saved-intellitrace-data"></a>Korzystanie z zapisanych danych funkcji IntelliTrace
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Przejdź do określonych punktów w wykonywaniu swojej aplikacji, gdy zaczynasz debugowanie z pliku dziennika (.iTrace) funkcji IntelliTrace. Ten plik może zawierać zdarzeń dotyczących wydajności, wyjątki, wątki, kroki testu, moduły i inne informacje systemowe, że IntelliTrace podczas pracy Twojej aplikacji.  
  
 Upewnij się, że masz:  
  
- Pasujące pliki źródłowe i pliki symboli (.pdb) dla kodu aplikacji. W przeciwnym razie program Visual Studio nie może rozpoznać lokalizacji źródłowych i wyświetla komunikat "Nie można odnaleźć symboli". Zobacz [Określ symboli (.pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) i [diagnozowanie problemów po wdrożeniu](../debugger/diagnose-problems-after-deployment.md).  
  
- Program Visual Studio Enterprise (ale nie Professional lub Community Edition) na komputerze deweloperskim lub innym komputerze, aby otworzyć pliki .iTrace  
  
- Plik .iTrace z jednego z tych źródeł:  
  
    |**Element źródłowy**|**Zobacz**|  
    |----------------|-------------|  
    |Sesja IntelliTrace w Visual Studio Enterprise (ale nie Professional lub Community)|[Funkcje IntelliTrace](../debugger/intellitrace-features.md)|  
    |Sesji testowej w programie Microsoft Test Manager. Dołącza plik .iTrace do elementu roboczego Team Foundation Server.|[Zbieranie większej ilości danych podczas wykonywania testów ręcznych](https://msdn.microsoft.com/library/bb5a2cc0-84f5-4dfe-9560-ca3d313aefd2)|  
    |Program Microsoft Monitoring Agent, albo samodzielnie lub z programem System Center 2012 R2 Operations Manager dla platformy ASP.NET i aplikacje sieci web aplikacji programu SharePoint, działające we wdrożeniu|-   [Diagnozowanie problemów po wdrożeniu](../debugger/diagnose-problems-after-deployment.md)<br />-   [What's New for System Center 2012 R2 Operations Manager](https://technet.microsoft.com/library/dn249700.aspx)|  
  
## <a name="GetStarted"></a> Co chcesz zrobić?  
  
- [Otwórz dziennik IntelliTrace](#Open)  
  
- [Informacje w dzienniku IntelliTrace](#Understand)  
  
- [Rozpocznij debugowanie z dziennika funkcji IntelliTrace](#StartDebugging)  
  
## <a name="Open"></a> Otwórz dziennik IntelliTrace  
 Na komputerze przy użyciu programu Visual Studio Enterprise Otwórz plik .iTrace.  
  
- Kliknij dwukrotnie plik .iTrace, poza Visual Studio lub Otwórz plik z poziomu programu Visual Studio.  
  
     \- lub —  
  
- Jeśli plik .iTrace jest dołączony do elementu roboczego Team Foundation Server, wykonaj następujące kroki w elemencie roboczym:  
  
  - W obszarze **wszystkie łącza**, Znajdź plik .iTrace. Otwórz go.  

        \- or -  

  - W obszarze **kroki odtwarzania**, wybierz **IntelliTrace** łącza.  
  
> [!TIP]
> Jeśli plik IntelliTrace został zamknięty podczas debugowania, możesz uruchomić go w łatwy sposób. Przejdź do **debugowania** menu, wybierz **IntelliTrace**, **Pokaż podsumowanie dziennika**. Można również wybrać **Pokaż podsumowanie dziennika** w **IntelliTrace** okna. Jest on dostępny tylko podczas debugowania przy użyciu funkcji IntelliTrace.  
  
## <a name="Understand"></a> Informacje w dzienniku IntelliTrace  
 Niektóre z poniższych sekcji w pliku .iTrace są wyświetlane tylko wtedy, gdy zostały zebrane dane z określonego źródła, na przykład z programu Test Manager lub aplikacji programu SharePoint.  
  
|**Sekcja**|**zawiera**|**Źródło kolekcji**|  
|-----------------|------------------|---------------------------|  
|[Naruszenia wydajności](#Performance)|Zdarzenia wydajności w przypadku wywołań funkcji, która przekracza skonfigurowany próg|Program Microsoft Monitoring Agent, albo samodzielnie lub z programem System Center 2012 R2 Operations Manager dla programu ASP.NET aplikacje sieci web hostowanych w usługach IIS|  
|[Dane wyjątku](#ExceptionData)|Wyjątki, w tym pełny stos wywołania dla każdego wyjątku|Wszystkie źródła|  
|[Analiza](#Analysis)|SharePoint 2010 i SharePoint 2013 tylko dla aplikacji. Diagnozowanie zdarzeń IntelliTrace i programu SharePoint, takich jak zdarzenia debugera, zdarzenia usługi ULS, nieobsłużone wyjątki i inne dane zarejestrowane przez program Microsoft Monitoring Agent.|Program Microsoft Monitoring Agent, albo samodzielnie lub z programem System Center 2012 R2 Operations Manager|  
|[Informacje o systemie](#SystemInfo)|Ustawienia i specyfikacje systemu hosta|Wszystkie źródła|  
|[Lista wątków](#ThreadsList)|Wątki, które uruchomiono podczas procesu kolekcji|Wszystkie źródła|  
|[Dane testowe](#TestData)|Kroki testu i ich wyniki z sesji testowej|Test Manager|  
|[Moduły](#Modules)|Moduły załadowane w procesie ładowania w kolejności załadowania.|Wszystkie źródła|  
  
 Poniżej przedstawiono kilka wskazówek, aby pomóc w znalezieniu informacji w każdej sekcji:  
  
- Wybierz nagłówek kolumny, aby posortować dane.  
  
- Użyj pola wyszukiwania do filtrowania danych. Zwykłe wyszukiwanie tekstu działa we wszystkich kolumnach, z wyjątkiem kolumn czasowych. Można także filtrować wyszukiwania do określonej kolumny za pomocą jednego filtru na kolumnę. Wpisz nazwę kolumny bez spacji, dwukropka ( **:** ) ani wartości wyszukiwania. Postępuj zgodnie z tym przy użyciu średnika ( **;** ) aby dodać inną wartość w kolumnie i wyszukiwania.  
  
     Na przykład, aby znaleźć zdarzenia wydajności, które zawierają wyraz "wolne" w **opis** kolumny, wpisz:  
  
     `Description:slow`  
  
## <a name="StartDebugging"></a> Rozpocznij debugowanie z dziennika funkcji IntelliTrace  
  
### <a name="Performance"></a> Naruszenia wydajności  
 Przejrzyj zdarzenia wydajności, które zostały zarejestrowane dla aplikacji. Można ukryć te zdarzenia, które nie występują często.  
  
##### <a name="to-start-debugging-from-a-performance-event"></a>Aby rozpocząć debugowanie ze zdarzenia wydajności  
  
1. W obszarze **naruszeń wydajności**, przejrzyj zarejestrowane zdarzenia wydajności, ich całkowity czas realizacji i inne informacje o zdarzeniach. Następnie zagłęb się w metody, które zostały wywołane podczas zdarzenia dotyczącego wydajności.  
  
     ![Wyświetl szczegóły zdarzeń dotyczących wydajności](../debugger/media/ffr-itsummarypageperformance.png "FFR_ITSummaryPagePerformance")  
  
     Możesz także po prostu dwukrotnie kliknąć zdarzenie.  
  
2. Na stronie zdarzeń przejrzyj czasy wykonania dla tych wywołań. Odszukaj spowalniające wywołanie w drzewie wykonywania.  
  
     Najwolniejsze wywołania pojawiają się we własnej sekcji w przypadku wielu wywołań, zagnieżdżonych lub innych.  
  
3. Rozwiń, że wywołanie, aby przejrzeć wszelkie zagnieżdżone wywołania i wartości parametrów, które zostały zarejestrowane w danym momencie.  
  
     (Klawiatura: Aby pokazać lub ukryć zagnieżdżone wywołania, naciśnij klawisz **Strzałka w prawo** lub **Strzałka w lewo** odpowiednio klucza. Aby pokazać i ukryć wartości parametrów dla zagnieżdżonych wywołań, naciśnij klawisz **miejsca** klucza.)  
  
     Uruchom debugowanie z wywołania.  
  
     ![Rozpocznij debugowanie z wywołania metody](../debugger/media/ffr-itsummarypageperformancemethodscalled.png "FFR_ITSummaryPagePerformanceMethodsCalled")  
  
     Możesz też po prostu dwukrotnie kliknąć wywołanie lub naciśnij **Enter** klucza.  
  
     Jeśli metoda ta jest w kodzie aplikacji, program Visual Studio przechodzi do tej metody.  
  
     ![Przejdź do kodu aplikacji ze zdarzenia wydajności](../debugger/media/ffr-itsummarypageperformancegotocode.png "FFR_ITSummaryPagePerformanceGoToCode")  
  
     Teraz można przejrzeć inne zarejestrowane wartości, stos wywołań, przejść przez kod lub przy użyciu **IntelliTrace** okna [Przenieś tyłu lub do przodu "w czasie" między innymi metodami](../debugger/intellitrace.md) które zostały wywołane podczas tego zdarzenia dotyczącego wydajności.  
  
### <a name="ExceptionData"></a> Dane wyjątku  
 Przejrzyj wyjątki, które zostały zgłoszone i rejestrowane dla swojej aplikacji. Można grupować wyjątki, które mają tego samego typu i stosu wywołań, aby wyświetlić najbardziej aktualne wyjątku.  
  
##### <a name="to-start-debugging-from-an-exception"></a>Aby rozpocząć debugowanie z wyjątku  
  
1. W obszarze **dane o wyjątkach**, przejrzyj zarejestrowane zdarzenia wyjątków, ich typy, wiadomości, i czas ich wystąpienia. Aby poznać więcej szczegółów związanych z kodem, rozpocznij debugowanie od ostatniego zdarzenia w grupie wyjątków.  
  
     ![Rozpocząć debugowanie ze zdarzenia wyjątków](../debugger/media/ffr-itsummarypageexception.png "FFR_ITSummaryPageException")  
  
     Możesz także po prostu dwukrotnie kliknąć zdarzenie. Jeśli zdarzenia nie są grupowane, wybierz opcję **debugować tego zdarzenia**.  
  
     Jeśli wystąpił wyjątek w kodzie aplikacji, program Visual Studio przechodzi do tego miejsca.  
  
     ![Przejdź do kodu aplikacji ze zdarzenia wyjątków](../debugger/media/ffr-itsummarypageexceptiongotocode.png "FFR_ITSummaryPageExceptionGoToCode")  
  
     Teraz można przejrzeć inne zarejestrowane wartości, stos wywołań, lub użyć **IntelliTrace** okna [przenoszenie tyłu lub do przodu "w czasie" między innymi zarejestrowanymi zdarzeniami](../debugger/intellitrace.md), kodu powiązany i wartości odnotowane w te punkty w czasie.  
  
    |**Kolumny**|**Pokazuje**|  
    |----------------|-------------------|  
    |**Typ**|Typ architektury .NET wyjątku|  
    |**Najnowszy komunikat** dla grupowane wyjątki lub **komunikat** niezgrupowane wyjątków|Komunikat o wyjątku|  
    |**Liczba** dla grupowane wyjątków|Liczba przypadków, gdy wyjątek został zgłoszony.|  
    |**Identyfikator wątku** niezgrupowane wyjątków|Identyfikator wątku, który wygenerował wyjątek|  
    |**Czas najnowszego zdarzenia** lub **czas trwania zdarzenia**|Sygnatura czasowa zapisana, gdy wyjątek został zgłoszony|  
    |**Stos wywołań**|Stos wywołań dla wyjątku.<br /><br /> Aby zobaczyć stos wywołań, wybierz wyjątek z listy. Stos wywołań jest wyświetlany poniżej listy wyjątków.|  
  
### <a name="Analysis"></a> Analiza  
 Diagnozowanie problemów z aplikacjami programu SharePoint 2010 i SharePoint 2013 za pomocą Identyfikatora korelacji programu SharePoint, lub przejrzyj nieobsłużone wyjątki, które zostały odnalezione przez program Microsoft Monitoring Agent.  
  
- Użyj identyfikator korelacji programu SharePoint, aby znaleźć jego odpowiadające żądanie sieci web i zdarzenia. Wybierz zdarzenie, a następnie rozpocząć debugowanie w punkcie gdzie i kiedy wystąpiło zdarzenie.  
  
- Jeśli program Microsoft Monitoring Agent znalazł nieobsłużone wyjątki, wybierz wyjątek, a następnie rozpocząć debugowanie w punkcie, w którym wyjątek wystąpił.  
  
##### <a name="start-debugging-with-a-sharepoint-correlation-id"></a>Uruchom debugowanie z identyfikatorem korelacji programu SharePoint  
  
1. Skopiuj identyfikator korelacji SharePoint z jej źródła.  
  
    Przykład:  
  
    ![IntelliTrace &#45; błąd SharePoint &#45; identyfikator korelacji](../debugger/media/sharepointerror-intellitrace.png "SharePointError_IntelliTrace")  
  
2. Otwórz plik .iTrace, a następnie przejdź do **analizy** i wprowadź identyfikator korelacji programu SharePoint, aby przejrzeć odpowiadające żądanie sieci web i rejestrowane zdarzenia.  
  
    ![Dziennik IntelliTrace &#45; identyfikator korelacji SharePoint wprowadź](../debugger/media/entersharepointcorrelationid.png "EnterSharePointCorrelationID")  
  
3. W obszarze **zdarzenia żądań**, zbadaj zdarzenia. Począwszy od góry, zdarzenia są wyświetlane w kolejności ich wystąpienia.  
  
   1. Wybierz zdarzenie, aby wyświetlić jego szczegóły.  
  
   2. Wybierz **Rozpocznij debugowanie** aby rozpocząć debugowanie w punkcie, w której zaszło zdarzenie.  
  
      ![Plik dziennika IntelliTrace &#45; żądania sieci web widoku &#43; zdarzenia](../debugger/media/entersharepointcorrelationid2.png "EnterSharePointCorrelationID2")  
  
   Możesz zobaczyć te rodzaje zdarzeń programu SharePoint oraz zdarzenia IntelliTrace:  
  
- **Zdarzenia profilu użytkownika**  
  
     Te zdarzenia mają miejsce, gdy program SharePoint ładuje profil użytkownika i gdy właściwości profilu użytkownika są odczytywane lub zmieniane.  
  
- **Ujednoliconego systemu rejestrowania (ULS) zdarzenia**  
  
     Program Microsoft Monitoring Agent zapisuje podzbiór zdarzeń ULS programu SharePoint i następujące pola:  
  
    |**Pole IntelliTrace**|**Pole ULS programu SharePoint**|  
    |----------------------------|------------------------------|  
    |**Identyfikator**|**Identyfikator zdarzenia**|  
    |**Poziom**|**Poziom**|  
    |**Identyfikator kategorii**|**Identyfikator kategorii**|  
    |**Kategoria**|**Kategoria**|  
    |**Obszar**|**Produkt**|  
    |**Output**|**Komunikat**|  
    |**Identyfikator korelacji**|**Identyfikator korelacji**|  
  
##### <a name="start-debugging-from-an-unhandled-exception"></a>Uruchom debugowanie z nieobsłużonego wyjątku  
  
1. Wybierz identyfikator korelacji programu SharePoint, dla wyjątku. Wyjątki są pogrupowane według typu i stosu wywołań.  
  
2. (Opcjonalnie) Rozwiń **stos wywołań** aby zobaczyć stos wywołań dla grupy wyjątki.  
  
3. Wybierz **wyjątek debugowania** aby rozpocząć debugowanie w punkcie, w którym wyjątek wystąpił.  
  
    ![Dziennik IntelliTrace &#45; SharePoint nieobsługiwane wyjątki](../debugger/media/sharepointunhandledexceptions-intellitrace.png "SharePointUnhandledExceptions_IntelliTrace")  
  
   Aby uzyskać wskazówki, zobacz [instruktażu: Debugowanie aplikacji SharePoint przy użyciu funkcji IntelliTrace](https://msdn.microsoft.com/library/4bd80d2f-f680-4bf4-81c3-f14e8185f6a4). Do tego rodzaju danych, które rekordy agenta, zobacz [funkcji IntelliTrace](../debugger/intellitrace-features.md).  
  
### <a name="ThreadsList"></a> Lista wątków  
 Badać zarejestrowane wątki, które uruchomiono w procesie docelowym. Możesz rozpocząć debugowanie od pierwszego prawidłowego zdarzenia IntelliTrace w wybranym wątku.  
  
##### <a name="to-start-debugging-from-a-specific-thread"></a>Aby rozpocząć debugowanie z określonego wątku  
  
1. W obszarze **Lista wątków**, wybierz wątek.  
  
2. W dolnej części **Lista wątków**, wybierz **Rozpocznij debugowanie**. Możesz także dwukrotnie kliknąć na wątek.  
  
    Aby rozpocząć debugowanie, od której rozpoczyna się aplikacja, kliknij dwukrotnie **główny wątek**. Zobacz [funkcji IntelliTrace](../debugger/intellitrace-features.md).  
  
   Dane wątku, który użytkownik utworzył mogą być bardziej przydatne niż wątki, które serwer tworzy i którymi zarządza w zakresie aplikacji sieci Web obsługiwanych przez usługi IIS.  
  
|**Kolumny**|**Pokazuje**|  
|----------------|-------------------|  
|**Identyfikator**|Numer identyfikacyjny wątku|  
|**Nazwa**|Nazwa wątku. Nienazwane wątki są wyświetlane jako "\<bez nazwy >".|  
|**Godzina rozpoczęcia**|Godzina utworzenia wątku|  
|**Godzina zakończenia**|Czas zakończenia wątku|  
  
### <a name="TestData"></a> Dane testowe  
 Przeanalizuj dane funkcji IntelliTrace programu Test Manager rejestrowane podczas testowania aplikacji.  
  
##### <a name="to-start-debugging-from-a-specific-test-step"></a>Aby rozpocząć debugowanie z określonego etapu testu  
  
1. Rozwiń **siatka etapów testu**. Wybierz etap badania.  
  
2. W dolnej części **siatka etapów testu**, wybierz **Rozpocznij debugowanie**. Możesz również kliknąć dwukrotnie krok testu.  
  
     Uruchomiony zostanie program debugowania z pierwszego odpowiedniego zdarzenia IntelliTrace po wybrany krok testu.  
  
     Jeśli istnieją dane testowe, IntelliTrace próbuje rozpoznać skojarzone kompilacji Team Foundation Server, która została użyta do wykonania przebiegu testu. Jeśli kompilacja zostanie znaleziona, skojarzone z nią symbole dla aplikacji są rozpoznawane automatycznie.  
  
|**Pole**|**Pokazuje**|  
|---------------|-------------------|  
|**Sesja testowa**|Sesje testowe, które zostały zapisane. Zazwyczaj występuje tylko jeden. Ta lista jest pusta, jeśli dane testowe został utworzony za pomocą manualnego testu poznawczego.|  
|**Przypadek testowy**|Przypadki testowe z wybranej sesji testowej. Ta lista jest pusta, jeśli dane testowe został utworzony za pomocą manualnego testu poznawczego.|  
|**Siatka etapów testu**|Kroki, które zostały zapisane z wynikiem testu w przebiegu testu lub się nie powieść|  
  
### <a name="SystemInfo"></a> Informacje o systemie  
 Ta sekcja zawiera szczegółowe informacje o systemie, który obsługiwał aplikację, na przykład sprzęt, system operacyjny, informacje dotyczące procesu i środowiska.  
  
### <a name="Modules"></a> Moduły  
 W tej sekcji przedstawiono moduły, które załadowane w procesie ładowania. Moduły są wyświetlane w kolejności załadowania.  
  
|**Kolumny**|**Pokazuje**|  
|----------------|-------------------|  
|**Nazwa modułu**|Nazwa pliku modułu|  
|**Ścieżka modułu**|Lokalizację dysku, na którym moduł został załadowany|  
|**Identyfikator modułu**|Unikatowy identyfikator modułu, który jest specyficzny dla wersji i przyczynia się do pasujących plików symboli (PDB). Zobacz [znajdowanie plików symboli (.pdb) i pliki źródłowe](https://msdn.microsoft.com/05384c85-d264-4e18-abaa-aa482ab25470).|  
  
### <a name="where-can-i-get-more-information"></a>Gdzie można uzyskać więcej informacji?  
 [Korzystanie z autonomicznego modułu zbierającego funkcji IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md)  
  
 [Funkcje IntelliTrace](../debugger/intellitrace-features.md)  
  
 [Zbieranie większej ilości danych podczas wykonywania testów ręcznych](https://msdn.microsoft.com/library/bb5a2cc0-84f5-4dfe-9560-ca3d313aefd2)  
  
 [IntelliTrace](../debugger/intellitrace.md)  
  
#### <a name="forums"></a>Fora  
 [Visual Studio Debugger](http://go.microsoft.com/fwlink/?LinkId=262263)  
  
#### <a name="guidance"></a>Wskazówki  
 [Testowanie dostarczania ciągłego w programie Visual Studio 2012 – rozdział 6: Przybornik testowy](http://go.microsoft.com/fwlink/?LinkID=255203)
