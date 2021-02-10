---
title: Liczniki procesora i systemu Windows | Microsoft Docs
description: Liczniki procesora CPU (sprzętu) i systemu Windows zapewniają dane dotyczące wydajności. Dowiedz się, jak je przeglądać i jak zbierać dane z nich.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.property.counters
helpviewer_keywords:
- Windows counters in Profiling Tools
- CPU counters in Profiling Tools
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 3553106c9c2bea0d4d4c24b2e51b59e4fcf42722
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99956064"
---
# <a name="cpu-and-windows-counters"></a>Liczniki procesora CPU i systemu Windows

Program Visual Studio profiler umożliwia zbieranie danych wydajności wygenerowanych przez system operacyjny (liczniki systemu operacyjnego) i dane wydajności, które zostały wygenerowane przez jednostkę procesora (liczniki procesora).

> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemach Windows 8 i Windows Server 2012 wymagały znaczących zmian w sposobie, w jaki program Visual Studio profiler zbiera dane na tych platformach. Aplikacje platformy UWP wymagają również nowych technik zbierania danych. Zobacz [Narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="windows-counters"></a>Liczniki systemu Windows

Liczniki systemu Windows są częścią infrastruktury diagnostyki systemu Windows, która zawiera informacje o wydajności systemu operacyjnego lub aplikacji, usługi lub sterownika. Liczniki systemu Windows są zależne od konfiguracji bieżącego komputera i mogą nie być dostępne na innych komputerach. Liczniki wydajności systemu Windows są zbierane w profilowanych plikach danych jako znaczniki profilowania, które mogą być następnie używane do filtrowania widoków i raportów.

## <a name="cpu-counters"></a>Liczniki procesora CPU

Liczniki procesora są funkcją procesora komputera, która przechowuje liczbę zdarzeń związanych ze sprzętem. Podczas zbierania danych licznika procesora przy użyciu metody profilowania Instrumentacji dane są dołączane do danych dla funkcji i modułów. Można zbierać wiele liczników procesora CPU przy użyciu metody instrumentacji. Korzystając z metody próbkowania, należy wybrać jeden licznik, który będzie używany jako zdarzenie do próbkowania.

Liczniki wydajności są specyficzne dla procesora. Różne modele i wersje procesora mogą mieć znacznie różne ustawienia konfiguracji umożliwiające włączenie tego samego licznika wydajności. [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] Zdarzenia przenośne profilera oddzielą niektóre typowe liczniki wydajności z określonych procesorów i umożliwiają zbieranie lub próbkowanie ogólnych zdarzeń wydajności.

Jeśli chcesz zliczać konkretne zdarzenie przy użyciu profilera, na przykład Chybienia pamięci podręcznej L2, możesz utworzyć sesję wydajności dla tego nadawcy zdarzeń. Można to zrobić na dowolnym PROCESORze z pamięcią podręczną L2. Sesję wydajności można przenieść z platformy na platformę bez modyfikacji.

Program Visual Studio profiler kontynuuje obsługę określonych zdarzeń dla określonej platformy. Na przykład Deweloper na platformie Pentium 4 może chcieć obliczyć zdarzenia specyficzne dla architektury sieci. To zdarzenie nie jest przenośne, ale nadal jest dostępne dla dewelopera dla konkretnej sesji wydajności na określonej platformie.

## <a name="portable-and-platform-events"></a>Zdarzenia przenośne i platformy

Zdarzenia przenośne są grupą liczników procesora, które nie są specyficzne dla określonego procesora. Wszystkie inne liczniki procesora CPU są nazywane zdarzeniami platformy i mogą nie być obsługiwane na różnych platformach.

 Liczniki dla zdarzeń przenośnych i platform są zdefiniowane w. pliki *XML* , gdzie określone wartości, które są związane z licznikami, są dostarczane. Istnieje wiele plików dla różnych procesorów CPU, ponieważ dane dla procesorów Intel i AMD, na przykład są różne. [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)]Profiler używa tych informacji, aby przedstawić odpowiednie liczniki, zarówno przenośne, jak i platformy, do użytkownika w celu pomiaru wydajności.

### <a name="portable-events"></a>Zdarzenia przenośne

Zdarzenia przenośne zawierają następujące zdarzenia:

**Zdarzenia ogólne**

|Nazwa zdarzenia|Opis zdarzenia|
|----------------|-----------------------|
|Wycofane instrukcje|Wskazuje liczbę instrukcji, które są wykonywane do momentu ukończenia zdarzenia.|
|Cykle niezatrzymane|Wskazuje tylko te cykle, w których procesor nie jest zatrzymany, na przykład w przypadku oczekiwania na we/wy.|

**Zdarzenia frontonu**

|Nazwa zdarzenia|Opis zdarzenia|
|----------------|-----------------------|
|Chybienia ITLB|Wskazuje liczbę przeszukiwanych buforów przeszukiwanych w tłumaczeniach instrukcji, które spowodowały brak.|

**Zdarzenia gałęzi**

|Nazwa zdarzenia|Opis zdarzenia|
|----------------|-----------------------|
|Wycofane gałęzie|Wskazuje liczbę instrukcji gałęzi wykonywanych do momentu ukończenia zdarzenia.|
|Nieprzewidywalne gałęzie|Wskazuje źle przewidywalną gałąź, która występuje, ponieważ procesor przewidział niepoprawną ścieżkę. Nieprawidłowo przewidywane gałęzie mają wpływ na wydajność, ponieważ procesor musi odrzucić wszystkie wykonane zadania i ponownie uruchomić w poprawnej ścieżce.|

**Zdarzenia pamięci:**

|Nazwa zdarzenia|Opis zdarzenia|
|----------------|-----------------------|
|Chybienia odczytu pamięci podręcznej L2|Wskazuje liczbę chybień odczytu pamięci podręcznej drugiego poziomu.|
|Odwołania odczytu pamięci podręcznej L2|Wskazuje liczbę odwołań do odczytu pamięci podręcznej drugiego poziomu. Obejmuje to chybień i odczyty dla chybień (RFO) i trafień.|

## <a name="view-available-counters"></a>Wyświetl dostępne liczniki

Dostępne liczniki procesora można wyświetlić w środowisku IDE programu Visual Studio, w oknie wiersza polecenia.

### <a name="visual-studio-ui"></a>Interfejs użytkownika programu Visual Studio

Aby wyświetlić listę dostępnych liczników na komputerze w środowisku IDE programu Visual Studio, należy otworzyć sesję wydajności profilera w Eksplorator wydajności.

#### <a name="to-view-a-list-of-a-list-of-all-cpu-counters-that-are-supported-on-the-current-platform"></a>Aby wyświetlić listę wszystkich liczników procesora CPU, które są obsługiwane przez bieżącą platformę

1. W Eksplorator wydajności kliknij prawym przyciskiem myszy sesję wydajności, a następnie kliknij polecenie **Właściwości**.

2. Wykonaj jedną z następujących czynności:

   - Kliknij pozycję **próbkowanie**, a następnie wybierz pozycję **licznik wydajności** z listy zdarzeń **przykładowych** . Liczniki procesora CPU są wymienione w **dostępnych licznikach wydajności**.

      **Uwaga** Kliknij przycisk **Anuluj** , aby powrócić do poprzedniej konfiguracji próbkowania.

     -lub-

   - Wybierz pozycję **liczniki procesora**, a następnie wybierz pozycję **Zbierz liczniki procesora CPU**. Liczniki procesora CPU są wymienione w **dostępnych licznikach**.

      **Uwaga** Kliknij przycisk **Anuluj** , aby powrócić do poprzedniej konfiguracji kolekcji liczników.

#### <a name="to-view-a-list-of-a-list-of-window-counters-that-are-supported-on-the-current-platform"></a>Aby wyświetlić listę liczników okna, które są obsługiwane przez bieżącą platformę

1. W Eksplorator wydajności kliknij prawym przyciskiem myszy sesję wydajności, a następnie kliknij polecenie **Właściwości**.

2. Kliknij pozycję **liczniki systemu Windows**.

3. Wybierz pozycję **Zbierz liczniki systemu Windows**.

4. Z listy **Kategoria licznika** wybierz grupę liczników. W polu listy zostanie wyświetlony licznik systemu Windows dla grupy.

     **Uwaga:** Kliknij przycisk **Anuluj** , aby powrócić do poprzedniej konfiguracji kolekcji liczników.

### <a name="command-line"></a>Wiersz polecenia

Za pomocą narzędzia wiersza polecenia [VSPerfCmd](../profiling/vsperfcmd.md) można wyświetlić listę liczników procesora, które są dostępne na komputerze z wiersza polecenia.

#### <a name="to-list-of-cpu-counters-that-are-supported-on-the-current-platform"></a>Aby wyświetlić listę liczników procesora, które są obsługiwane przez bieżącą platformę

1. Otwórz okno wiersza polecenia.

2. Typ

     **\<Visual Studio Performance Tools Directory>\VSPerfCmd/QueryCounters**

     gdzie *\<Visual Studio Performance Tools Directory>* jest ścieżką do katalogu narzędzi wydajności instalacji programu Visual Studio. Aby uzyskać ścieżkę do narzędzi wydajności, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).

## <a name="see-also"></a>Zobacz też

- [Omówienia](../profiling/overviews-performance-tools.md)
- [Instrukcje: Wybieranie zdarzeń próbkowania](../profiling/how-to-choose-sampling-events.md)
- [Instrukcje: zbieranie danych licznika procesora CPU](../profiling/how-to-collect-cpu-counter-data.md)
- [Instrukcje: zbieranie danych licznika systemu Windows](../profiling/how-to-collect-windows-counter-data.md)
