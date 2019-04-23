---
title: 'Przewodnik: Profilowanie wiersza polecenia przy użyciu metody Instrumentacji | Dokumentacja firmy Microsoft'
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
ms.openlocfilehash: d5b7e8dbe12f9c57c101c8f877dfcb0c6ee3196f
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60064696"
---
# <a name="walkthrough-command-line-profiling-using-instrumentation"></a>Przewodnik: Wiersza polecenia, profilowania przy użyciu metody Instrumentacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ten przewodnik przeprowadzi Cię przez profilowanie [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] aplikacji autonomicznej zbierać szczegółowe informacje o czasach i wywoływać dane dotyczące liczby przy użyciu metody instrumentacji dla narzędzi profilowania. W tym przewodniku będzie wykonywać następujące zadania:  
  
- Użyj [VSInstr](../profiling/vsinstr.md) narzędzia wiersza polecenia, aby wygenerować instrumentowanych danych binarnych.  
  
- Użyj [VSPerfCLREnv](../profiling/vsperfclrenv.md) narzędzie do ustawiania zmiennych środowiskowych w celu zbierania danych profilowania dla programu .NET.  
  
- Użyj [VSPerfCmd](../profiling/vsperfcmd.md) narzędzia do zbierania danych profilowania.  
  
- Użyj [VSPerfReport](../profiling/vsperfreport.md) narzędzie do generowania raportów na podstawie pliku danych profilowania.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
  
- [!INCLUDE[vsprvsts](../includes/vsprvsts-md.md)]  
  
- Pośredni znajomości języka C#  
  
- Pośredni, informacje o pracy z narzędzi wiersza polecenia  
  
- Kopię [peopletrax — przykład](../profiling/peopletrax-sample-profiling-tools.md)  
  
- Aby pracować z danymi dostarczonych przez profilowanie, najlepiej jest mieć debugowania dostępnych informacji o symbolach. Aby uzyskać więcej informacji, zobacz [jak: Informacje o symbolach Windows odwołanie](../profiling/how-to-reference-windows-symbol-information.md).  
  
## <a name="command-line-profiling-using-the-instrumentation-method"></a>Polecenie wiersza profilowania przy użyciu metody Instrumentacji  
 Instrumentacja jest metody profilowania za pomocą którego specjalnie utworzone wersje profilowanych danych binarnych zawiera funkcje sondy, które zbierają informacje o czasie na wejścia i wyjścia funkcji w moduł instrumentowany. Ponieważ ta metoda profilowania jest bardziej inwazyjne niż próbkowanie, spowoduje naliczenie większej ilości obciążenia. Instrumentowane pliki binarne są również większych niż Debuguj lub zwolnij pliki binarne i nie są przeznaczone do wdrożenia.  
  
> [!NOTE]
>  Nie wysyłaj instrumentowanych danych binarnych dla klientów. Instrumentowanych danych binarnych mogą zawierać kilka zagrożeń. Pliki binarne obejmują informacje, które ułatwia aplikacji odtwarzania, a także zagrożenia dla bezpieczeństwa.  
  
#### <a name="to-profile-the-peopletrax-application-by-using-the-instrumentation-method"></a>Aplikacja ma być profilowana peopletrax — przy użyciu metody Instrumentacji  
  
1. Zainstaluj Przykładowa aplikacja peopletrax — i Utwórz pełnej wersji.  
  
2. Otwórz okno wiersza polecenia i Dodaj **Profiling Tools** katalogu do lokalnej zmiennej środowiskowej Path.  
  
3. Zmień katalog roboczy na katalog zawierający pliki binarne peopletrax —.  
  
4. Utwórz katalog zawiera raporty na podstawie plików. Wpisz następujące polecenie:  
  
    ```  
    md Reports  
    ```  
  
5. Użyj narzędzia wiersza polecenia VSInstr do Instrumentacji danych binarnych w aplikacji. Wpisz następujące polecenia w osobnych wierszach polecenia:  
  
    ```  
    VSInstr PeopleTrax.exe  
    VSInstr PeopleTrax.exe  
    VSInstr People.dll  
    VSInstr Person.dll  
    VSInstr Operation.dll  
    ```  
  
     **Uwaga** Domyślnie narzędzie VSInstr zapisuje nieinstrumentowanego kopii zapasowej oryginalnego pliku. Nazwa pliku kopii zapasowej ma rozszerzenie. orig. Na przykład oryginalną wersję "MyApp.exe" zostaną zapisane jako "MyApp.exe.orig."  
  
6. Wpisz następujące polecenie, aby ustawić odpowiednie zmienne środowiskowe:  
  
    ```  
    VsPerfCLREnv /traceon  
    ```  
  
7. Aby uruchomić program profilujący, wpisz następujące polecenie:  
  
    ```  
    VsPerfCmd /start:trace /output:Reports\Report.vsp  
    ```  
  
8. Po uruchomieniu programu profilującego w trybie śledzenia z wersją instrumentowaną PeopleTrax.exe procesu zbierania danych.  
  
     **Peopletrax —** pojawi się okno aplikacji.  
  
9. Kliknij przycisk **Pobierz osoby**.  
  
     Peopletrax — Siatka danych zostaną wyświetlone wszystkie dane.  
  
10. Kliknij przycisk **eksportowanie danych**.  
  
     Notatnik rozpoczyna się i wyświetla nowy plik, który zawiera listę użytkowników z **peopletrax —** aplikacji.  
  
11. Zamknij Notatnik, a następnie Zamknij **peopletrax —** aplikacji.  
  
12. Zamknij program profilujący. Wpisz następujące polecenie:  
  
    ```  
    VSPerfCmd /shutdown  
    ```  
  
13. Wpisz następujące polecenie, aby zresetować zmienne środowiskowe:  
  
    ```  
    VSPerfCLREnv /off  
    ```  
  
14. Użyj vsperfreport — narzędzie do generowania lub pliki raportu wartości rozdzielanych przecinkami (CSV). Wpisz:  
  
    ```  
    VSPerfReport Reports\Report.vsp /output:Reports /summary:all  
    ```  
  
     Możesz analizować wygenerowanych raportów w programie arkusz kalkulacyjny lub użyć [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE do analizowania danych profilowania w pliku Report.vsp. Aby uzyskać więcej informacji, zobacz [analizowanie danych dotyczących narzędzi wydajności](../profiling/analyzing-performance-tools-data.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Sesja wydajności — omówienie](../profiling/performance-session-overview.md)   
 [Profilowanie z wiersza polecenia](../profiling/using-the-profiling-tools-from-the-command-line.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Z wartościami danych próbkowania opis](../profiling/understanding-sampling-data-values.md)   
 [Widoki raportu wydajności](../profiling/performance-report-views.md)
