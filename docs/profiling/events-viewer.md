---
title: Podgląd zdarzeń | Microsoft Docs
ms.date: 4/30/2020
ms.topic: how-to
helpviewer_keywords:
- Profiler, Events Viewer
author: Sagar-S-S
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 4cba043d8300d47ae5ffba1c175a19fcfa2e65ed
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2020
ms.locfileid: "85330340"
---
# <a name="events-viewer"></a>Podgląd zdarzeń

Podgląd zdarzeń ogólnych przedstawia aktywność aplikacji za pomocą listy zdarzeń, takich jak obciążenie modułu, uruchomienie wątku i konfiguracja systemu. Ten widok pomaga lepiej zdiagnozować sposób działania aplikacji w programie Visual Studio profiler.

## <a name="setup"></a>Konfigurowanie

1. Wybierz **kombinację klawiszy Alt + F2** , aby otworzyć Profiler wydajności w programie Visual Studio.

1. Zaznacz pole wyboru **Podgląd zdarzeń** .

   ![Zaznaczone pole wyboru Podgląd zdarzeń](../profiling/media/eventsviewerselected.png "Zaznaczone pole wyboru Podgląd zdarzeń")

1. Wybierz przycisk **Start** , aby uruchomić narzędzie.

1. Po uruchomieniu narzędzia Przejdź przez scenariusz, aby profilować aplikację. Następnie wybierz pozycję **Zatrzymaj zbieranie** lub Zamknij aplikację, aby zobaczyć swoje dane.

   ![Okno pokazujące Zatrzymaj zbieranie](../profiling/media/stopcollectioneventsviewer.png "Okno pokazujące Zatrzymaj zbieranie")

Aby uzyskać więcej informacji na temat zwiększania wydajności narzędzia, zobacz [Optymalizacja ustawień profilowania](../profiling/optimize-profiler-settings.md).

## <a name="understand-your-data"></a>Zrozumienie danych

![Ślad podglądu zdarzeń](../profiling/media/eventviewertrace.png "Ślad podglądu zdarzeń")

|Nazwa kolumny|Opis|
|----------|---------------------|
|Nazwa dostawcy|Źródło zdarzenia|
|Nazwa zdarzenia|Zdarzenie określone przez jego dostawcę|
|Tekst|Opisy dostawcy, nazwy zdarzenia i identyfikatora zdarzenia|
|Sygnatura czasowa (MS)|Gdy zdarzenie zostało wykonane|
|Identyfikator GUID dostawcy|Identyfikator dostawcy zdarzeń|
|Identyfikator zdarzenia|Identyfikator zdarzenia|
|Identyfikator procesu|Proces, w którym wystąpiło zdarzenie (jeśli jest znane)|
|Nazwa procesu|Nazwa procesu, jeśli jest aktywnie uruchomiona|
|Identyfikator wątku|Identyfikator wątku, w którym wystąpiło zdarzenie (jeśli jest znane)|

Jeśli żadna kolumna nie jest domyślnie zaznaczona, kliknij prawym przyciskiem myszy jeden z istniejących nagłówków kolumn, a następnie wybierz kolumnę, którą chcesz dodać.

![Dodawanie kolumn do podglądu zdarzeń](../profiling/media/eventvieweraddcolumns.png "Dodawanie kolumn do podglądu zdarzeń")

Po wybraniu zdarzenia zostanie wyświetlone okno **właściwości dodatkowe** . **Wspólne właściwości** przedstawiają listę właściwości, które będą wyświetlane dla każdego zdarzenia. **Właściwości ładunku** przedstawiają właściwości specyficzne dla zdarzenia. W przypadku niektórych zdarzeń można również wyświetlać **stosy**.

![Podgląd zdarzeń przedstawiający stosy](../profiling/media/eventviewerstacks.png "Podgląd zdarzeń przedstawiający stosy")

## <a name="organize-your-data"></a>Organizuj dane

Wszystkie kolumny z wyjątkiem kolumny **tekstowej** są sortowane.

![Ślad podglądu zdarzeń](../profiling/media/eventviewertrace.png "Ślad podglądu zdarzeń")

Podgląd zdarzeń wyświetla do 20 000 zdarzeń jednocześnie. Aby skupić się na interesujących zdarzeniach, możesz filtrować Wyświetlanie zdarzeń przez wybranie filtru zdarzeń. Możesz również sprawdzić, jaki procent łącznej liczby zdarzeń wystąpiły dla każdego dostawcy. Umieść kursor nad pojedynczym filtrem zdarzeń, aby wyświetlić etykietkę narzędzia, która pokazuje:

- Nazwa zdarzenia
- Dostawca
- GUID
- Procent łącznej liczby zdarzeń
- Liczba zdarzeń

![Filtr zdarzeń podglądu zdarzeń](../profiling/media/eventviewereventfilter.png "Filtr zdarzeń podglądu zdarzeń")

Filtr dostawcy pokazuje, jaki procent łącznej liczby zdarzeń wystąpiłych dla każdego dostawcy. Umieść wskaźnik myszy na pojedynczym dostawcy, aby wyświetlić podobną etykietkę narzędzia z nazwą dostawcy, wartością procentową łącznych zdarzeń i liczbą zdarzeń.

![Filtr dostawcy podglądu zdarzeń](../profiling/media/eventviewerproviderfilter.png "Filtr dostawcy podglądu zdarzeń")
