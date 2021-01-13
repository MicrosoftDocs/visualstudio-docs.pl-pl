---
title: Korzystanie z zapisanych danych IntelliTrace | Microsoft Docs
description: Aby rozpocząć debugowanie w określonym punkcie wykonywania, użyj pliku IntelliTrace (. iTrace). Plik zawiera informacje, które IntelliTrace zarejestrowane z przebiegu aplikacji.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.historicaldebug.norepro
helpviewer_keywords:
- iTrace files
- IntelliTrace, log files
- IntelliTrace log files
- .iTrace files
ms.assetid: 9f2cce86-345a-4e22-84ba-91542d81e67a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 42f355a0a8d04e48a2b9d14d0d62edf2cd949a87
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/13/2021
ms.locfileid: "98150941"
---
# <a name="using-saved-intellitrace-data-c-visual-basic-c"></a>Korzystanie z zapisanych danych IntelliTrace (C#, Visual Basic, C++)

Przejdź do określonych punktów w wykonaniu aplikacji po rozpoczęciu debugowania z pliku dziennika IntelliTrace (. iTrace). Ten plik może zawierać zdarzenia dotyczące wydajności, wyjątki, wątki, kroki testu, moduły i inne informacje o systemie, które IntelliTrace rekordy podczas uruchamiania aplikacji.

 Upewnij się, że masz:

- Zgodne pliki źródłowe i pliki symboli (. pdb) dla kodu aplikacji. W przeciwnym razie program Visual Studio nie może rozpoznać lokalizacji źródłowych i zostanie wyświetlony komunikat "nie znaleziono symboli". Zobacz [Określanie symboli (. pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) oraz [diagnozowanie problemów po wdrożeniu](../debugger/diagnose-problems-after-deployment.md).

- Visual Studio Enterprise (ale nie wersje Professional lub Community) na komputerze deweloperskim lub innym komputerze, aby otworzyć pliki. iTrace

- Plik. iTrace z jednego z następujących źródeł:

    |**Element źródłowy**|**Wyświetlania**|
    |----------------|-------------|
    |Sesja IntelliTrace w Visual Studio Enterprise (ale nie wersji Professional lub Community)|[Funkcje IntelliTrace](../debugger/intellitrace-features.md)|
    |Microsoft Monitoring Agent, samodzielne lub z programem System Center 2012 R2 Operations Manager, dla aplikacji internetowych ASP.NET i aplikacji programu SharePoint działających we wdrożeniu|-   [Diagnozowanie problemów po wdrożeniu](../debugger/diagnose-problems-after-deployment.md)<br />-   [Co nowego w programie System Center 2012 R2 Operations Manager](/previous-versions/system-center/system-center-2012-R2/dn249700(v=sc.12))|

## <a name="what-do-you-want-to-do"></a><a name="GetStarted"></a> Co chcesz zrobić?

- [Otwórz dziennik IntelliTrace](#Open)

- [Opis dziennika IntelliTrace](#Understand)

- [Rozpocznij debugowanie z dziennika IntelliTrace](#StartDebugging)

## <a name="open-an-intellitrace-log"></a><a name="Open"></a> Otwórz dziennik IntelliTrace
 Na komputerze z Visual Studio Enterprise Otwórz plik. iTrace.

- Kliknij dwukrotnie plik. iTrace poza programem Visual Studio lub Otwórz plik w programie Visual Studio.

     \- oraz

- Jeśli plik. iTrace jest dołączony do Team Foundation Server elementu pracy, wykonaj następujące kroki w elemencie roboczym:

  - W obszarze **wszystkie linki** Znajdź plik. iTrace. Otwórz go.

    \- oraz

  - W obszarze **Odtwórz kroki** wybierz łącze **IntelliTrace** .

> [!TIP]
> Jeśli plik IntelliTrace został zamknięty podczas debugowania, możesz go łatwo otworzyć. Przejdź do menu **Debuguj** , wybierz pozycję **IntelliTrace**, **Pokaż podsumowanie dziennika**. Możesz również wybrać **Pokaż podsumowanie dziennika** w oknie **IntelliTrace** . Jest to możliwe tylko podczas debugowania za pomocą IntelliTrace.

## <a name="understand-the-intellitrace-log"></a><a name="Understand"></a> Opis dziennika IntelliTrace
 Niektóre z poniższych sekcji w pliku. iTrace są wyświetlane tylko w przypadku zebrania danych z konkretnego źródła, na przykład z aplikacji programu SharePoint.

|**Sekcja**|**Wyświetlana**|**Źródło kolekcji**|
|-----------------|------------------|---------------------------|
|[Naruszenia wydajności](#Performance)|Zdarzenia wydajności z wywołaniami funkcji przekraczającymi skonfigurowany próg|Microsoft Monitoring Agent, autonomiczny moduł zbierający lub program System Center 2012 R2 Operations Manager for ASP.NET Web Apps hostowanych w usługach IIS|
|[Dane wyjątku](#ExceptionData)|Wyjątki, w tym pełny stos wywołań dla każdego wyjątku|Wszystkie źródła|
|[Analizy](#Analysis)|Tylko dla aplikacji SharePoint 2010 i SharePoint 2013. Diagnozuj zdarzenia IntelliTrace i programu SharePoint, takie jak zdarzenia debugera, zdarzenia ULS, Nieobsłużone wyjątki i inne dane zarejestrowane Microsoft Monitoring Agent.|Microsoft Monitoring Agent, autonomiczny moduł zbierający lub program System Center 2012 R2 Operations Manager|
|[Informacje o systemie](#SystemInfo)|Ustawienia i specyfikacje systemu hosta|Wszystkie źródła|
|[Lista wątków](#ThreadsList)|Wątki, które zostały uruchomione podczas zbierania|Wszystkie źródła|
|[Moduły](#Modules)|Moduły, które proces docelowy został załadowany w kolejności, w jakiej zostały załadowane.|Wszystkie źródła|
|[Żądanie sieci Web](#Modules)|Dane żądania sieci Web dla produkcyjnych aplikacji sieci Web usług IIS i SharePoint 2010 i SharePoint 2013|Microsoft Monitoring Agent i autonomiczny moduł zbierający|

 Oto kilka porad ułatwiających znalezienie informacji w poszczególnych sekcjach:

- Wybierz nagłówek kolumny, aby sortować dane.

- Użyj pola wyszukiwania, aby odfiltrować dane. Wyszukiwanie w postaci zwykłego tekstu działa we wszystkich kolumnach poza kolumnami czasu. Możesz również filtrować wyszukiwania do określonej kolumny z jednym filtrem na kolumnę. Wpisz nazwę kolumny bez spacji, dwukropek (**:**) i wartość wyszukiwania. Postępuj zgodnie z średnikiem (**;**), aby dodać kolejną kolumnę i wartość wyszukiwania.

     Na przykład aby znaleźć zdarzenia dotyczące wydajności, które mają wyraz "wolno" w kolumnie **Opis** , wpisz:

     `Description:slow`

## <a name="start-debugging-from-an-intellitrace-log"></a><a name="StartDebugging"></a> Rozpocznij debugowanie z dziennika IntelliTrace

### <a name="performance-violations"></a><a name="Performance"></a> Naruszenia wydajności
 Przejrzyj zdarzenia wydajności, które zostały zarejestrowane dla aplikacji. Można ukryć te zdarzenia, które nie występują często.

##### <a name="to-start-debugging-from-a-performance-event"></a>Aby rozpocząć debugowanie ze zdarzenia wydajności

1. W obszarze **naruszenia wydajności** Sprawdź zarejestrowane zdarzenia wydajności, ich łączny czas wykonywania i inne informacje o zdarzeniach. Następnie zagłęb się w metody, które zostały wywołane podczas zdarzenia dotyczącego wydajności.

     ![Wyświetl szczegóły zdarzenia wydajności](../debugger/media/ffr_itsummarypageperformance.png "FFR_ITSummaryPagePerformance")

     Możesz także po prostu dwukrotnie kliknąć zdarzenie.

2. Na stronie zdarzeń przejrzyj czasy wykonania dla tych wywołań. Odszukaj spowalniające wywołanie w drzewie wykonywania.

     Najwolniejsze wywołania pojawiają się we własnej sekcji w przypadku wielu wywołań, zagnieżdżonych lub innych.

3. Rozwiń to wywołanie, aby przejrzeć wszelkie zagnieżdżone wywołania i wartości parametrów, które zostały zarejestrowane w danym momencie.

     (Klawiatura: aby pokazać lub ukryć wywołanie zagnieżdżone, naciśnij odpowiednio **strzałkę w prawo** lub klawisz **Strzałka w lewo** . Aby pokazać i ukryć wartości parametrów dla wywołania zagnieżdżonego, naciśnij klawisz **spacji** .

     Rozpocznij debugowanie od wywołania.

     ![Rozpocznij debugowanie od wywołania metody](../debugger/media/ffr_itsummarypageperformancemethodscalled.png "FFR_ITSummaryPagePerformanceMethodsCalled")

     Możesz również po prostu dwukrotnie kliknąć wywołanie lub nacisnąć klawisz **Enter** .

     Jeśli metoda ta jest w kodzie aplikacji, program Visual Studio przechodzi do tej metody.

     ![Przejdź do kodu aplikacji ze zdarzenia wydajności](../debugger/media/ffr_itsummarypageperformancegotocode.png "FFR_ITSummaryPagePerformanceGoToCode")

     Teraz można przejrzeć inne zarejestrowane wartości, stos wywołań, przekroczyć kod lub użyć okna **IntelliTrace** do [przenoszenia do tyłu lub do przodu "w czasie" między innymi metodami](../debugger/intellitrace.md) , które zostały wywołane podczas tego zdarzenia wydajności.

### <a name="exception-data"></a><a name="ExceptionData"></a> Dane wyjątku
 Przejrzyj wyjątki, które zostały zgłoszone i zarejestrowane dla aplikacji. Można grupować wyjątki, które mają ten sam typ i stos wywołań, aby zobaczyć tylko najnowszy wyjątek.

##### <a name="to-start-debugging-from-an-exception"></a>Aby rozpocząć debugowanie z wyjątku

1. W obszarze **dane wyjątku** Przejrzyj zarejestrowane zdarzenia wyjątków, ich typy, komunikaty i czas wystąpienia wyjątków. Aby poznać więcej szczegółów związanych z kodem, rozpocznij debugowanie od ostatniego zdarzenia w grupie wyjątków.

     ![Rozpocznij debugowanie od zdarzenia wyjątku](../debugger/media/ffr_itsummarypageexception.png "FFR_ITSummaryPageException")

     Możesz także po prostu dwukrotnie kliknąć zdarzenie. Jeśli zdarzenia nie są zgrupowane, wybierz **Debuguj to zdarzenie**.

     Jeśli wystąpił wyjątek w kodzie aplikacji, program Visual Studio przechodzi do tego miejsca.

     ![Przejdź do kodu aplikacji ze zdarzenia wyjątku](../debugger/media/ffr_itsummarypageexceptiongotocode.png "FFR_ITSummaryPageExceptionGoToCode")

     Teraz można przejrzeć inne zarejestrowane wartości, stos wywołań lub użyć okna **IntelliTrace** do [przenoszenia do tyłu lub do przodu "w czasie" między innymi zarejestrowanymi zdarzeniami](../debugger/intellitrace.md), kodem pokrewnym i wartościami zarejestrowanymi w tych punktach w czasie.

    |**Kolumna**|**Pokazuje**|
    |----------------|-------------------|
    |**Typ**|Typ wyjątku dla platformy .NET|
    |**Najnowszy komunikat** dla pogrupowanych wyjątków lub **komunikatów** dla wyjątków niepogrupowanych|Komunikat dostarczony przez wyjątek|
    |**Liczba** zgrupowanych wyjątków|Liczba zgłoszonych wyjątków|
    |**Identyfikator wątku** dla wyjątków niezgrupowane|Identyfikator wątku, który wywołał wyjątek|
    |**Najnowszy czas zdarzenia** lub **czas zdarzenia**|Sygnatura czasowa zarejestrowana po zgłoszeniu wyjątku|
    |**Stos wywołań**|Stos wywołań dla wyjątku.<br /><br /> Aby wyświetlić stos wywołań, wybierz wyjątek z listy. Stos wywołań jest wyświetlany poniżej listy wyjątków.|

### <a name="analysis"></a><a name="Analysis"></a> Analizy
 Diagnozowanie problemów z aplikacjami SharePoint 2010 i SharePoint 2013 przy użyciu identyfikatora korelacji programu SharePoint lub sprawdzanie wszelkich nieobsłużonych wyjątków znalezionych Microsoft Monitoring Agent.

- Użyj identyfikatora korelacji programu SharePoint, aby znaleźć pasujące żądania sieci Web i zdarzenia. Wybierz zdarzenie, a następnie Rozpocznij debugowanie w punkcie, w którym wystąpiło zdarzenie.

- Jeśli Microsoft Monitoring Agent znaleziono Nieobsłużone wyjątki, wybierz wyjątek, a następnie Rozpocznij debugowanie w punkcie, w którym wystąpił wyjątek.

##### <a name="start-debugging-with-a-sharepoint-correlation-id"></a>Uruchom debugowanie z identyfikatorem korelacji programu SharePoint

1. Skopiuj identyfikator korelacji programu SharePoint ze źródła.

    Na przykład:

    ![Błąd IntelliTrace &#45; SharePoint &#45; identyfikator korelacji](../debugger/media/sharepointerror_intellitrace.png "SharePointError_IntelliTrace")

2. Otwórz plik. iTrace, a następnie przejdź do **analizy** i wprowadź identyfikator korelacji programu SharePoint, aby przejrzeć pasujące żądania sieci Web i zarejestrowane zdarzenia.

    ![&#45; dziennika IntelliTrace wprowadź identyfikator korelacji programu SharePoint](../debugger/media/entersharepointcorrelationid.png "EnterSharePointCorrelationID")

3. W obszarze **zdarzenia żądań** Przejrzyj zdarzenia. Od góry zdarzenia są wyświetlane w kolejności, w jakiej się znajdują.

   1. Wybierz zdarzenie, aby wyświetlić jego szczegóły.

   2. Wybierz **Rozpocznij debugowanie** , aby rozpocząć debugowanie w punkcie, w którym wystąpiło zdarzenie.

      ![Plik dziennika IntelliTrace &#45; Wyświetlanie zdarzeń &#43; żądania sieci Web](../debugger/media/entersharepointcorrelationid2.png "EnterSharePointCorrelationID2")

   Możesz zobaczyć te rodzaje zdarzeń programu SharePoint wraz ze zdarzeniami IntelliTrace:

- **Zdarzenia profilu użytkownika**

     Te zdarzenia są wykonywane, gdy program SharePoint ładuje profil użytkownika i gdy właściwości profilu użytkownika są odczytywane lub zmieniane.

- **Zdarzenia Unified Logging system (ULS)**

     Microsoft Monitoring Agent rejestruje podzestaw zdarzeń ULS programu SharePoint i następujące pola:

    |**Pole IntelliTrace**|**Pole ULS programu SharePoint**|
    |----------------------------|------------------------------|
    |**ID (Identyfikator)**|**EventID**|
    |**Poziomie**|**Poziomie**|
    |**Identyfikator kategorii**|**Identyfikator kategorii**|
    |**Kategoria**|**Kategoria**|
    |**Obszar**|**Product**|
    |**Dane wyjściowe**|**Wiadomość**|
    |**Identyfikator korelacji**|**Identyfikator korelacji**|

##### <a name="start-debugging-from-an-unhandled-exception"></a>Uruchom debugowanie z nieobsłużonego wyjątku

1. Wybierz identyfikator korelacji programu SharePoint dla wyjątku. Wyjątki są pogrupowane według typu i stosu wywołań.

2. Obowiązkowe Rozwiń węzeł **stos wywołań** , aby zobaczyć stos wywołań dla grupy wyjątków.

3. Wybierz pozycję **Debuguj wyjątek** , aby rozpocząć debugowanie w punkcie, w którym wystąpił wyjątek.

    ![IntelliTrace &#45; dziennika nieobsłużonych wyjątków programu SharePoint](../debugger/media/sharepointunhandledexceptions_intellitrace.png "SharePointUnhandledExceptions_IntelliTrace")

   Aby zapoznać się z przewodnikiem, zobacz [Przewodnik: debugowanie aplikacji SharePoint za pomocą IntelliTrace](../sharepoint/walkthrough-debugging-a-sharepoint-application-by-using-intellitrace.md). Aby poznać rodzaje danych, które są rejestrowane przez agenta, zobacz [IntelliTrace Features](../debugger/intellitrace-features.md).

### <a name="threads-list"></a><a name="ThreadsList"></a> Lista wątków
 Przejrzyj zarejestrowane wątki, które zostały uruchomione w procesie docelowym. Możesz rozpocząć debugowanie od pierwszego prawidłowego zdarzenia IntelliTrace w wybranym wątku.

##### <a name="to-start-debugging-from-a-specific-thread"></a>Aby rozpocząć debugowanie z określonego wątku

1. Na **liście wątki** wybierz wątek.

2. W dolnej części **listy wątki** wybierz **Rozpocznij debugowanie**. Możesz również kliknąć dwukrotnie wątek.

    Aby rozpocząć debugowanie w miejscu, w którym rozpoczyna się aplikacja, kliknij dwukrotnie **wątek główny**. Zobacz [Funkcje IntelliTrace](../debugger/intellitrace-features.md).

   Dane wątku tworzone przez użytkownika mogą być bardziej przydatne niż wątki tworzone przez serwer i zarządzane dla aplikacji sieci Web hostowanych przez usługi IIS.

|**Kolumna**|**Pokazuje**|
|----------------|-------------------|
|**ID (Identyfikator)**|Numer IDENTYFIKACYJNy wątku|
|**Nazwa**|Nazwa wątku. Wątki nienazwane są wyświetlane jako " \<No Name> ".|
|**Godzina rozpoczęcia**|Czas utworzenia wątku|
|**Czas zakończenia**|Czas ukończenia wątku|

##### <a name="to-start-debugging-from-a-specific-test-step"></a>Aby rozpocząć debugowanie z określonego kroku testu

1. Rozwiń pozycję **Siatka kroków testu**. Wybierz etap testu.

2. W dolnej części **siatki kroków testu** wybierz **Rozpocznij debugowanie**. Możesz również kliknąć dwukrotnie krok testu.

     Spowoduje to uruchomienie debugowania po pierwszym prawidłowym zdarzeniu IntelliTrace po wybranym kroku testu.

     Gdy istnieją dane testowe, IntelliTrace próbuje rozwiązać skojarzoną kompilację Team Foundation Server, która została użyta do przeprowadzenia przebiegu testu. Jeśli kompilacja zostanie znaleziona, skojarzone symbole aplikacji są rozwiązywane automatycznie.

|**Pole**|**Pokazuje**|
|---------------|-------------------|
|**Sesja testowa**|Zarejestrowane sesje testowe. Zazwyczaj istnieje tylko jeden. Ta lista jest pusta, jeśli dane testowe zostały utworzone przy użyciu testu ręcznego.|
|**Przypadek testowy**|Przypadki testowe z wybranej sesji testowej. Ta lista jest pusta, jeśli dane testowe zostały utworzone przy użyciu testu ręcznego.|
|**Siatka kroków testu**|Kroki testu, które zostały zarejestrowane z wynikiem testu lub zakończą się niepowodzeniem|

### <a name="system-info"></a><a name="SystemInfo"></a> Informacje o systemie
 W tej sekcji przedstawiono szczegółowe informacje o systemie, który jest hostowany w aplikacji, na przykład o sprzęcie, systemie operacyjnym, środowisku i informacje specyficzne dla procesu.

### <a name="modules"></a><a name="Modules"></a> Moduły
 W tej sekcji przedstawiono moduły, które zostały załadowane przez proces docelowy. Moduły są wyświetlane w kolejności, w jakiej zostały załadowane.

|**Kolumna**|**Pokazuje**|
|----------------|-------------------|
|**Nazwa modułu**|Nazwa pliku modułu|
|**Ścieżka modułu**|Lokalizacja dysku, na którym moduł został załadowany|
|**Identyfikator modułu**|Unikatowy identyfikator modułu, który jest specyficzny dla wersji i przyczynia się do zgodnych plików symboli (PDB). Zobacz [Znajdowanie plików symboli (. pdb) i plików źródłowych](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).|

### <a name="where-can-i-get-more-information"></a>Gdzie można uzyskać więcej informacji?
 [Korzystanie z autonomicznego modułu zbierającego funkcji IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md)

 [Funkcje IntelliTrace](../debugger/intellitrace-features.md)

 [Zbieraj więcej danych diagnostycznych w testach ręcznych](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts)

 [IntelliTrace](../debugger/intellitrace.md)

#### <a name="forums"></a>Fora
 [Visual Studio Debugger](https://social.msdn.microsoft.com/Forums/en-US/home)

#### <a name="guidance"></a>Wskazówki
 [Testowanie w celu ciągłego dostarczania za pomocą programu Visual Studio 2012 — Rozdział 6: Przybornik testowy](/previous-versions/msp-n-p/jj159337(v=pandp.10))
