---
title: Strona startowa dla rozszerzenia Snapshot Debugger
ms.date: 07/14/2018
robots: noindex, nofollow
ms.topic: reference
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cf2aba33089623dc98a90c23166291bb2d6e7123
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62905275"
---
# <a name="getting-started-with-the-snapshot-debugger"></a>Rozpoczęcie korzystania z rozszerzenia Snapshot Debugger

Visual Studio Snapshot Debugger jest teraz połączona z usługą i rozpocząć zbieranie migawek, aby pomóc w debugowaniu.

Aby użyć rozszerzenia Snapshot Debugger, ustaw niektóre punkty przyciągania w kodzie, kliknij przycisk, aby rozpocząć zbieranie migawek, a następnie uruchom danego scenariusza. Gdy kod działa, w którym ustawiono punkt przyciągania, aplikacji migawki. Następnie Otwórz migawkę, klikając ją w programie Visual Studio w oknie narzędzia diagnostyczne. Można teraz debugować migawki z poziomu usługi, tak samo, jak był lokalny. Aby uzyskać szczegółowe instrukcje Zachowaj odczytu.

## <a name="collect-and-view-snapshots"></a>Zbierane i wyświetlane są migawki

Rozszerzenie Snapshot Debugger zbiera migawki z aplikacji. Migawki są takie jak obrazy z aplikację w punkcie w czasie. Visual Studio możesz wskazać, kiedy i gdzie zbiera dane migawki przez ustawienie punktu przyciągania w kodzie. Punkt przyciągania określasz wszelkie warunki, które należy upewnić się, że możesz uzyskać problemu dotyczącego analizujesz migawkę.

### <a name="set-a-snappoint"></a>Ustaw punkt przyciągania

1. W edytorze kodu kliknij lewym marginesie na oprawę obok wiersza kodu, który Cię interesuje można ustawić punktu przyciągania. Upewnij się, że kod, który będzie uruchamiany.

    ![Ustawianie punktu przyciągania w edytorze](../media/snapshot-startpage-set-snappoint.png)

    Purpurowa sześciokąt pojawia się, gdy klikniesz po lewej stronie.

2. Kliknij przycisk **Rozpocznij zbieranie** włączenie punktu przyciągania.

### <a name="open-a-snapshot"></a>Otwórz migawkę

1. Po osiągnięciu punktu przyciągania migawki pojawia się w oknie narzędzia diagnostyczne po prawej stronie. Jeśli nie zostanie otwarte okno, możesz go otworzyć, wybierając **debugowania** > **Windows** > **Pokaż narzędzia diagnostyczne**.

    ![Migawka w oknie narzędzia diagnostyczne](../media/snapshot-startpage-diagsession-window.png)

2. Kliknij dwukrotnie migawkę, aby go otworzyć.

### <a name="inspect-snapshot-data"></a>Sprawdź dane migawki

Z poziomu tego widoku możesz umieścić kursor zmienne, aby wyświetlić DataTips, użyj zmienne lokalne, czujki i wywoływać stosu systemu windows, a także ocenę wyrażenia.

Nadal działa z witryną i nie ma to wpływ na użytkowników końcowych. Domyślnie tylko jedna migawka jest przechwytywany na punktu przyciągania. Oznacza to, że po przechwyceniu migawkę punktu przyciągania wyłącza. Chcesz przechwytywać innego migawkę punktu przyciągania, można włączyć punkt przyciągania ponownie, klikając **Aktualizuj kolekcję**.

### <a name="set-a-logpoint"></a>Ustaw punkt rejestrowania

1. Kliknij prawym przyciskiem myszy ikonę punkt przyciągania (sześciokąt purpurowy), a następnie wybierz **ustawienia**.

2. W **ustawienia punktu przyciągania** wybierz **akcje**.

    ![Warunki punkt przyciągania](../media/snapshot-startpage-logpoint.png)

3. W **komunikat** wprowadź komunikat dziennika, które mają być rejestrowane. Można również obliczyć zmiennych w wiadomości dziennika, umieszczając je wewnątrz nawiasów klamrowych.

    Jeśli wybierzesz **Wyślij do okna danych wyjściowych**, komunikat zostanie wyświetlony w oknie narzędzia diagnostyczne, gdy zostanie osiągnięty punkt rejestrowania.

    Jeśli wybierzesz **Wyślij do dziennika aplikacji**, komunikat pojawi się gdziekolwiek zobaczyć komunikaty z `System.Diagnostics.Trace` (lub `ILogger` platformie .NET Core), takich jak usługi App Insights, gdy zostanie osiągnięty punkt rejestrowania.

## <a name="learn-more"></a>Dowiedz się więcej

Więcej informacji na temat rozszerzenia Snapshot Debugger można znaleźć na [strony witryny docs](../debug-live-azure-applications.md). Dowiedz się więcej na temat ustawiania warunki, aby ułatwić znajdowanie usterek.

## <a name="dont-show-me-this-again"></a>Nie "pokazuj mi tego ponownie

Aby nigdy nie pokazuj strony początkowej debugera migawki podczas łączenia z rozszerzenia Snapshot Debugger, należy zmienić **strony "Wprowadzenie" Pokaż w menu start sesji** opcji **narzędzia**  >   **Opcje** > **Snapshot Debugger**.

![Strony opcji narzędzi debugera migawki](../media/snapshot-startpage-tools-options.png)
