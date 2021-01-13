---
title: IntelliTrace | Microsoft Docs
description: Użyj IntelliTrace, aby rejestrować i śledzić historię wykonywania kodu w programie Visual Studio. Rejestruj konkretne zdarzenia, badaj kod powiązany i Debuguj błędy.
ms.custom: SEO-VS-2020
ms.date: 09/19/2018
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
- IntelliTrace
- IntelliTrace, debugging after a crash
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 518043a38f3a0f6945840a36a1f7fcade5a313d7
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/13/2021
ms.locfileid: "98149004"
---
# <a name="intellitrace-for-visual-studio-enterprise-c-visual-basic-c"></a>IntelliTrace for Visual Studio Enterprise (C#, Visual Basic, C++)

Możesz poświęcać mniej czasu na Debugowanie aplikacji, gdy używasz IntelliTrace do rejestrowania i śledzenia historii wykonywania kodu. Błędy można łatwo znaleźć, ponieważ IntelliTrace umożliwia:

- Rejestrowanie określonych zdarzeń

- Badaj kod powiązany, dane wyświetlane w oknie **zmiennych lokalnych** podczas zdarzeń debugera i informacje o wywołaniu funkcji

- Debuguj błędy, które są trudne do odtworzenia lub występują w przypadku wdrożenia

Możesz użyć IntelliTrace w wersji Visual Studio Enterprise (ale nie wersji Professional lub Community).

## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?

|Scenariusz|Tytuł|
|-|-|
|**Debuguj moją aplikację przy użyciu IntelliTrace:**<br /><br /> -Pokaż poprzednie zdarzenia.<br />-Wyświetla informacje o wywołaniu dla przeszłych zdarzeń.<br />-Zapisz moją sesję IntelliTrace.<br />— Kontroluj dane zbierane przez IntelliTrace.|- [Zbadaj poprzednie Stany aplikacji przy użyciu IntelliTrace](../debugger/view-historical-application-state.md)<br />- [Przewodnik: używanie IntelliTrace](../debugger/walkthrough-using-intellitrace.md)<br />- [Funkcje IntelliTrace](../debugger/intellitrace-features.md)<br />- [Debugowanie historyczne](../debugger/historical-debugging.md)|
|**Zbieraj dane IntelliTrace z wdrożonych aplikacji**|- [Korzystanie z autonomicznego modułu zbierającego IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md)|
|**Rozpocznij debugowanie z pliku dziennika IntelliTrace (plik iTrace).**|- [Korzystanie z zapisanych danych IntelliTrace](../debugger/using-saved-intellitrace-data.md)|

## <a name="what-apps-can-i-debug-with-intellitrace"></a><a name="IntelliTraceSupport"></a> Jakie aplikacje można debugować za pomocą IntelliTrace?

| Poziom pomocy technicznej| Typy aplikacji |
|---------------------| - |
| **Pełna obsługa** | -Visual Basic i aplikacje Visual C#, które używają .NET Framework 2,0 lub nowszych wersji.<br/>Można debugować większość aplikacji, w tym ASP.NET, Microsoft Azure, Windows Forms, WCF, WPF, Windows Workflow, SharePoint 2010, SharePoint 2013 i 64-bitowe aplikacje.<br/>Aby debugować aplikacje programu SharePoint za pomocą IntelliTrace, zobacz [Przewodnik: debugowanie aplikacji SharePoint przy użyciu IntelliTrace](../sharepoint/walkthrough-debugging-a-sharepoint-application-by-using-intellitrace.md).<br/> Aby debugować Microsoft Azure aplikacje za pomocą IntelliTrace, zobacz [debugowanie opublikowanej usługi w chmurze za pomocą usługi IntelliTrace i programu Visual Studio](../azure/vs-azure-tools-intellitrace-debug-published-cloud-services.md). |
| **Ograniczona pomoc techniczna** | -C++ aplikacje obsługujące obsługę systemu Windows przeglądanie migawek przy użyciu IntelliTrace kroku. Obsługiwane są tylko zdarzenia debugera i wyjątków.<br />— Aplikacje .NET Core i ASP.NET Core obsługiwane tylko dla określonych zdarzeń (kontroler MVC, ADO.NET i HTTPClient) w debugowaniu lokalnym. Autonomiczny moduł zbierający nie jest obsługiwany w przypadku aplikacji .NET Core lub ASP.NET Core.<br />-Aplikacje F # na zasadach eksperymentalnych<br />-PLATFORMY UWP aplikacje obsługiwane tylko dla zdarzeń |
| **Nieobsługiwany** | — Inne języki i skrypt<br />— Usługi systemu Windows, Silverlight, Xbox lub aplikacje mobilne systemu Windows |

> [!NOTE]
> Jeśli chcesz debugować proces, który jest już uruchomiony, można zbierać tylko zdarzenia IntelliTrace (bez informacji o wywołaniu). Możesz dołączyć do procesu 32-bitowego lub 64-bitowego tylko na komputerze lokalnym. Zdarzenia, które wystąpiły przed dołączeniem do procesu, nie są zbierane.

## <a name="why-debug-with-intellitrace"></a><a name="IntelliTraceVSTraditional"></a> Dlaczego debugować za pomocą IntelliTrace?

Tradycyjne lub na *żywo* debugowanie pokazuje tylko bieżący stan aplikacji z ograniczoną ilością danych na temat przeszłych zdarzeń. Musisz wywnioskować te zdarzenia na podstawie bieżącego stanu aplikacji lub trzeba ponownie utworzyć te zdarzenia przez ponowne uruchomienie aplikacji.

IntelliTrace rozszerza standardowe debugowanie poprzez zapisywanie określonych zdarzeń i danych w konkretnym czasie. Dzięki temu można zobaczyć, co się stało w aplikacji bez konieczności jej ponownego uruchamiania, zwłaszcza w przypadku wcześniejszego przekroczenia błędu. Funkcja IntelliTrace jest domyślnie włączana podczas standardowego debugowania i zbiera dane automatycznie i w sposób niewidoczny. W ten sposób można łatwo przełączać się między standardowym debugowaniem i debugowaniem IntelliTrace, aby wyświetlić zapisane informacje. Zobacz [IntelliTrace funkcje](../debugger/intellitrace-features.md) i [jakie dane są zbierane przez IntelliTrace?](#WhatData)

Funkcja IntelliTrace może również debugować błędy, które są trudne do odtworzenia lub mają miejsce we wdrożeniu. Możesz zbierać dane IntelliTrace i zapisywać je do pliku dziennika IntelliTrace (plik iTrace). Plik iTrace zawiera szczegóły dotyczące wyjątków, zdarzeń dotyczących wydajności, żądań sieci Web, danych testowych, wątków, modułów i innych informacji o systemie. Możesz otworzyć ten plik w Visual Studio Enterprise, wybierz element i Rozpocznij debugowanie za pomocą IntelliTrace. Dzięki temu możesz przejść do dowolnego zdarzenia w pliku i zobaczyć szczegółowe informacje o aplikacji w tym momencie.

Możesz zapisywać dane IntelliTrace z następujących źródeł:

- Sesja IntelliTrace w programie Visual Studio 2015 Enterprise lub jego nowszych wersjach lub wcześniejszych wersjach Visual Studio Ultimate.

- Aplikacje internetowe ASP.NET hostowane w usłudze IIS lub aplikacje SharePoint 2010 i SharePoint 2013 działające we wdrożeniu, gdy używasz programu Microsoft Monitoring Agent samodzielnie lub w połączeniu z programem System Center 2012. Zobacz [Korzystanie z IntelliTrace autonomicznego modułu zbierającego](../debugger/using-the-intellitrace-stand-alone-collector.md) i [monitorowanie za pomocą Microsoft Monitoring Agent](/previous-versions/system-center/system-center-2012-R2/dn465153(v=sc.12)).

Oto kilka przykładów, jak IntelliTrace może pomóc w debugowaniu:

- Aplikacja ma uszkodzony plik danych, ale nie wiadomo, gdzie wystąpił to zdarzenie.

  Bez IntelliTrace należy przeglądać kod, aby znaleźć wszystkie możliwe dostęp do pliku, umieścić punkty przerwania w tych dostępach i ponownie uruchomić aplikację, aby znaleźć miejsce wystąpienia problemu. Za pomocą IntelliTrace można zobaczyć wszystkie zebrane zdarzenia dostępu do plików i szczegółowe informacje o aplikacji po wystąpieniu każdego zdarzenia.

- Ma miejsce wyjątek.

  Bez IntelliTrace pojawia się komunikat o wyjątku, ale nie masz wielu informacji o zdarzeniach, które doprowadziły do wyjątku. Możesz sprawdzić stos wywołań, aby zobaczyć łańcuch wywołań, które doprowadziły do wyjątku, ale nie widać sekwencji zdarzeń, które wystąpiły podczas tych wywołań. Z IntelliTrace można sprawdzić zdarzenia, które miały miejsce przed wystąpieniem wyjątku.

- Wystąpił błąd lub awaria w wdrożonej aplikacji.

  W przypadku aplikacji opartych na Microsoft Azure można skonfigurować zbieranie danych IntelliTrace przed opublikowaniem aplikacji. Gdy aplikacja jest uruchomiona, IntelliTrace zapisuje dane w pliku. iTrace. Zobacz [debugowanie opublikowanej usługi w chmurze za pomocą IntelliTrace i programu Visual Studio](../azure/vs-azure-tools-intellitrace-debug-published-cloud-services.md).

  W przypadku aplikacji internetowych ASP.NET obsługiwanych przez usługi IIS 7.0, 7.5 i 8.0 oraz aplikacji SharePoint 2010 lub SharePoint 2013 możesz używać programu Microsoft Monitoring Agent, samego lub w połączeniu z System Center 2012, aby zapisywać dane IntelliTrace w pliku iTrace.

  Jest to przydatne, gdy chcesz zdiagnozować problemy z aplikacjami w trakcie wdrażania. Zobacz [Korzystanie z autonomicznego modułu zbierającego IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md).

## <a name="what-data-does-intellitrace-collect"></a><a name="WhatData"></a> Jakie dane są zbierane przez IntelliTrace?

**Zbierz informacje o zdarzeniach**

Domyślnie IntelliTrace rejestruje tylko zdarzenia IntelliTrace: zdarzenia debugera, wyjątki, zdarzenia .NET Framework i inne zdarzenia systemowe, które mogą pomóc w debugowaniu. Możesz wybrać typy zdarzeń IntelliTrace, które mają być zbierane, z wyjątkiem zdarzeń debugera i wyjątków, które są zawsze zbierane. Zobacz [Funkcje IntelliTrace](../debugger/intellitrace-features.md).

- **Zdarzenia debugera**

  IntelliTrace zawsze zapisuje zdarzenia mające miejsce w debugerze Visual Studio. Uruchamianie aplikacji jest na przykład zdarzeniem debugera. Inne zdarzenia debugera są zatrzymywane zdarzenia, co powoduje przerwanie wykonywania aplikacji. Na przykład program trafi do punktu przerwania, trafi punkt śledzenia lub wykonuje polecenie **kroku** .

  Domyślnie, aby pomóc w wydajności, IntelliTrace nie rejestruje każdej możliwej wartości dla zdarzenia debugera. Zamiast tego zapisuje następujące wartości:

  - Wartości w oknie **zmiennych lokalnych** . Pozostaw otwarte okno **lokalne** , aby wyświetlić te wartości.

  - Wartości w oknie **samochody** tylko wtedy, gdy okno **autowypełniane** jest otwarte

  - Wartości w DataTips, które są wyświetlane, gdy ustawisz wskaźnik myszy nad zmienną w oknie źródłowym, aby zobaczyć jej wartość. IntelliTrace nie zbiera wartości w unieruchomionych DataTips.

    Gdy tryb IntelliTrace zdarzeń i migawek jest włączony, IntelliTrace będzie wykonywać migawkę procesu aplikacji w każdym **punkcie przerwania** debugera i zdarzeniu **kroku** . Spowoduje to zapisanie wartości w oknach **zmiennych lokalnych**, **autostartowych** i **czujki** , niezależnie od tego, czy okna są otwarte. Zostaną również zebrane wartości z dowolnych przypiętych porad dotyczących danych.

- **Wyjątki**

  IntelliTrace zapisuje typ wyjątku i komunikat dla tego rodzaju wyjątków:

  - Obsługiwane wyjątki, gdy wyjątek jest generowany i przechwycony

  - Nieobsługiwane wyjątki

- **Zdarzenia .NET Framework**

  IntelliTrace domyślnie zapisuje najbardziej typowe zdarzenia .NET Framework. Na przykład dla <xref:System.Windows.Forms.CheckBox.CheckedChanged?displayProperty=nameWithType> zdarzenia IntelliTrace zbiera stan pola wyboru i tekst.

- **Zdarzenia aplikacji SharePoint 2010 i SharePoint 2013**

  Można zapisać zdarzenia dotyczące profili użytkowników i zdarzenia w podzbiorze Unified Logging System (ULS) do aplikacji SharePoint 2010 i 2013 działających poza programem Visual Studio. Zdarzenia te można zapisać w pliku iTrace. Wymaga Visual Studio Enterprise 2015 lub nowszych wersji, wcześniejszej wersji Visual Studio Ultimate lub [Microsoft Monitoring Agent](https://www.microsoft.com/download/details.aspx?id=40316) działających w trybie **śledzenia** .

  Po otwarciu pliku iTrace wprowadź identyfikator korelacji programu SharePoint, aby znaleźć odpowiadające mu żądanie sieci Web, zobaczyć zarejestrowane zdarzenia i rozpocząć debugowanie od określonego zdarzenia. Jeśli plik zawiera nieobsłużone wyjątki, można wybrać identyfikator korelacji, aby uruchomić debugowanie wyjątku.

  Zobacz:

  - [Korzystanie z autonomicznego modułu zbierającego funkcji IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md)

  - [Korzystanie z zapisanych danych funkcji IntelliTrace](../debugger/using-saved-intellitrace-data.md)

  - [Przewodnik: debugowanie aplikacji SharePoint przy użyciu narzędzia IntelliTrace](../sharepoint/walkthrough-debugging-a-sharepoint-application-by-using-intellitrace.md)

**Przechwytywanie migawek**

Można skonfigurować IntelliTrace do przechwytywania migawek przy każdym punkcie przerwania i zdarzeniu debugera. IntelliTrace rejestruje pełny stan aplikacji w każdej migawce, która umożliwia wyświetlanie złożonych zmiennych i obliczanie wyrażeń.

> [!NOTE]
> Autonomiczny [moduł zbierający IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md) nie obsługuje przechwytywania migawek.

Zobacz [Sprawdzanie poprzedniego stanu aplikacji przy użyciu IntelliTrace](../debugger/view-historical-application-state.md).

**Zbierz informacje o wywołaniu funkcji**

Możesz skonfigurować IntelliTrace, aby zbierać informacje dotyczące wywołań dla funkcji. Te informacje pozwalają wyświetlać historię stosu wywołań i umożliwiają poruszanie się w wywołaniach kodu w dowolnym kierunku. W przypadku każdego wywołania funkcji IntelliTrace rejestruje następujące dane:

- Nazwa funkcji
- Wartości pierwotnych typów danych przekazywanych jako parametry w punktach wejścia do funkcji i zwracanych w punktach wyjścia z funkcji
- Wartości właściwości automatycznych, gdy są one odczytywane lub zmieniane
- Wskaźniki do pierwszego poziomu obiektów podrzędnych, ale nie ich wartości inne, niż gdyby były równe null lub nie

> [!NOTE]
> IntelliTrace zbiera tylko 256 pierwszych obiektów w tablicach i pierwszych 256 znaków w ciągach.

Zobacz [Sprawdzanie aplikacji za pomocą debugowania historycznego](../debugger/historical-debugging-inspect-app.md).

**Zbierz informacje o module**

Aby kontrolować, ile informacji na temat wywołania gromadzi IntelliTrace, określ tylko te moduły, która Cię interesują. Może to pomóc w ulepszaniu wydajności aplikacji podczas zbierania. Zapoznaj się z sekcją Sterowanie tym, [ile IntelliTrace informacji zbiera](../debugger/intellitrace-features.md#ControlCallData) w funkcjach IntelliTrace.

## <a name="will-intellitrace-slow-down-my-application"></a><a name="AffectPerformance"></a> IntelliTrace spowalnia moją aplikację?

IntelliTrace domyślnie zbiera dane tylko dla wybranych zdarzeń IntelliTrace. Może to być niespowolnienie aplikacji, w zależności od struktury i organizacji kodu. Na przykład jeśli IntelliTrace często zapisuje zdarzenie, może to spowolnić aplikację. Może być również konieczne rozważenie refaktoryzacji aplikacji.

Zbieranie informacji o wywołaniu może znacząco spowolnić aplikację. Może to również zwiększyć rozmiar wszystkich plików dziennika IntelliTrace (iTrace) zapisywanych na dysku. Aby zminimalizować te skutki, zbieraj informacji o wywołaniach tylko interesujących Cię modułów.  Aby zmienić maksymalny rozmiar plików. iTrace, przejdź do pozycji **Narzędzia**, **Opcje**, **IntelliTrace**, **Zaawansowane**.

### <a name="blogs"></a>Blogi

[DevOps firmy Microsoft](https://devblogs.microsoft.com/devops/)

### <a name="forums"></a>Fora

[Diagnostyka programu Visual Studio](https://social.msdn.microsoft.com/Forums/en-US/home)