---
title: Liczniki procesorów i systemu Windows | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.property.counters
helpviewer_keywords:
- Windows counters in Profiling Tools
- CPU counters in Profiling Tools
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 9accd3d0ab5ff1f7a3084d5973cace08e66396b9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779553"
---
# <a name="cpu-and-windows-counters"></a>Liczniki procesora CPU i systemu Windows

Profiler programu Visual Studio umożliwia zbieranie danych dotyczących wydajności, które zostały wygenerowane przez system operacyjny (liczniki systemu Windows) i dane dotyczące wydajności, które zostały wygenerowane przez jednostkę procesora (liczniki procesora).

> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemach Windows 8 i Windows Server 2012 wymagały znaczących zmian w sposobie, w jaki profiler programu Visual Studio zbiera dane na tych platformach. Aplikacje platformy uniwersalnej systemu Windows wymagają również nowych technik zbierania. Zobacz [Narzędzia wydajności w aplikacjach dla systemów Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="windows-counters"></a>Liczniki systemu Windows

Liczniki systemu Windows są częścią infrastruktury diagnostycznej systemu Windows, która zawiera informacje o wydajności systemu operacyjnego lub aplikacji, usługi lub sterownika. Liczniki systemu Windows zależą od konfiguracji bieżącego komputera i mogą nie być dostępne na innych komputerach. Liczniki wydajności systemu Windows są zbierane w profilowaniu plików danych jako znaczniki profilowania, które następnie mogą być używane do filtrowania widoków i raportów.

## <a name="cpu-counters"></a>Liczniki procesorów

Liczniki procesora CPU są funkcją procesora cpu komputera, które przechowują liczbę zdarzeń związanych ze sprzętem. Podczas zbierania danych licznika procesora CPU przy użyciu metody profilowania instrumentacji, dane są dołączane do danych dla funkcji i modułów. Można zebrać wiele liczników procesora CPU przy użyciu metody instrumentacji. Korzystając z metody próbkowania, należy wybrać jeden licznik do użycia jako zdarzenie, które ma być próbkowana.

Liczniki wydajności są specyficzne dla procesora CPU. Różne modele i wersje procesora CPU mogą mieć znacznie różne ustawienia konfiguracji, aby włączyć ten sam licznik wydajności. [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]Profileer zdarzenia przenośne oddzielić niektóre typowe liczniki wydajności z określonych procesorów i umożliwiają zbieranie lub próbkowanie zdarzeń wydajności ogólnej.

Jeśli chcesz policzyć określone zdarzenie podczas korzystania z profilera, na przykład chybienia pamięci podręcznej L2, możesz utworzyć sesję wydajności wokół tego nadawcy zdarzenia. Można to zrobić na dowolnym procesorze z pamięcią podręczną L2. Sesję wydajności można przenieść z platformy na platformę bez modyfikacji.

Profiler programu Visual Studio nadal obsługuje określone zdarzenia dla określonej platformy. Na przykład deweloper na platformie Pentium 4 może chcieć zliczać zdarzenia, które są specyficzne dla architektury NetBurst. To zdarzenie nie jest przenośne, ale nadal dostępne dla dewelopera dla określonej sesji wydajności na określonej platformie.

## <a name="portable-and-platform-events"></a>Zdarzenia przenośne i platformowe

Zdarzenia przenośne to grupa liczników procesora CPU, które nie są specyficzne dla określonego procesora. Wszystkie inne liczniki procesora CPU są nazywane zdarzeniami platformy i mogą nie być obsługiwane na różnych platformach.

 Liczniki dla zdarzeń przenośnych i platformowych są zdefiniowane w pliku . *pliki xml,* gdzie są dostarczane określone wartości związane z licznikami. Istnieje wiele plików dla różnych procesorów, ponieważ dane dla procesorów Intel i AMD, na przykład, są różne. Profiler [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)] używa tych informacji do przedstawienia użytkownika odpowiednich liczników, zarówno przenośnych, jak i platformowych, do pomiaru wydajności.

### <a name="portable-events"></a>Zdarzenia przenośne

Zdarzenia przenośne zawierają następujące zdarzenia:

**Zdarzenia ogólne**

|Nazwa wydarzenia|Opis zdarzenia|
|----------------|-----------------------|
|Instrukcje wycofane|Wskazuje liczbę instrukcji wykonywanych do czasu zakończenia zdarzenia.|
|Cykle niezatrzymowane|Wskazuje tylko te cykle, w których procesor nie jest zatrzymany, na przykład oczekiwanie na we/wy.|

**Wydarzenia frontowe**

|Nazwa wydarzenia|Opis zdarzenia|
|----------------|-----------------------|
|Itlb Chybienia|Wskazuje liczbę odnośnych odnośnych odnośnych odnośów buforu tłumaczenia instrukcji, które spowodowały pominięcie.|

**Zdarzenia w oddziale**

|Nazwa wydarzenia|Opis zdarzenia|
|----------------|-----------------------|
|Oddziały wycofane|Wskazuje liczbę instrukcji gałęzi wykonywanych do czasu zakończenia zdarzenia.|
|Źle przewidywane gałęzie|Wskazuje błędnie przewidywane gałęzie, które występują, ponieważ procesor przewidział niepoprawną ścieżkę. Błędnie przewidywane gałęzie wpływają na wydajność, ponieważ procesor musi odrzucić całą wykonaną pracę i uruchomić ponownie na poprawnej ścieżce.|

**Zdarzenia pamięci:**

|Nazwa wydarzenia|Opis zdarzenia|
|----------------|-----------------------|
|L2 Pamięć podręczna Odczyt Chybień|Wskazuje liczbę chybień odczytu pamięci podręcznej drugiego poziomu.|
|Odwołania do odczytu pamięci podręcznej L2|Wskazuje liczbę odwołań do odczytu pamięci podręcznej drugiego poziomu. Zawiera chybienia obciążenia i odczytywania dla własności (RFO) chybień i trafień.|

## <a name="view-available-counters"></a>Wyświetlanie dostępnych liczników

W oknie wiersza polecenia można wyświetlić listę dostępnych liczników procesora CPU w programie Visual Studio IDE.

### <a name="visual-studio-ui"></a>Interfejs użytkownika programu Visual Studio

Aby wyświetlić listę dostępnych liczników na komputerze w programie Visual Studio IDE, musisz mieć otwartą sesję wydajności profilera w Eksploratorze wydajności.

#### <a name="to-view-a-list-of-a-list-of-all-cpu-counters-that-are-supported-on-the-current-platform"></a>Aby wyświetlić listę wszystkich liczników procesora CPU obsługiwanych na bieżącej platformie

1. W Eksploratorze wydajności kliknij prawym przyciskiem myszy sesję wydajności, a następnie kliknij polecenie **Właściwości**.

2. Wykonaj jedną z następujących czynności:

   - Kliknij **pozycję Próbkowanie**, a następnie wybierz **pozycję Licznik wydajności** z listy Zdarzenia **przykładowe.** Liczniki procesora cpu są wymienione w **liczniki wydajności Dostępne**.

      **Uwaga** Kliknij **przycisk Anuluj,** aby powrócić do poprzedniej konfiguracji próbkowania.

     — lub —

   - Wybierz **pozycję Liczniki procesora ,** a następnie wybierz pozycję **Zbieraj liczniki procesora**. Liczniki procesora cpu są wymienione w **dostępne liczniki**.

      **Uwaga** Kliknij **przycisk Anuluj,** aby powrócić do poprzedniej konfiguracji kolekcji liczników.

#### <a name="to-view-a-list-of-a-list-of-window-counters-that-are-supported-on-the-current-platform"></a>Aby wyświetlić listę liczników okna obsługiwanych na bieżącej platformie

1. W Eksploratorze wydajności kliknij prawym przyciskiem myszy sesję wydajności, a następnie kliknij polecenie **Właściwości**.

2. Kliknij pozycję **Liczniki systemu Windows**.

3. Wybierz **pozycję Zbieraj liczniki systemu Windows**.

4. Z listy **Kategoria licznika** wybierz grupę liczników. Licznik systemu Windows dla grupy jest wyświetlany w polu listy.

     **Uwaga:** Kliknij **przycisk Anuluj,** aby powrócić do poprzedniej konfiguracji kolekcji liczników.

### <a name="command-line"></a>Wiersz polecenia

Za pomocą narzędzia wiersza polecenia [VSPerfCmd](../profiling/vsperfcmd.md) można wyświetlić listę liczników procesora CPU dostępnych na komputerze z wiersza polecenia.

#### <a name="to-list-of-cpu-counters-that-are-supported-on-the-current-platform"></a>Aby wyświetlić listę liczników procesora CPU obsługiwanych na bieżącej platformie

1. Otwórz okno wiersza polecenia.

2. Typ

     **\<Katalog narzędzi wydajności programu Visual Studio>\VSPerfCmd /querycounters**

     gdzie * \<>katalogu narzędzi wydajności programu Visual Studio* jest ścieżką do katalogu Narzędzi wydajności instalacji programu Visual Studio. Aby uzyskać ścieżkę do narzędzi wydajności, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).

## <a name="see-also"></a>Zobacz też

[Przeglądy](../profiling/overviews-performance-tools.md)
[Jak: Wybierz zdarzenia](../profiling/how-to-choose-sampling-events.md)
próbkowania[Jak: Zbieranie danych](../profiling/how-to-collect-cpu-counter-data.md)
licznika procesora[Jak: Zbieranie danych licznika systemu Windows](../profiling/how-to-collect-windows-counter-data.md)
