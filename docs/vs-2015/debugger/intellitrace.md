---
title: IntelliTrace | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.historicaldebug.overview
helpviewer_keywords:
- debugger, recording execution history
- debugging, recording execution history
- IntelliTrace [Visual Studio ALM]
- IntelliTrace, debugging applications
- debugger, (See also IntelliTrace [Visual Studio ALM])
- debugging, (See also IntelliTrace [Visual Studio ALM])
- IntelliTrace, collecting data from Test Manager
- IntelliTrace
- Test Manager, debugging with IntelliTrace
- IntelliTrace, debugging after a crash
ms.assetid: 486bfec2-39bd-4d78-892a-42352128ee52
caps.latest.revision: 142
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c9097a8c067ce4e04dd54f879a6c1388f854d7ec
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60079308"
---
# <a name="intellitrace"></a>IntelliTrace
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [IntelliTrace](https://docs.microsoft.com/visualstudio/debugger/intellitrace) .  
  
Spędzisz mniej czasu na debugowaniu aplikacji, jeśli będziesz używać IntelliTrace do rejestrowania i śledzenia historii wykonywania kodu. Błędów można znaleźć łatwe, ponieważ IntelliTrace umożliwia:  
  
- Rejestruje określone zdarzenia  
  
   Sprawdzić kod pokrewny, dane wyświetlane w **lokalne** okna podczas zdarzenia debuger i informacje o wywołaniach funkcji  
  
- Debugowanie błędów, które są trudne do odtworzenia lub zdarzyły się we wdrożeniu  
  
  Za pomocą funkcji IntelliTrace w programie Visual Studio Enterprise (ale nie w wersjach Professional lub Community).  
  
## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?  
  
|||  
|-|-|  
|**Debuguj aplikację przy użyciu funkcji IntelliTrace:**<br /><br /> — Pokaż poprzednie zdarzenia.<br />— Pokaż informacje wywołań w przeszłych zdarzeń.<br />-Zapisz sesję IntelliTrace.<br />-Control IntelliTrace zbiera dane.|-   [Wskazówki: Używanie funkcji IntelliTrace](../debugger/walkthrough-using-intellitrace.md)<br />     [Funkcje IntelliTrace](../debugger/intellitrace-features.md)<br />-   [Konfigurowanie funkcji IntelliTrace](http://msdn.microsoft.com/7657ecab-e07e-4b1b-872d-f05d966be37e)<br />-   [Debugowanie historyczne](../debugger/historical-debugging.md)|  
|**Zbieraj dane IntelliTrace podczas sesji testowej w programie Test Manager**|-   [Zbieranie większej ilości danych podczas wykonywania testów ręcznych](http://msdn.microsoft.com/library/bb5a2cc0-84f5-4dfe-9560-ca3d313aefd2)|  
|**Zbieraj dane IntelliTrace z wdrożonych aplikacji**|-   [Przy użyciu autonomicznego modułu zbierającego IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md)|  
|**Uruchom debugowanie z pliku dziennika IntelliTrace (plik itrace).**|-   [Przy użyciu zapisanych danych funkcji IntelliTrace](../debugger/using-saved-intellitrace-data.md)|  
  
## <a name="IntelliTraceSupport"></a> Jakie aplikacje można debugować za pomocą IntelliTrace?  
  
|||  
|-|-|  
|**Obsługiwane**|— W przypadku aplikacji w języku Visual Basic i Visual C#, które używają .NET Framework 2.0 lub nowszych wersji.<br />     Możesz debugować większość aplikacji, w tym ASP.NET, Microsoft Azure, Windows Forms, WCF, WPF, Windows Workflow, SharePoint 2010, SharePoint 2013 i aplikacje 64-bitowe.<br />     Aby debugować aplikacje programu SharePoint za pomocą IntelliTrace, zobacz [instruktażu: Debugowanie aplikacji SharePoint przy użyciu funkcji IntelliTrace](http://msdn.microsoft.com/library/4bd80d2f-f680-4bf4-81c3-f14e8185f6a4).<br />     Aby debugować aplikacje Microsoft Azure za pomocą IntelliTrace, zobacz [debugowanie opublikowanych usług w chmurze za pomocą IntelliTrace i Visual Studio](../azure/vs-azure-tools-intellitrace-debug-published-cloud-services.md).|  
|**Ograniczona obsługa**|- F# aplikacje na zasadach eksperymentalnych<br />-Windows Store apps obsługiwane tylko pod kątem zdarzeń|  
|**Nieobsługiwane**|-C++, inne języki i skryptu<br />— Usługi Windows, Silverlight, Xbox lub [!INCLUDE[winmobile](../includes/winmobile-md.md)] aplikacji|  
  
> [!NOTE]
>  Jeśli chcesz debugować proces, który jest już uruchomiony, nie możesz użyć IntelliTrace. IntelliTrace należy uruchomić, gdy proces jest uruchamiany.  
  
## <a name="IntelliTraceVSTraditional"></a> Dlaczego debugować za pomocą IntelliTrace?  
 Tradycyjny lub *live* debugowania pokazuje tylko aplikacji bieżący stan, z ograniczoną ilością danych na temat przeszłych zdarzeń. Musisz albo wywnioskować te zdarzenia, w oparciu o bieżący stan aplikacji lub musisz odtworzyć te zdarzenia, ponownie uruchamiając aplikację.  
  
 IntelliTrace rozszerza standardowe debugowanie poprzez zapisywanie określonych zdarzeń i danych w konkretnym czasie. Dzięki temu możesz zobaczyć, co wydarzyło się w aplikacji bez konieczności ponownego uruchamiania, zwłaszcza, jeśli jest to krok w przeszłości w przypadku błędu. Funkcja IntelliTrace jest domyślnie włączana podczas standardowego debugowania i zbiera dane automatycznie i w sposób niewidoczny. W ten sposób można łatwo przełączać się między standardowym debugowaniem i debugowaniem IntelliTrace, aby wyświetlić zapisane informacje. Zobacz [funkcji IntelliTrace](../debugger/intellitrace-features.md) i [jakie dane są zbierane przez IntelliTrace?](#WhatData)  
  
 Funkcja IntelliTrace może również debugować błędy, które są trudne do odtworzenia lub mają miejsce we wdrożeniu. Możesz zbierać dane IntelliTrace i zapisywać je do pliku dziennika IntelliTrace (plik iTrace). Plik iTrace zawiera szczegóły dotyczące wyjątków, zdarzeń dotyczących wydajności, żądań sieci Web, danych testowych, wątków, modułów i innych informacji o systemie. Możesz otworzyć ten plik w programie Visual Studio Enterprise, zaznacz element i Rozpocznij debugowanie z IntelliTrace. Dzięki temu można przejść do dowolnego zdarzenia w pliku i zobaczyć szczegółowe informacje o aplikacji w danym momencie.  
  
 Możesz zapisywać dane IntelliTrace z następujących źródeł:  
  
- Sesja IntelliTrace w Visual Studio 2015 Enterprise lub starszych wersji programu Visual Studio Ultimate.  
  
- Sesji testowej w programie Microsoft Test Manager  
  
- Aplikacje internetowe ASP.NET hostowane w usłudze IIS lub aplikacje SharePoint 2010 i SharePoint 2013 działające we wdrożeniu, gdy używasz programu Microsoft Monitoring Agent samodzielnie lub w połączeniu z programem System Center 2012. Zobacz [przy użyciu autonomicznego modułu zbierającego IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md) i [monitorowanie przy użyciu programu Microsoft Monitoring Agent](http://technet.microsoft.com/library/dn465153.aspx).  
  
  Oto kilka przykładów, jak IntelliTrace może pomóc w debugowaniu:  
  
- Aplikacja ma uszkodzony plik danych, ale nie wiesz, gdzie miało miejsce to zdarzenie.  
  
   Nie mając IntelliTrace musisz szukać kodu, aby znaleźć wszystkie możliwe dostępy do pliku, ustalić punkty przerwania w tych dostępach i ponownie uruchom aplikację, aby znaleźć miejsce wystąpienia problemu. Za pomocą IntelliTrace widać wszystkie zdarzenia zebrane dostępu do pliku i szczegółowe informacje na temat aplikacji podczas każdorazowego wystąpienia zdarzenia.  
  
- Ma miejsce wyjątek.  
  
   Bez IntelliTrace pojawia się komunikat o wyjątku, ale nie masz wielu informacji o zdarzeniach, które doprowadziły do niego. Możesz analizować stos wywołań, aby zobaczyć łańcuch wywołań, który doprowadził do wyjątku, ale nie widać sekwencji zdarzeń, które wystąpiły podczas tych wywołań. Z IntelliTrace można sprawdzić zdarzenia, które miały miejsce przed wystąpieniem wyjątku.  
  
- Aplikacja przestaje działać na komputerze testowym, ale pomyślnie działa na komputerze deweloperskim.  
  
   Możesz zbierać dane IntelliTrace z Microsoft Test Manager, zapisać dane w pliku iTrace i dołączyć ten plik do elementu pracy programu Team Foundation Server, aby przeprowadzić późniejszą analizę. Zobacz [zbieranie większej ilości danych podczas wykonywania testów ręcznych](http://msdn.microsoft.com/library/bb5a2cc0-84f5-4dfe-9560-ca3d313aefd2) i [używanie zapisanych danych funkcji IntelliTrace](../debugger/using-saved-intellitrace-data.md).  
  
- Błąd lub awaria ma miejsce we wdrożonej aplikacji.  
  
   Dla aplikacji opartych na platformie Azure firmy Microsoft można skonfigurować zbieranie danych IntelliTrace, przed opublikowaniem aplikacji. Podczas wykonywania aplikacji IntelliTrace zapisuje dane w pliku .iTrace. Zobacz [debugowanie opublikowanych usług w chmurze za pomocą IntelliTrace i programu Visual Studio](../azure/vs-azure-tools-intellitrace-debug-published-cloud-services.md).  
  
   W przypadku aplikacji internetowych ASP.NET obsługiwanych przez usługi IIS 7.0, 7.5 i 8.0 oraz aplikacji SharePoint 2010 lub SharePoint 2013 możesz używać programu Microsoft Monitoring Agent, samego lub w połączeniu z System Center 2012, aby zapisywać dane IntelliTrace w pliku iTrace.  
  
   Jest to przydatne, gdy chcesz zdiagnozować problemy z aplikacjami w trakcie wdrażania. Zobacz [przy użyciu autonomicznego modułu zbierającego IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md).  
  
## <a name="WhatData"></a> Jakie dane są zbierane przez IntelliTrace?  
 **Zbieranie informacji o zdarzeniach**  
  
 Domyślnie IntelliTrace zapisuje tylko zdarzenia funkcji IntelliTrace: debugera, zdarzenia, wyjątki, zdarzenia .NET Framework i inne zdarzenia systemowe, które mogą pomóc w debugowaniu. Możesz wybrać typy zdarzeń IntelliTrace, które mają być zbierane, z wyjątkiem zdarzeń debugera i wyjątków, które są zawsze zbierane. Zobacz [skonfiguruj IntelliTrace](http://msdn.microsoft.com/7657ecab-e07e-4b1b-872d-f05d966be37e).  
  
- **Zdarzenia debugera**  
  
   IntelliTrace zawsze zapisuje zdarzenia mające miejsce w debugerze Visual Studio. Na przykład uruchamianie aplikacji jest zdarzenia debuger. Inne zdarzenia debugera są zdarzeniami zatrzymującymi, które powodują przerwanie wykonywania aplikacji. Na przykład program osiąga punkt przerwania, osiąga punkt śledzenia lub wykonuje **kroku** polecenia.  
  
   Aby poprawić wydajność, IntelliTrace nie zapisuje każdej możliwej wartości dla zdarzenia debugera. Zamiast tego zapisuje następujące wartości:  
  
  - Wartości w **lokalne** okna. Zachowaj **lokalne** okna otwarte, aby zobaczyć te wartości.  
  
  - Wartości w **Autos** tylko wtedy, gdy okno **Autos** jest otwarte okno  
  
  - Wartości w DataTips, które są wyświetlane, gdy ustawisz wskaźnik myszy nad zmienną w oknie źródłowym, aby zobaczyć jej wartość. IntelliTrace nie zbiera wartości w unieruchomionych DataTips.  
  
- **Wyjątki**  
  
   IntelliTrace zapisuje typ wyjątku i komunikat dla tego rodzaju wyjątków:  
  
  - Obsługiwane wyjątki, gdy wyjątek jest generowany i przechwycony  
  
  - Nieobsługiwane wyjątki  
  
- **Zdarzenia .NET framework**  
  
   IntelliTrace domyślnie zapisuje najbardziej typowe zdarzenia .NET Framework. Na przykład:  
  
  - W przypadku zdarzenia dostępu do plików IntelliTrace zbiera nazwę pliku.  
  
  - W przypadku zdarzenia sprawdzania pola wyboru IntelliTrace zbiera stan pola wyboru i tekst.  
  
- **Zdarzenia aplikacji programów SharePoint 2010 i SharePoint 2013**  
  
   Można zapisać zdarzenia dotyczące profili użytkowników i zdarzenia w podzbiorze Unified Logging System (ULS) do aplikacji SharePoint 2010 i 2013 działających poza programem Visual Studio. Zdarzenia te można zapisać w pliku iTrace. Wymaga programu Visual Studio Enterprise 2015 poprzedniej wersji programu Visual Studio Ultimate lub [Microsoft Monitoring Agent](http://go.microsoft.com/fwlink/?LinkId=320384) działające w **śledzenia** trybu.  
  
   Po otwarciu pliku iTrace wprowadź identyfikator korelacji programu SharePoint, aby znaleźć odpowiadające mu żądanie sieci Web, zobaczyć zarejestrowane zdarzenia i rozpocząć debugowanie od określonego zdarzenia. Jeśli plik zawiera nieobsłużone wyjątki, można wybrać identyfikator korelacji, aby uruchomić debugowanie wyjątku.  
  
   Zobacz:  
  
  - [Korzystanie z autonomicznego modułu zbierającego funkcji IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md)  
  
  - [Korzystanie z zapisanych danych funkcji IntelliTrace](../debugger/using-saved-intellitrace-data.md)  
  
  - [Przewodnik: Debugowanie aplikacji SharePoint przy użyciu funkcji IntelliTrace](http://msdn.microsoft.com/library/4bd80d2f-f680-4bf4-81c3-f14e8185f6a4)  
  
  **Gromadzenie informacji o wywołaniach funkcji**  
  
  Możesz skonfigurować IntelliTrace, aby zbierać informacje dotyczące wywołań dla funkcji. Te informacje pozwalają wyświetlać historię stosu wywołań i umożliwiają poruszanie się w wywołaniach kodu w dowolnym kierunku. W przypadku każdego wywołania funkcji IntelliTrace rejestruje następujące dane:  
  
- Nazwa funkcji  
  
- Wartości pierwotnych typów danych przekazywanych jako parametry w punktach wejścia do funkcji i zwracanych w punktach wyjścia z funkcji  
  
- Wartości właściwości automatycznych, gdy są one odczytywane lub zmieniane  
  
- Wskaźniki do pierwszego poziomu obiektów podrzędnych, ale nie ich wartości inne, niż gdyby były równe null lub nie  
  
> [!NOTE]
>  IntelliTrace zbiera tylko 256 pierwszych obiektów w tablicach i pierwszych 256 znaków w ciągach.  
  
 Zobacz [skonfiguruj IntelliTrace](http://msdn.microsoft.com/7657ecab-e07e-4b1b-872d-f05d966be37e).  
  
 **Moduł — zbieranie informacji**  
  
 Aby kontrolować, ile informacji na temat wywołania gromadzi IntelliTrace, określ tylko te moduły, która Cię interesują. Może to zwiększyć wydajność aplikacji podczas zbierania. Zobacz [skonfiguruj IntelliTrace](http://msdn.microsoft.com/7657ecab-e07e-4b1b-872d-f05d966be37e).  
  
## <a name="AffectPerformance"></a> IntelliTrace spowolni moją aplikację?  
 IntelliTrace domyślnie zbiera dane tylko dla wybranych zdarzeń IntelliTrace. To może lub nie może spowolnić aplikację, w zależności od struktury i organizacji kodu. Na przykład jeśli funkcja IntelliTrace często zapisuje zdarzenie, może to spowolnić aplikację. To może również, że możesz rozważenia refaktoryzacji aplikacji.  
  
 Gromadzenie informacji o wywołaniach może znacznie spowolnić pracę aplikacji. Może to również zwiększyć rozmiar wszystkich plików dziennika IntelliTrace (iTrace) zapisywanych na dysku. Aby zminimalizować te skutki, zbieraj informacji o wywołaniach tylko interesujących Cię modułów.  Aby zmienić maksymalny rozmiar plików itrace, przejdź do **narzędzia**, **opcje**, **IntelliTrace**, **zaawansowane**. Zobacz [skonfiguruj IntelliTrace](http://msdn.microsoft.com/7657ecab-e07e-4b1b-872d-f05d966be37e).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Funkcje IntelliTrace](../debugger/intellitrace-features.md)  
  
 [Konfigurowanie funkcji IntelliTrace](http://msdn.microsoft.com/7657ecab-e07e-4b1b-872d-f05d966be37e)  
  
 [Dołączanie danych diagnostycznych śledzenia z usterkami trudnymi do odtworzenia](http://msdn.microsoft.com/library/944ae9af-5a55-4c58-b520-0108c03b3564)  
  
 [Diagnozowanie problemów po wdrożeniu](../debugger/diagnose-problems-after-deployment.md)  
  
 [Korzystanie z zapisanych danych funkcji IntelliTrace](../debugger/using-saved-intellitrace-data.md)  
  
### <a name="blogs"></a>Blogi  
 [Visual Studio ALM + Team Foundation Server](http://go.microsoft.com/fwlink/?LinkID=201340)  
  
### <a name="forums"></a>Fora  
 [Visual Studio Diagnostics](http://go.microsoft.com/fwlink/?LinkId=262263)
