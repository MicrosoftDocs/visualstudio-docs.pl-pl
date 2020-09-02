---
title: 'Przewodnik: Profilowanie wiersza polecenia przy użyciu próbkowania | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64820321"
---
# <a name="walkthrough-command-line-profiling-using-sampling"></a>Wskazówki: Profilowanie wiersza polecenia przy użyciu metody pobierania próbek
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym instruktażu pokazano, jak profilować aplikację przy użyciu narzędzi wiersza polecenia i próbkowania w celu identyfikowania problemów z wydajnością.  
  
 W tym instruktażu krok po kroku proces profilowania aplikacji zarządzanej przy użyciu narzędzi wiersza polecenia jest używany do wyodrębniania i identyfikowania problemów z wydajnością w aplikacji.  
  
 W tym instruktażu wykonasz następujące czynności:  
  
- Profilowanie aplikacji przy użyciu narzędzi wiersza polecenia i próbkowania.  
  
- Analizuj przykładowe wyniki profilowania, aby zlokalizować i rozwiązać problemy z wydajnością.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
  
- [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] lub [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
- Pośrednia interpretacja [!INCLUDE[csharp_current_short](../includes/csharp-current-short-md.md)]  
  
- Pośrednia znajomość pracy z narzędziami wiersza polecenia  
  
- Kopia [przykładu PeopleTrax —](../profiling/peopletrax-sample-profiling-tools.md)  
  
- Aby można było korzystać z informacji dostarczonych przez profilowanie, najlepszym rozwiązaniem jest udostępnienie informacji o symbolach debugowania.  
  
## <a name="command-line-profiling-using-the-sampling-method"></a>Profilowanie wiersza polecenia przy użyciu metody próbkowania  
 Próbkowanie to metoda profilowania, za pomocą której konkretny proces jest okresowo sondowany, aby określić aktywną funkcję. Dane wynikowe zawierają liczbę, jak często funkcja była w szczycie stosu wywołań, gdy proces został próbkowany.  
  
> [!NOTE]
> Narzędzia wiersza polecenia narzędzia profilowania znajdują się w podkatalogu \Team Tools\Performance Tools w katalogu instalacyjnym programu Visual Studio. Na komputerach 64 bitowych dostępne są zarówno wersje 64 bitowe, jak i 32 bitowe narzędzi. Aby użyć narzędzi wiersza polecenia profilera, należy dodać ścieżkę do zmiennej środowiskowej PATH okna wiersza polecenia lub dodać je do samego polecenia. Aby uzyskać więcej informacji, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). PeopleTrax — jest aplikacją 32-bitową.  
  
#### <a name="to-profile-the-peopletrax-application-by-using-the-sampling-method"></a>Aby profilować aplikację PeopleTrax — za pomocą metody próbkowania  
  
1. Zainstaluj przykładową aplikację PeopleTrax — i skompiluj wydaną wersję aplikacji.  
  
2. Otwórz okno wiersza polecenia i Dodaj katalog narzędzia profilowania do zmiennej środowiskowej ścieżka lokalna.  
  
3. Zmień katalog roboczy na katalog zawierający pliki binarne PeopleTrax —.  
  
4. Wpisz następujące polecenie, aby ustawić odpowiednie zmienne środowiskowe:  
  
    ```  
    VSPerfCLREnv /sampleon  
    ```  
  
5. Uruchom profilowanie, uruchamiając VSPerfCmd.exe, który jest narzędziem wiersza polecenia, które kontroluje Profiler. Następujące polecenie uruchamia aplikację i Profiler w trybie próbkowania:  
  
    ```  
    VsPerfCmd /start:sample /output:PeopleTraxReport.vsp /launch:PeopleTrax.exe  
    ```  
  
     Proces profilera zostanie uruchomiony i dołączy do procesu PeopleTrax.exe. Proces profilera rozpocznie pisanie zebranych danych profilowania do pliku raportu.  
  
6. Kliknij pozycję **Pobierz osoby**.  
  
7. Kliknij pozycję **ExportData**.  
  
     Zostanie otwarty Notatnik i zostanie wyświetlony nowy plik zawierający wyeksportowane dane z **PeopleTrax —**.  
  
8. Zamknij Notatnik, a następnie zamknij aplikację **PeopleTrax —** .  
  
9. Zamknij program profilujący. Wpisz następujące polecenie:  
  
    ```  
    VSPerfCmd /shutdown  
    ```  
  
10. Użyj następującego polecenia, aby zresetować zmienne środowiskowe:  
  
    ```  
    VSPerfCLREnv /sampleoff  
    ```  
  
11. Dane profilowania są przechowywane w pliku. vsp Przeanalizuj wyniki przy użyciu jednej z następujących metod:  
  
    - Otwórz plik VSP w środowisku IDE programu Visual Studio.  
  
         oraz  
  
    - Wygeneruj plik z wartościami rozdzielanymi przecinkami (CSV) za pomocą narzędzia wiersza polecenia VSPerfReport.exe. Aby generować raporty do użycia poza [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE, użyj następującego polecenia:  
  
        ```  
        VSPerfReport <dir> PeopleTraxReport.vsp /output:<dir> /summary:all  
        ```  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd sesji wydajności](../profiling/performance-session-overview.md)   
 [Profilowanie z wiersza polecenia](../profiling/using-the-profiling-tools-from-the-command-line.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Omówienie wartości danych próbkowania](../profiling/understanding-sampling-data-values.md)   
 [Widoki raportu wydajności](../profiling/performance-report-views.md)
