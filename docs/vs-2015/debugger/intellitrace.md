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
ms.openlocfilehash: a3a3e68874bb3295f6696bbdadb3c470a7f2a4ad
ms.sourcegitcommit: da5ebc29544fdbdf625ab4922c9777faf2bcae4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/29/2020
ms.locfileid: "82586624"
---
# <a name="intellitrace"></a>IntelliTrace
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu można znaleźć pod adresem [IntelliTrace](/visualstudio/debugger/intellitrace) .  
  
Możesz poświęcać mniej czasu na Debugowanie aplikacji, gdy używasz IntelliTrace do rejestrowania i śledzenia historii wykonywania kodu. Błędy można łatwo znaleźć, ponieważ IntelliTrace umożliwia:  
  
- Rejestrowanie określonych zdarzeń  
  
   Badaj kod powiązany, dane wyświetlane w oknie **zmiennych lokalnych** podczas zdarzeń debugera i informacje o wywołaniu funkcji  
  
- Debuguj błędy, które są trudne do odtworzenia lub występują w przypadku wdrożenia  
  
  Możesz użyć IntelliTrace w wersji Visual Studio Enterprise (ale nie wersji Professional lub Community).  
  
## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?  
  
|||  
|-|-|  
|**Debuguj moją aplikację przy użyciu IntelliTrace:**<br /><br /> -Pokaż poprzednie zdarzenia.<br />-Wyświetla informacje o wywołaniu dla przeszłych zdarzeń.<br />-Zapisz moją sesję IntelliTrace.<br />— Kontroluj dane zbierane przez IntelliTrace.|-   [Przewodnik: używanie IntelliTrace](../debugger/walkthrough-using-intellitrace.md)<br />     [Funkcje IntelliTrace](../debugger/intellitrace-features.md)<br />-   [Konfigurowanie IntelliTrace](https://msdn.microsoft.com/7657ecab-e07e-4b1b-872d-f05d966be37e)<br />-   [Debugowanie historyczne](../debugger/historical-debugging.md)|  
|**Zbieraj dane IntelliTrace podczas sesji testowej w Test Manager**|-   [Zbieraj więcej danych diagnostycznych w testach ręcznych](https://msdn.microsoft.com/library/bb5a2cc0-84f5-4dfe-9560-ca3d313aefd2)|  
|**Zbieraj dane IntelliTrace z wdrożonych aplikacji**|-   [Korzystanie z autonomicznego modułu zbierającego IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md)|  
|**Rozpocznij debugowanie z pliku dziennika IntelliTrace (plik iTrace).**|-   [Korzystanie z zapisanych danych IntelliTrace](../debugger/using-saved-intellitrace-data.md)|  
  
## <a name="what-apps-can-i-debug-with-intellitrace"></a><a name="IntelliTraceSupport"></a>Jakie aplikacje można debugować za pomocą IntelliTrace?  
  
|||  
|-|-|  
|**Obsługiwane**|-Visual Basic i aplikacje Visual C#, które używają .NET Framework 2,0 lub nowszych wersji.<br />     Można debugować większość aplikacji, w tym ASP.NET, Microsoft Azure, Windows Forms, WCF, WPF, Windows Workflow, SharePoint 2010, SharePoint 2013 i 64-bitowe aplikacje.<br />     Aby debugować aplikacje programu SharePoint za pomocą IntelliTrace, zobacz [Przewodnik: debugowanie aplikacji SharePoint przy użyciu IntelliTrace](https://msdn.microsoft.com/library/4bd80d2f-f680-4bf4-81c3-f14e8185f6a4).<br />     Aby debugować Microsoft Azure aplikacje za pomocą IntelliTrace, zobacz [debugowanie opublikowanej usługi w chmurze za pomocą usługi IntelliTrace i programu Visual Studio](../azure/vs-azure-tools-intellitrace-debug-published-cloud-services.md).|  
|**Ograniczona pomoc techniczna**|-Aplikacje F # na zasadach eksperymentalnych<br />— Aplikacje ze sklepu Windows obsługiwane tylko dla zdarzeń|  
|**Nieobsługiwane**|-C++, inne języki i skrypt<br />— Usługi systemu Windows, Silverlight, Xbox lub [!INCLUDE[winmobile](../includes/winmobile-md.md)] aplikacje|  
  
> [!NOTE]
> Jeśli chcesz debugować proces, który jest już uruchomiony, nie możesz użyć IntelliTrace. IntelliTrace należy uruchomić, gdy proces jest uruchamiany.  
  
## <a name="why-debug-with-intellitrace"></a><a name="IntelliTraceVSTraditional"></a>Dlaczego debugować za pomocą IntelliTrace?  
 Tradycyjne lub na *żywo* debugowanie pokazuje tylko bieżący stan aplikacji z ograniczoną ilością danych na temat przeszłych zdarzeń. Musisz wywnioskować te zdarzenia na podstawie bieżącego stanu aplikacji lub trzeba ponownie utworzyć te zdarzenia przez ponowne uruchomienie aplikacji.  
  
 IntelliTrace rozszerza standardowe debugowanie poprzez zapisywanie określonych zdarzeń i danych w konkretnym czasie. Dzięki temu można zobaczyć, co się stało w aplikacji bez konieczności jej ponownego uruchamiania, zwłaszcza w przypadku wcześniejszego przekroczenia błędu. Funkcja IntelliTrace jest domyślnie włączana podczas standardowego debugowania i zbiera dane automatycznie i w sposób niewidoczny. W ten sposób można łatwo przełączać się między standardowym debugowaniem i debugowaniem IntelliTrace, aby wyświetlić zapisane informacje. Zobacz [IntelliTrace funkcje](../debugger/intellitrace-features.md) i [jakie dane są zbierane przez IntelliTrace?](#WhatData)  
  
 Funkcja IntelliTrace może również debugować błędy, które są trudne do odtworzenia lub mają miejsce we wdrożeniu. Możesz zbierać dane IntelliTrace i zapisywać je do pliku dziennika IntelliTrace (plik iTrace). Plik iTrace zawiera szczegóły dotyczące wyjątków, zdarzeń dotyczących wydajności, żądań sieci Web, danych testowych, wątków, modułów i innych informacji o systemie. Możesz otworzyć ten plik w Visual Studio Enterprise, wybierz element i Rozpocznij debugowanie za pomocą IntelliTrace. Dzięki temu możesz przejść do dowolnego zdarzenia w pliku i zobaczyć szczegółowe informacje o aplikacji w tym momencie.  
  
 Możesz zapisywać dane IntelliTrace z następujących źródeł:  
  
- Sesja IntelliTrace w programie Visual Studio 2015 Enterprise lub wcześniejszych wersjach Visual Studio Ultimate.  
  
- Sesja testowa w Microsoft Test Manager  
  
- Aplikacje internetowe ASP.NET hostowane w usłudze IIS lub aplikacje SharePoint 2010 i SharePoint 2013 działające we wdrożeniu, gdy używasz programu Microsoft Monitoring Agent samodzielnie lub w połączeniu z programem System Center 2012. Zobacz [Używanie autonomicznego modułu zbierającego IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md) i [monitorowania za pomocą Microsoft Monitoring Agent](https://technet.microsoft.com/library/dn465153.aspx).  
  
  Oto kilka przykładów, jak IntelliTrace może pomóc w debugowaniu:  
  
- Aplikacja ma uszkodzony plik danych, ale nie wiadomo, gdzie wystąpił to zdarzenie.  
  
   Bez IntelliTrace należy przeglądać kod, aby znaleźć wszystkie możliwe dostęp do pliku, umieścić punkty przerwania w tych dostępach i ponownie uruchomić aplikację, aby znaleźć miejsce wystąpienia problemu. Za pomocą IntelliTrace można zobaczyć wszystkie zebrane zdarzenia dostępu do plików i szczegółowe informacje o aplikacji po wystąpieniu każdego zdarzenia.  
  
- Ma miejsce wyjątek.  
  
   Bez IntelliTrace pojawia się komunikat o wyjątku, ale nie masz wielu informacji o zdarzeniach, które doprowadziły do niego. Możesz analizować stos wywołań, aby zobaczyć łańcuch wywołań, który doprowadził do wyjątku, ale nie widać sekwencji zdarzeń, które wystąpiły podczas tych wywołań. Z IntelliTrace można sprawdzić zdarzenia, które miały miejsce przed wystąpieniem wyjątku.  
  
- Aplikacja ulega awarii na komputerze testowym, ale pomyślnie działa na komputerze deweloperskim.  
  
   Możesz zbierać dane IntelliTrace z Microsoft Test Manager, zapisać dane w pliku iTrace i dołączyć ten plik do elementu pracy programu Team Foundation Server, aby przeprowadzić późniejszą analizę. Zobacz [Zbieranie większej ilości danych diagnostycznych w testach ręcznych](https://msdn.microsoft.com/library/bb5a2cc0-84f5-4dfe-9560-ca3d313aefd2) i [Używanie zapisanych danych IntelliTrace](../debugger/using-saved-intellitrace-data.md).  
  
- Wystąpił błąd lub awaria w wdrożonej aplikacji.  
  
   W przypadku aplikacji opartych na Microsoft Azure można skonfigurować zbieranie danych IntelliTrace przed opublikowaniem aplikacji. Gdy aplikacja jest uruchomiona, IntelliTrace zapisuje dane w pliku. iTrace. Zobacz [debugowanie opublikowanej usługi w chmurze za pomocą IntelliTrace i programu Visual Studio](../azure/vs-azure-tools-intellitrace-debug-published-cloud-services.md).  
  
   W przypadku aplikacji internetowych ASP.NET obsługiwanych przez usługi IIS 7.0, 7.5 i 8.0 oraz aplikacji SharePoint 2010 lub SharePoint 2013 możesz używać programu Microsoft Monitoring Agent, samego lub w połączeniu z System Center 2012, aby zapisywać dane IntelliTrace w pliku iTrace.  
  
   Jest to przydatne, gdy chcesz zdiagnozować problemy z aplikacjami w trakcie wdrażania. Zobacz [Używanie autonomicznego modułu zbierającego IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md).  
  
## <a name="what-data-does-intellitrace-collect"></a><a name="WhatData"></a>Jakie dane są zbierane przez IntelliTrace?  
 **Zbieranie informacji o zdarzeniach**  
  
 Domyślnie IntelliTrace rejestruje tylko zdarzenia IntelliTrace: zdarzenia debugera, wyjątki, zdarzenia .NET Framework i inne zdarzenia systemowe, które mogą pomóc w debugowaniu. Możesz wybrać typy zdarzeń IntelliTrace, które mają być zbierane, z wyjątkiem zdarzeń debugera i wyjątków, które są zawsze zbierane. Zobacz [Konfigurowanie IntelliTrace](https://msdn.microsoft.com/7657ecab-e07e-4b1b-872d-f05d966be37e).  
  
- **Zdarzenia debugera**  
  
   IntelliTrace zawsze zapisuje zdarzenia mające miejsce w debugerze Visual Studio. Uruchamianie aplikacji jest na przykład zdarzeniem debugera. Inne zdarzenia debugera są zatrzymywane zdarzenia, co powoduje przerwanie wykonywania aplikacji. Na przykład program trafi do punktu przerwania, trafi punkt śledzenia lub wykonuje polecenie **kroku** .  
  
   Aby poprawić wydajność, IntelliTrace nie zapisuje każdej możliwej wartości dla zdarzenia debugera. Zamiast tego zapisuje następujące wartości:  
  
  - Wartości w oknie **zmiennych lokalnych** . Pozostaw otwarte okno **lokalne** , aby wyświetlić te wartości.  
  
  - Wartości w oknie **samochody** tylko wtedy, gdy okno **autowypełniane** jest otwarte  
  
  - Wartości w DataTips, które są wyświetlane, gdy ustawisz wskaźnik myszy nad zmienną w oknie źródłowym, aby zobaczyć jej wartość. IntelliTrace nie zbiera wartości w unieruchomionych DataTips.  
  
- **Wyjątki**  
  
   IntelliTrace zapisuje typ wyjątku i komunikat dla tego rodzaju wyjątków:  
  
  - Obsługiwane wyjątki, gdy wyjątek jest generowany i przechwycony  
  
  - Nieobsługiwane wyjątki  
  
- **Zdarzenia .NET Framework**  
  
   IntelliTrace domyślnie zapisuje najbardziej typowe zdarzenia .NET Framework. Przykład:  
  
  - W przypadku zdarzenia dostępu do plików IntelliTrace zbiera nazwę pliku.  
  
  - W przypadku zdarzenia sprawdzania pola wyboru IntelliTrace zbiera stan pola wyboru i tekst.  
  
- **Zdarzenia aplikacji SharePoint 2010 i SharePoint 2013**  
  
   Można zapisać zdarzenia dotyczące profili użytkowników i zdarzenia w podzbiorze Unified Logging System (ULS) do aplikacji SharePoint 2010 i 2013 działających poza programem Visual Studio. Zdarzenia te można zapisać w pliku iTrace. Wymaga Visual Studio Enterprise 2015, wcześniejszej wersji Visual Studio Ultimate lub [Microsoft Monitoring Agent](https://go.microsoft.com/fwlink/?LinkID=309771) uruchomione w trybie **śledzenia** .  
  
   Po otwarciu pliku iTrace wprowadź identyfikator korelacji programu SharePoint, aby znaleźć odpowiadające mu żądanie sieci Web, zobaczyć zarejestrowane zdarzenia i rozpocząć debugowanie od określonego zdarzenia. Jeśli plik zawiera nieobsłużone wyjątki, można wybrać identyfikator korelacji, aby uruchomić debugowanie wyjątku.  
  
   Zobacz:  
  
  - [Korzystanie z autonomicznego modułu zbierającego funkcji IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md)  
  
  - [Korzystanie z zapisanych danych funkcji IntelliTrace](../debugger/using-saved-intellitrace-data.md)  
  
  - [Przewodnik: Debugowanie aplikacji SharePoint przy użyciu narzędzia IntelliTrace](https://msdn.microsoft.com/library/4bd80d2f-f680-4bf4-81c3-f14e8185f6a4)  
  
  **Zbieranie informacji o wywołaniu funkcji**  
  
  Możesz skonfigurować IntelliTrace, aby zbierać informacje dotyczące wywołań dla funkcji. Te informacje pozwalają wyświetlać historię stosu wywołań i umożliwiają poruszanie się w wywołaniach kodu w dowolnym kierunku. W przypadku każdego wywołania funkcji IntelliTrace rejestruje następujące dane:  
  
- Nazwa funkcji  
  
- Wartości pierwotnych typów danych przekazywanych jako parametry w punktach wejścia do funkcji i zwracanych w punktach wyjścia z funkcji  
  
- Wartości właściwości automatycznych, gdy są one odczytywane lub zmieniane  
  
- Wskaźniki do pierwszego poziomu obiektów podrzędnych, ale nie ich wartości inne, niż gdyby były równe null lub nie  
  
> [!NOTE]
> IntelliTrace zbiera tylko 256 pierwszych obiektów w tablicach i pierwszych 256 znaków w ciągach.  
  
 Zobacz [Konfigurowanie IntelliTrace](https://msdn.microsoft.com/7657ecab-e07e-4b1b-872d-f05d966be37e).  
  
 **Zbieranie informacji o module**  
  
 Aby kontrolować, ile informacji na temat wywołania gromadzi IntelliTrace, określ tylko te moduły, która Cię interesują. Może to pomóc w ulepszaniu wydajności aplikacji podczas zbierania. Zobacz [Konfigurowanie IntelliTrace](https://msdn.microsoft.com/7657ecab-e07e-4b1b-872d-f05d966be37e).  
  
## <a name="will-intellitrace-slow-down-my-application"></a><a name="AffectPerformance"></a>IntelliTrace spowalnia moją aplikację?  
 IntelliTrace domyślnie zbiera dane tylko dla wybranych zdarzeń IntelliTrace. Może to być niespowolnienie aplikacji, w zależności od struktury i organizacji kodu. Na przykład jeśli IntelliTrace często zapisuje zdarzenie, może to spowolnić aplikację. Może być również konieczne rozważenie refaktoryzacji aplikacji.  
  
 Zbieranie informacji o wywołaniu może znacząco spowolnić aplikację. Może to również zwiększyć rozmiar wszystkich plików dziennika IntelliTrace (iTrace) zapisywanych na dysku. Aby zminimalizować te skutki, zbieraj informacji o wywołaniach tylko interesujących Cię modułów.  Aby zmienić maksymalny rozmiar plików. iTrace, przejdź do pozycji **Narzędzia**, **Opcje**, **IntelliTrace**, **Zaawansowane**. Zobacz [Konfigurowanie IntelliTrace](https://msdn.microsoft.com/7657ecab-e07e-4b1b-872d-f05d966be37e).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Funkcje IntelliTrace](../debugger/intellitrace-features.md)  
  
 [Konfigurowanie IntelliTrace](https://msdn.microsoft.com/7657ecab-e07e-4b1b-872d-f05d966be37e)  
  
 [Uwzględnianie danych śledzenia diagnostyki z błędami, które są trudne do odtworzenia](https://msdn.microsoft.com/library/944ae9af-5a55-4c58-b520-0108c03b3564)  
  
 [Diagnozowanie problemów po wdrożeniu](../debugger/diagnose-problems-after-deployment.md)  
  
 [Korzystanie z zapisanych danych funkcji IntelliTrace](../debugger/using-saved-intellitrace-data.md)  
  
### <a name="blogs"></a>Blogi  
 [Visual Studio ALM i Team Foundation Server](https://devblogs.microsoft.com/devops/welcome-to-the-visual-studio-alm-team-foundation-server-blog/)  
  
### <a name="forums"></a>Fora  
 [Diagnostyka programu Visual Studio](https://social.msdn.microsoft.com/Forums/vsdebug)
