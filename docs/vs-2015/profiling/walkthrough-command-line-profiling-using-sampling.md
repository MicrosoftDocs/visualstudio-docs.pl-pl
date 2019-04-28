---
title: 'Przewodnik: Profilowanie wiersza polecenia przy użyciu metody próbkowania | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, walkthroughs
- performance tools, walkthroughs
- performance tools, command-line tools
ms.assetid: 1d53972f-6f35-4842-8c74-1b627f18c70a
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 96dfe49ce4e174680202cd60c3e8bca83cfbf575
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63439681"
---
# <a name="walkthrough-command-line-profiling-using-sampling"></a>Przewodnik: Wiersza polecenia, profilowania przy użyciu metody próbkowania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym instruktażu przedstawiono sposób profilować aplikację przy użyciu narzędzia wiersza polecenia i pobierania próbek, aby zidentyfikować problemy z wydajnością.  
  
 W tym instruktażu będą kroków procesu profilowania aplikacji zarządzanej za pomocą narzędzia wiersza polecenia i użyj próbkowania, aby izolować i zidentyfikować problemy z wydajnością w aplikacji.  
  
 W tym instruktażu będą wykonaj następujące kroki:  
  
- Profil aplikacji przy użyciu narzędzia wiersza polecenia i pobierania próbek.  
  
- Analizuj próbkowanych wyniki profilowania, aby zlokalizować i rozwiązać problemy z wydajnością.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
  
- [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], lub [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
- Pośredni wiedzę na temat [!INCLUDE[csharp_current_short](../includes/csharp-current-short-md.md)]  
  
- Pośredni, informacje o pracy z narzędzi wiersza polecenia  
  
- Kopię [peopletrax — przykład](../profiling/peopletrax-sample-profiling-tools.md)  
  
- Aby pracować z danymi dostarczonych przez profilowanie, najlepiej jest mieć debugowania dostępnych informacji o symbolach.  
  
## <a name="command-line-profiling-using-the-sampling-method"></a>Polecenie wiersza profilowania przy użyciu metody próbkowania  
 Próbkowanie jest metodą profilowania za pomocą którego proces okresowo wysyłane do określenia funkcji active. Dane wynikowe zapewnia liczenie częstotliwość funkcja znajdowała się na szczycie stosu wywołań proces był wtedy próbkowany.  
  
> [!NOTE]
> Narzędzia wiersza poleceń dla narzędzi profilowania znajdują się w podkatalogu \team tools\performance Tools katalogu instalacyjnego programu Visual Studio. Na komputerach 64-bitowym 64-bitowe i 32-bitowe wersje narzędzia są dostępne. Aby użyć narzędzi profilowania z wiersza polecenia, należy dodać ścieżkę do zmiennej środowiskowej PATH okna wiersza polecenia lub dodać do niej samo polecenie. Aby uzyskać więcej informacji, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Peopletrax — jest to aplikacja 32-bitowych.  
  
#### <a name="to-profile-the-peopletrax-application-by-using-the-sampling-method"></a>Aplikacja ma być profilowana peopletrax — przy użyciu metody próbkowania  
  
1. Przykładowa aplikacja peopletrax — Instalowanie i tworzenie wersji aplikacji.  
  
2. Otwórz okno wiersza polecenia i Dodaj katalog Profiling Tools do lokalnej zmiennej środowiskowej Path.  
  
3. Zmień katalog roboczy na katalog, który zawiera pliki binarne peopletrax —.  
  
4. Wpisz następujące polecenie, aby ustawić odpowiednie zmienne środowiskowe:  
  
    ```  
    VSPerfCLREnv /sampleon  
    ```  
  
5. Uruchom profilowanie, uruchamiając VSPerfCmd.exe, czyli narzędzie wiersza polecenia, który kontroluje profilera. Następujące polecenie uruchamia aplikację i profiler w trybie próbkowania:  
  
    ```  
    VsPerfCmd /start:sample /output:PeopleTraxReport.vsp /launch:PeopleTrax.exe  
    ```  
  
     Proces profiler uruchamia i dołącza do procesu PeopleTrax.exe. Uruchamia proces profiler do zapisywania zebranych danych profilowania do pliku raportu.  
  
6. Kliknij przycisk **Pobierz osoby**.  
  
7. Kliknij przycisk **ExportData**.  
  
     Notatnik otwiera i wyświetla nowy plik, który zawiera wyeksportowane dane z **peopletrax —**.  
  
8. Zamknij Notatnik, a następnie Zamknij **peopletrax —** aplikacji.  
  
9. Zamknij program profilujący. Wpisz następujące polecenie:  
  
    ```  
    VSPerfCmd /shutdown  
    ```  
  
10. Użyj następującego polecenia, aby zresetować zmienne środowiskowe:  
  
    ```  
    VSPerfCLREnv /sampleoff  
    ```  
  
11. Profilowanie danych są przechowywane w pliku the.vsp Analizuj wyniki za pomocą jednego z następujących metod:  
  
    - Otwórz plik the.vsp w środowisku IDE programu Visual Studio.  
  
         — lub —  
  
    - Generowanie pliku wartości rozdzielanych przecinkami (.csv) za pomocą narzędzia wiersza polecenia VSPerfReport.exe. Do generowania raportów dla użycia poza [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE, użyj następującego polecenia:  
  
        ```  
        VSPerfReport <dir> PeopleTraxReport.vsp /output:<dir> /summary:all  
        ```  
  
## <a name="see-also"></a>Zobacz też  
 [Sesja wydajności — omówienie](../profiling/performance-session-overview.md)   
 [Profilowanie z wiersza polecenia](../profiling/using-the-profiling-tools-from-the-command-line.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Z wartościami danych próbkowania opis](../profiling/understanding-sampling-data-values.md)   
 [Widoki raportu wydajności](../profiling/performance-report-views.md)
