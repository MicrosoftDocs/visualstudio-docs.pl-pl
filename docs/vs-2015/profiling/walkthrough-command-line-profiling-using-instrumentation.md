---
title: 'Przewodnik: Profilowanie wiersza polecenia przy użyciu instrumentacji | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, walkthroughs
- performance tools, walkthroughs
- performance tools, command-line tools
ms.assetid: 1c6f1586-3d6a-431f-bedf-c54088e280ba
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3a37350cf274fbb551326ac96387330b0f3956e7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64817647"
---
# <a name="walkthrough-command-line-profiling-using-instrumentation"></a>Wskazówki: Profilowanie wiersza polecenia przy użyciu metody instrumentacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ten przewodnik obejmuje przechodzenie przez profilowanie [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] aplikacji autonomicznej w celu zbierania szczegółowych danych o chronometrażu i liczbie wywołań przy użyciu metody instrumentacji narzędzia profilowania. W tym instruktażu zostaną wykonane następujące zadania:  
  
- Użyj narzędzia wiersza polecenia [VSInstr](../profiling/vsinstr.md) , aby wygenerować instrumentację plików binarnych.  
  
- Użyj narzędzia [VSPerfCLREnv](../profiling/vsperfclrenv.md) , aby ustawić zmienne środowiskowe w celu zbierania danych profilowania platformy .NET.  
  
- Użyj narzędzia [VSPerfCmd](../profiling/vsperfcmd.md) , aby zebrać dane profilowania.  
  
- Użyj narzędzia [VSPerfReport](../profiling/vsperfreport.md) , aby wygenerować raporty oparte na plikach dla danych profilowania.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
  
- [!INCLUDE[vsprvsts](../includes/vsprvsts-md.md)]  
  
- Pośrednia znajomość języka C #  
  
- Pośrednia znajomość pracy z narzędziami wiersza polecenia  
  
- Kopia [przykładu PeopleTrax —](../profiling/peopletrax-sample-profiling-tools.md)  
  
- Aby można było korzystać z informacji dostarczonych przez profilowanie, najlepszym rozwiązaniem jest udostępnienie informacji o symbolach debugowania. Aby uzyskać więcej informacji, zobacz [How to: Reference informacje o symbolach systemu Windows](../profiling/how-to-reference-windows-symbol-information.md).  
  
## <a name="command-line-profiling-using-the-instrumentation-method"></a>Profilowanie wiersza polecenia przy użyciu metody instrumentacji  
 Instrumentacja to metoda profilowania, za pomocą której specjalnie skompilowane wersje plików binarnych zawierają funkcje sondowania, które zbierają informacje o chronometrażu w momencie wejścia i wyjścia do funkcji w module Instrumentacji. Ponieważ ta metoda profilowania jest bardziej inwazyjna niż próbkowanie, wiąże się to z większą ilością narzutów. Instrumentacja plików binarnych jest również większa niż debugowanie lub wydanie plików binarnych i nie jest przeznaczona do wdrożenia.  
  
> [!NOTE]
> Nie wysyłaj do klientów plików binarnych instrumentacji. Instrumentacja plików binarnych może zawierać kilka zagrożeń. Pliki binarne zawierają informacje ułatwiające odtworzenie aplikacji, a także zagrożenia bezpieczeństwa.  
  
#### <a name="to-profile-the-peopletrax-application-by-using-the-instrumentation-method"></a>Aby profilować aplikację PeopleTrax — przy użyciu metody instrumentacji  
  
1. Zainstaluj przykładową aplikację PeopleTrax — i skompiluj wersję release.  
  
2. Otwórz okno wiersza polecenia i Dodaj katalog **narzędzia profilowania** do zmiennej środowiskowej ścieżka lokalna.  
  
3. Zmień katalog roboczy na katalog zawierający pliki binarne PeopleTrax —.  
  
4. Utwórz katalog zawierający raporty na podstawie plików. Wpisz następujące polecenie:  
  
    ```  
    md Reports  
    ```  
  
5. Użyj narzędzia wiersza polecenia VSInstr do instrumentowania plików binarnych w aplikacji. W oddzielnych wierszach polecenia wpisz następujące polecenia:  
  
    ```  
    VSInstr PeopleTrax.exe  
    VSInstr PeopleTrax.exe  
    VSInstr People.dll  
    VSInstr Person.dll  
    VSInstr Operation.dll  
    ```  
  
     **Uwaga** Domyślnie VSInstr zapisuje nieinstrumentację kopii zapasowej oryginalnego pliku. Nazwa pliku kopii zapasowej ma rozszerzenie. orig. Na przykład oryginalna wersja "MyApp.exe" zostałaby zapisana jako "MyApp.exe. orig".  
  
6. Wpisz następujące polecenie, aby ustawić odpowiednie zmienne środowiskowe:  
  
    ```  
    VsPerfCLREnv /traceon  
    ```  
  
7. Aby uruchomić Profiler, wpisz następujące polecenie:  
  
    ```  
    VsPerfCmd /start:trace /output:Reports\Report.vsp  
    ```  
  
8. Po uruchomieniu profilera w trybie śledzenia Uruchom instrumentację wersji procesu PeopleTrax.exe, aby zebrać dane.  
  
     Zostanie wyświetlone okno aplikacji **PeopleTrax —** .  
  
9. Kliknij pozycję **Pobierz osoby**.  
  
     Siatka danych PeopleTrax — wypełnia dane.  
  
10. Kliknij przycisk **Eksportuj dane**.  
  
     Zostanie uruchomiony Notatnik i zostanie wyświetlony nowy plik zawierający listę osób z aplikacji **PeopleTrax —** .  
  
11. Zamknij Notatnik, a następnie zamknij aplikację **PeopleTrax —** .  
  
12. Zamknij program profilujący. Wpisz następujące polecenie:  
  
    ```  
    VSPerfCmd /shutdown  
    ```  
  
13. Wpisz następujące polecenie, aby zresetować zmienne środowiskowe:  
  
    ```  
    VSPerfCLREnv /off  
    ```  
  
14. Użyj narzędzia VSPerfReport, aby wygenerować pliki raportów z wartościami rozdzielanymi przecinkami (CSV). Wpisz:  
  
    ```  
    VSPerfReport Reports\Report.vsp /output:Reports /summary:all  
    ```  
  
     Można analizować wygenerowane raporty w programie arkusza kalkulacyjnego lub użyć [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE do analizowania danych profilowania w pliku Report. vsp. Aby uzyskać więcej informacji, zobacz [Analizowanie danych narzędzi wydajności](../profiling/analyzing-performance-tools-data.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd sesji wydajności](../profiling/performance-session-overview.md)   
 [Profilowanie z wiersza polecenia](../profiling/using-the-profiling-tools-from-the-command-line.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Omówienie wartości danych próbkowania](../profiling/understanding-sampling-data-values.md)   
 [Widoki raportu wydajności](../profiling/performance-report-views.md)
