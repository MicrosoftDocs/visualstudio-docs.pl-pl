---
title: 'Przewodnik: Profilowanie wiersza polecenia przy użyciu próbkowania | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, walkthroughs
- performance tools, walkthroughs
- performance tools, command-line tools
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 09272c8cf2dff02d3be024b9c3eeab8b51f56df7
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74777975"
---
# <a name="walkthrough-command-line-profiling-using-sampling"></a>Przewodnik: Profilowanie wiersza polecenia przy użyciu próbkowania

W tym instruktażu pokazano, jak profilować aplikację przy użyciu narzędzi wiersza polecenia i próbkowania w celu identyfikowania problemów z wydajnością.

W tym instruktażu krok po kroku proces profilowania aplikacji zarządzanej przy użyciu narzędzi wiersza polecenia jest używany do wyodrębniania i identyfikowania problemów z wydajnością w aplikacji.

W tym instruktażu wykonasz następujące czynności:

- Profilowanie aplikacji przy użyciu narzędzi wiersza polecenia i próbkowania.
- Analizuj przykładowe wyniki profilowania, aby zlokalizować i rozwiązać problemy z wydajnością.

## <a name="prerequisites"></a>Wymagania wstępne

- Pośrednia interpretacja [!INCLUDE[csharp_current_short](../misc/includes/csharp_current_short_md.md)]
- Pośrednia znajomość pracy z narzędziami wiersza polecenia
- Kopia [przykładu PeopleTrax —](performance-explorer.md)
- Aby można było korzystać z informacji dostarczonych przez profilowanie, najlepszym rozwiązaniem jest udostępnienie informacji o symbolach debugowania.

## <a name="command-line-profiling-using-the-sampling-method"></a>Profilowanie wiersza polecenia przy użyciu metody próbkowania

Próbkowanie to metoda profilowania, za pomocą której konkretny proces jest okresowo sondowany, aby określić aktywną funkcję. Dane wynikowe zawierają liczbę, jak często funkcja była w szczycie stosu wywołań, gdy proces został próbkowany.

> [!NOTE]
> Aby uzyskać ścieżkę do narzędzi profilowania, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na komputerach 64-bitowych są dostępne zarówno 64-bitowe, jak i 32-bitowe wersje narzędzi. Aby użyć narzędzi wiersza polecenia profilera, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH okna wiersza polecenia lub dodać do samego polecenia.

### <a name="to-profile-the-peopletrax-application-by-using-the-sampling-method"></a>Aby profilować aplikację PeopleTrax — za pomocą metody próbkowania

1. Zainstaluj przykładową aplikację PeopleTrax — i skompiluj wydaną wersję aplikacji.

2. Otwórz okno wiersza polecenia i Dodaj katalog narzędzia profilowania do zmiennej środowiskowej ścieżka lokalna.

3. Zmień katalog roboczy na katalog zawierający pliki binarne PeopleTrax —.

4. Wpisz następujące polecenie, aby ustawić odpowiednie zmienne środowiskowe:

    ```cmd
    VSPerfCLREnv /sampleon
    ```

5. Uruchom profilowanie, uruchamiając program *VSPerfCmd. exe*, który jest narzędziem wiersza polecenia, które kontroluje Profiler. Następujące polecenie uruchamia aplikację i Profiler w trybie próbkowania:

    ```cmd
    VsPerfCmd /start:sample /output:PeopleTraxReport.vsp /launch:PeopleTrax.exe
    ```

     Proces profilera zostanie uruchomiony i dołączy do procesu *PeopleTrax —. exe* . Proces profilera rozpocznie pisanie zebranych danych profilowania do pliku raportu.

6. Kliknij pozycję **Pobierz osoby**.

7. Kliknij pozycję **ExportData**.

     Zostanie otwarty Notatnik i zostanie wyświetlony nowy plik zawierający wyeksportowane dane z **PeopleTrax —** .

8. Zamknij Notatnik, a następnie zamknij aplikację **PeopleTrax —** .

9. Zamknij program profilujący. Wpisz następujące polecenie:

    ```cmd
    VSPerfCmd /shutdown
    ```

10. Użyj następującego polecenia, aby zresetować zmienne środowiskowe:

    ```cmd
    VSPerfCLREnv /sampleoff
    ```

11. Dane profilowania są przechowywane w. plik *VSP* analizuje wyniki przy użyciu jednej z następujących metod:

    - Otwórz okno. plik *VSP* w środowisku IDE programu Visual Studio.

         oraz

    - Generuj wartość rozdzieloną przecinkami (. *CSV*) za pomocą narzędzia wiersza polecenia *VSPerfReport. exe*. Aby generować raporty do użycia poza [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE, użyj następującego polecenia:

        ```cmd
        VSPerfReport <dir> PeopleTraxReport.vsp /output:<dir> /summary:all
        ```

## <a name="see-also"></a>Zobacz także

[Omówienie sesji wydajności](../profiling/performance-session-overview.md)
[profilu z wiersza polecenia](../profiling/using-the-profiling-tools-from-the-command-line.md)
[VSPerfCmd](../profiling/vsperfcmd.md)
[poznać wartości danych próbkowania](../profiling/understanding-sampling-data-values.md)
[widoki raportu wydajności](../profiling/performance-report-views.md)
