---
title: 'Przewodnik: Profilowanie wiersza polecenia przy użyciu metody próbkowania | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, walkthroughs
- performance tools, walkthroughs
- performance tools, command-line tools
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8dbb5daff9db064cedcfaa6713f5c31a72f961af
ms.sourcegitcommit: 34840a954ed3446c789e80ee87da6cbf1203cbb5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/18/2018
ms.locfileid: "53592433"
---
# <a name="walkthrough-command-line-profiling-using-sampling"></a>Przewodnik: Wiersza polecenia, profilowania przy użyciu metody próbkowania

W tym instruktażu przedstawiono sposób profilować aplikację przy użyciu narzędzia wiersza polecenia i pobierania próbek, aby zidentyfikować problemy z wydajnością.

W tym instruktażu będą kroków procesu profilowania aplikacji zarządzanej za pomocą narzędzia wiersza polecenia i użyj próbkowania, aby izolować i zidentyfikować problemy z wydajnością w aplikacji.

W tym instruktażu będą wykonaj następujące kroki:

- Profil aplikacji przy użyciu narzędzia wiersza polecenia i pobierania próbek.
- Analizuj próbkowanych wyniki profilowania, aby zlokalizować i rozwiązać problemy z wydajnością.

## <a name="prerequisites"></a>Wymagania wstępne

- Pośredni wiedzę na temat [!INCLUDE[csharp_current_short](../misc/includes/csharp_current_short_md.md)]
- Pośredni, informacje o pracy z narzędzi wiersza polecenia
- Kopię [peopletrax — przykład](../profiling/peopletrax-sample-profiling-tools.md)
- Aby pracować z danymi dostarczonych przez profilowanie, najlepiej jest mieć debugowania dostępnych informacji o symbolach.

## <a name="command-line-profiling-using-the-sampling-method"></a>Profilowanie wiersza polecenia przy użyciu metody próbkowania

Próbkowanie jest metodą profilowania za pomocą którego proces okresowo wysyłane do określenia funkcji active. Dane wynikowe zapewnia liczenie częstotliwość funkcja znajdowała się na szczycie stosu wywołań proces był wtedy próbkowany.

> [!NOTE]
>  Aby uzyskać ścieżkę do narzędzi profilowania, zobacz [Określ ścieżkę do narzędzia wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na komputerach 64-bitowym 64-bitowe i 32-bitowe wersje narzędzia są dostępne. Aby użyć narzędzi profilowania z wiersza polecenia, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH okna wiersza polecenia lub dodać do niej samo polecenie.  

### <a name="to-profile-the-peopletrax-application-by-using-the-sampling-method"></a>Aplikacja ma być profilowana peopletrax — przy użyciu metody próbkowania

1. Przykładowa aplikacja peopletrax — Instalowanie i tworzenie wersji aplikacji.

2. Otwórz okno wiersza polecenia i Dodaj katalog Profiling Tools do lokalnej zmiennej środowiskowej Path.

3. Zmień katalog roboczy na katalog, który zawiera pliki binarne peopletrax —.

4. Wpisz następujące polecenie, aby ustawić odpowiednie zmienne środowiskowe:

    ```cmd
    VSPerfCLREnv /sampleon
    ```

5. Uruchom profilowanie, uruchamiając *VSPerfCmd.exe*, czyli narzędzie wiersza polecenia, który kontroluje profilera. Następujące polecenie uruchamia aplikację i profiler w trybie próbkowania:

    ```cmd
    VsPerfCmd /start:sample /output:PeopleTraxReport.vsp /launch:PeopleTrax.exe
    ```

     Rozpoczyna się proces profilera i dołącza do *PeopleTrax.exe* procesu. Uruchamia proces profiler do zapisywania zebranych danych profilowania do pliku raportu.

6. Kliknij przycisk **Pobierz osoby**.

7. Kliknij przycisk **ExportData**.

     Notatnik otwiera i wyświetla nowy plik, który zawiera wyeksportowane dane z **peopletrax —**.

8. Zamknij Notatnik, a następnie Zamknij **peopletrax —** aplikacji.

9. Zamknij program profilujący. Wpisz następujące polecenie:

    ```cmd
    VSPerfCmd /shutdown
    ```

10. Użyj następującego polecenia, aby zresetować zmienne środowiskowe:

    ```cmd
    VSPerfCLREnv /sampleoff
    ```

11. Profilowanie danych są przechowywane w. *vsp* pliku Analizuj wyniki za pomocą jednego z następujących metod:

    - Otwórz. *vsp* pliku w programie Visual Studio IDE.

         — lub —

    - Generowanie wartości rozdzielanych przecinkami (. *CSV*) za pomocą narzędzia wiersza polecenia *VSPerfReport.exe*. Do generowania raportów dla użycia poza [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE, użyj następującego polecenia:

        ```cmd
        VSPerfReport <dir> PeopleTraxReport.vsp /output:<dir> /summary:all
        ```

## <a name="see-also"></a>Zobacz także

[Sesja wydajności — omówienie](../profiling/performance-session-overview.md)  
[Profilowanie z wiersza polecenia](../profiling/using-the-profiling-tools-from-the-command-line.md)  
[VSPerfCmd](../profiling/vsperfcmd.md)  
[Informacje z wartościami danych próbkowania](../profiling/understanding-sampling-data-values.md)  
[Widoki raportu wydajności](../profiling/performance-report-views.md)