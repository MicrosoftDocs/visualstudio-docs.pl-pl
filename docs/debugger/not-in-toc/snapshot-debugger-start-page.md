---
title: Strona początkowa dla Snapshot Debugger
ms.date: 07/14/2018
robots: noindex, nofollow
ms.topic: reference
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9f237f121d0bd0a5eaa57cd2b198024d22951622
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99941999"
---
# <a name="getting-started-with-the-snapshot-debugger"></a>Wprowadzenie z Snapshot Debugger

Visual Studio Snapshot Debugger jest teraz połączona z usługą i możesz rozpocząć zbieranie migawek, aby pomóc w debugowaniu.

Aby użyć Snapshot Debugger, ustaw punkty przyciągania w kodzie, kliknij przycisk, aby rozpocząć zbieranie migawek, a następnie Uruchom swój scenariusz. Po uruchomieniu kodu, w którym ustawiono punkt przyciągania, tworzona jest migawka aplikacji. Następnie otwórz migawkę, klikając ją w programie Visual Studio w oknie narzędzia diagnostyczne. Teraz można debugować migawkę z usługi tak, jakby była lokalna. Szczegółowe instrukcje znajdują się w temacie.

## <a name="collect-and-view-snapshots"></a>Zbieranie i wyświetlanie migawek

Snapshot Debugger zbiera migawki z aplikacji. Migawki przypominają obrazy appication w danym momencie. Poinformuj program Visual Studio, kiedy i gdzie należy zebrać migawkę, ustawiając punkt przyciągania w kodzie. W punkt przyciągania ustawia się dowolne warunki, które należy wykonać, aby uzyskać migawkę badanego problemu.

### <a name="set-a-snappoint"></a>Ustaw punkt przyciągania

1. W edytorze kodu kliknij lewy margines obok wiersza kodu, który Cię interesują, aby ustawić punkt przyciągania. Upewnij się, że jest to kod, który wiesz, że zostanie uruchomiony.

    ![Ustawianie elementu punkt przyciągania w edytorze](../media/snapshot-startpage-set-snappoint.png)

    Purpurowy sześciokąt pojawia się, gdy klikniesz po lewej stronie.

2. Kliknij pozycję **Rozpocznij zbieranie** , aby włączyć punkt przyciągania.

### <a name="open-a-snapshot"></a>Otwórz migawkę

1. Po trafieniu punkt przyciągania zostanie wyświetlona migawka w oknie narzędzia diagnostyczne po prawej stronie. Jeśli okno nie jest otwarte, można je otworzyć, wybierając pozycję **Debuguj**  >  **okna**  >  **Pokaż narzędzia diagnostyczne**.

    ![Migawka w oknie narzędzia diagnostyczne](../media/snapshot-startpage-diagsession-window.png)

2. Kliknij dwukrotnie migawkę, aby ją otworzyć.

### <a name="inspect-snapshot-data"></a>Sprawdzanie danych migawek

Z tego widoku można przesuwać się nad zmiennymi, aby wyświetlać etykietki danych, korzystać z okien zmiennych lokalnych, zegarki i stosu wywołań, a także szacować wyrażenia.

Sama witryna sieci Web jest nadal na żywo, a użytkownicy końcowi nie mają na nie wpływu. Domyślnie tylko jedna migawka jest przechwytywana na punkt przyciągania. Oznacza to, że po przechwyceniu migawki punkt przyciągania wyłącza. Jeśli chcesz przechwycić kolejną migawkę w punkt przyciągania, możesz włączyć punkt przyciągania ponownie, klikając polecenie **Aktualizuj kolekcję**.

### <a name="set-a-logpoint"></a>Ustaw punkt rejestrowania

1. Kliknij prawym przyciskiem myszy ikonę punkt przyciągania (purpurowy sześciokąt), a następnie wybierz pozycję **Ustawienia**.

2. W oknie **Ustawienia punkt przyciągania** wybierz pozycję **Akcje**.

    ![Warunki punkt przyciągania](../media/snapshot-startpage-logpoint.png)

3. W polu **komunikat** wprowadź komunikat dziennika, który chcesz zarejestrować. Możesz również obliczyć zmienne w komunikacie dziennika, umieszczając je w nawiasach klamrowych.

    Jeśli wybierzesz pozycję **Wyślij do okno dane wyjściowe**, komunikat pojawi się w oknie narzędzia diagnostyczne po trafieniu punkt rejestrowania.

    Jeśli wybierzesz pozycję **Wyślij do dziennika aplikacji**, komunikat pojawi się w dowolnym miejscu, w którym można zobaczyć komunikaty z `System.Diagnostics.Trace` (lub `ILogger` w programie .NET Core), takie jak Application Insights, po trafieniu punkt rejestrowania.

## <a name="learn-more"></a>Dowiedz się więcej

Więcej informacji na temat Snapshot Debugger można znaleźć na [stronie docs](../debug-live-azure-applications.md). Dowiedz się więcej o ustawianiu warunków, aby ułatwić znajdowanie usterek.

## <a name="dont-show-me-this-again"></a>Nie pokazuj tego ponownie

Aby nie wyświetlać ponownie Snapshot Debugger stronę początkową podczas łączenia Snapshot Debugger, należy zmienić **stronę Pokaż "wprowadzenie" w opcji Start sesji** w opcji **Narzędzia**  >    >  **Snapshot Debugger**.

![Strona opcji narzędzia Snapshot Debugger](../media/snapshot-startpage-tools-options.png)
