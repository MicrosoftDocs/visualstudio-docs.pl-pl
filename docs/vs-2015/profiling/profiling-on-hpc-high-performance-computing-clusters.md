---
title: Profilowanie na klastrach HPC (przetwarzanie o wysokiej wydajności) | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.hpc.wizard.exeoptions
- vs.performance.hpc.wizard.summary
- vs.performance.hpc.wizard.startoptions
- vs.performance.hpc.wizard.intro
- vs.performance.hpc.property.basic
- vs.performance.hpc.wizard.application
- vs.performance.hpc.wizard.clusteroptions
- vs.performance.hpc.property.advanced
helpviewer_keywords:
- profililng tools,HPC
- HPC profiling
ms.assetid: 1525bbdb-27da-4088-8487-a486cee5e7b3
caps.latest.revision: 27
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e952f9611b7bdb4d96e8a50b502ae15e1e6ce528
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54802317"
---
# <a name="profiling-on-hpc-high-performance-computing-clusters"></a>Profilowanie na klastrach HPC (przetwarzanie o wysokiej wydajności)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można profilować w węzłach obliczeniowych systemu Microsoft Windows HPC klastrów za pomocą metody pobierania próbek [!INCLUDE[vsPreExt](../includes/vspreext-md.md)] lub [!INCLUDE[vsUltExt](../includes/vsultext-md.md)] Profiling Tools. Aby uzyskać więcej informacji na temat HPC zobacz [Windows HPC](http://go.microsoft.com/fwlink/?LinkId=165393) w witrynie sieci Web firmy Microsoft.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby przeprowadzić profilowanie w węźle obliczeń HPC, wykonaj następujące czynności:  
  
- Zainstaluj Microsoft HPC Pack 2008 na tym samym komputerze co [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)]. Komputer nie musi być częścią klastra HPC. Można zainstalować pakietu HPC Pack na [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=177414).  
  
- Zainstaluj [!INCLUDE[net_v40_long](../includes/net-v40-long-md.md)] i węzła obliczeniowego autonomiczną wersję narzędzi profilowania w HPC. Zainstalować programy dla obu [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] a profiler autonomicznym dostępnych [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] nośnika instalacyjnego. **Uwaga** po wykonaniu procedury instalacji należy ponownie uruchomić obliczenia [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] oraz przed zainstalowaniem narzędzi profilowania.  
  
  Aby zainstalować [!INCLUDE[net_v40_long](../includes/net-v40-long-md.md)] i autonomicznych Profiling Tools na aktywne HPC obliczeń, węzeł i Włącz profilowanie na komputerze z klastra, wykonaj następujące kroki:  
  
1.  Otwórz okno wiersza polecenia, który został zainstalowany przy użyciu pakietu HPC pack.  
  
2.  Wpisz następujące polecenia w oddzielnych wierszy polecenia:  
  
    1.  `clusrun /all /scheduler:` *%HeadNode% %FxPath%* `/q /norestart`  
  
    2.  `clusrun /all /scheduler:` *Węzeł główny %* `shutdown /r /t 0 /d u:4:2 /c "Microsoft .NET Framework install required restart"`  
  
    3.  `clusrun /all /scheduler:` *%HeadNode% %ProfilerPath%* `/q /norestart`  
  
|||  
|-|-|  
|*%HeadNode%*|Nazwa węzła głównego klastra.|  
|*%FxPath%*|Ścieżka do [!INCLUDE[net_v40_long](../includes/net-v40-long-md.md)] Instalatora. Na [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] nośnika instalacyjnego ścieżka jest: WCU\dotNetFramework\dotNetFx40_Full_x86_x64.exe|  
|*%ProfilerPath%*|Ścieżka do wersji autonomicznego Instalatora narzędzi profilowania. Na [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] nośnika instalacyjnego ścieżka jest: Standalone Profiler\x64\vs_profiler.exe|  
  
## <a name="profiling-on-an-hpc-compute-node"></a>Profilowanie w węźle obliczeń HPC  
 Sesję profilowania można skonfigurować za pomocą Kreatora osiągów HPC pozwala określić informacje o klastra i docelowy HPC. Można ustawić dodatkowe opcje na stronach właściwości sesji wydajności. Profiling Tools automatycznie wdrożyć pliki binarne niezbędne docelowy i uruchom program profilujący i aplikacji HPC.  
  
#### <a name="to-profile-on-an-hpc-compute-node"></a>Aby przeprowadzić profilowanie w węźle obliczeń HPC  
  
1.  Na **analizy** menu, kliknij przycisk **Uruchom Kreatora wydajności HPC**. Jeśli polecenie nie jest dostępny, upewnij się, że wymagania wstępne wymienione powyżej.  
  
2.  Kliknij przycisk **dalej** na pierwszej stronie kreatora.  
  
3.  Na drugiej stronie kreatora wybierz aplikację, którą chcesz profilować.  
  
    -   Aby profilować projekt, który jest obecnie otwarty w [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)], wybierz opcję **co najmniej jeden z dostępnych projektów** opcji, a następnie wybierz nazwę projektu z listy.  
  
    -   Aby przeprowadzić profilowanie plik binarny, który nie znajduje się w otwartym projekcie wybierz **plik wykonywalny (. Plik EXE)** opcji.  
  
4.  Kliknij przycisk **Dalej**.  
  
5.  Na trzeciej stronie kreatora:  
  
    -   Jeśli profilowany plik wykonywalny, który nie znajduje się w otwartym projekcie, określ ścieżkę do pliku binarnego w **co to jest pełna ścieżka do pliku wykonywalnego**.  
  
    -   Jeśli profilowany plik wykonywalny, który nie znajduje się w otwartym projekcie, można określić argumenty wiersza polecenia do przekazania do procesu w **argumenty wiersza polecenia**.  
  
    -   W **zdalny katalog roboczy**, określ ścieżkę do folderu, który jest używany przez wystąpień procesu na poszczególnych węzłach obliczeniowych.  
  
    -   W **lokalizacji wdrożenia**, określ ścieżkę do katalogu, w którym używane przez serwer HPC na etapie obrazy dla wdrożenia.  
  
6.  Kliknij przycisk **Dalej**.  
  
7.  Na czwartej stronie kreatora:  
  
    -   W **węzeł główny** listy, kliknij komputer, który działa jako węzeł główny HPC podczas uruchomienia profilowania. Węzeł główny może być "localhost", co umożliwia profilu na komputerze lokalnym bez konieczności stosowania klastra.  
  
    -   W **liczba procesów** kliknij liczbę wystąpień do uruchomienia aplikacji.  
  
    -   Z **profilowania opcje** wybierz celu profilowania.  
  
         Aby profilować proces w klastrze, wybierz **profilu na ranga** opcji, a następnie wybierz pozycję proces z listy rozwijanej.  
  
         Aby profilować proces lub procesy, które są uruchamiane w określonym węźle w klastrze HPC, wybierz **profilu w węźle** opcji, a następnie wybierz węzeł z listy rozwijanej.  
  
8.  Kliknij przycisk **Dalej**.  
  
9. Na piątej stronie kreatora można wybrać, aby natychmiast uruchomić profiler jak i profilowania procesu lub do uruchomienia profilowania później za pomocą Eksploratora wydajności.  
  
    -   Wybierz **Uruchom profilowanie po zakończeniu pracy kreatora** Uruchom profilowanie natychmiast lub usuń zaznaczenie pola wyboru, aby rozpocząć profilowanie ręcznie.  
  
10. Kliknij przycisk **Zakończ**.  
  
## <a name="setting-hpc-profiling-properties-by-using-performance-session-property-pages"></a>Ustawianie właściwości profilowanie HPC za pomocą stron właściwości sesji wydajności  
 Można zmienić właściwości sesji wydajności, które ustawione w Kreatorze profilowanie HPC na stronie właściwości uruchamiania HPC na stronie właściwości sesji wydajności. Możesz ustawić dodatkowe opcje na stronie właściwości zaawansowane HPC.  
  
#### <a name="to-open-the-performance-session-property-pages"></a>Aby otworzyć na stronach właściwości sesji wydajności  
  
1.  Jeśli to konieczne, otwórz plik sesji (.psess) wydajności w Eksploratorze wydajności. Na **pliku** menu, kliknij przycisk **Otwórz** i zlokalizuj plik.  
  
2.  W Eksploratorze wydajności, kliknij prawym przyciskiem myszy nazwę sesji wydajności, a następnie kliknij przycisk **właściwości**.  
  
3.  W oknie dialogowym stron właściwości użyj jednej z następujących metod:  
  
    -   Kliknij przycisk **ogólne** , a następnie wybierz **zbieranie klastra HPC** Włącz profilowanie HPC lub usuń zaznaczenie pola wyboru, aby wyłączyć profilowanie HPC.  
  
    -   Kliknij przycisk **właściwości uruchamiania HPC** można zmienić właściwości, które Uruchom aplikację HPC.  
  
    -   Kliknij przycisk **HPC zaawansowane właściwości** można ustawić opcje dodatkowe  
  
### <a name="hpc-launch-properties"></a>Właściwości uruchamiania HPC  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|**Węzeł główny**|Określa komputer, który działa jako węzeł główny HPC w trakcie uruchomienia profilowania.|  
|**Liczba procesów**|Określa liczbę wystąpień aplikacji do uruchamiania w profilowanej aplikacji.|  
|**Profiluj ranga**|Aby profilować proces w klastrze, wybierz **profilu na ranga** opcji, a następnie wybierz pozycję proces z listy rozwijanej.|  
|**Profil w węźle**|Aby profilować proces lub procesy, które są uruchamiane w określonym węźle w klastrze HPC, wybierz **profilu w węźle** opcji, a następnie wybierz węzeł z listy rozwijanej.|  
|**Zdalny katalog roboczy**|Określa ścieżkę do folderu, który jest używany przez wystąpień procesu na poszczególnych węzłach obliczeniowych.|  
|**Lokalizacja wdrożenia**|Określa ścieżkę do katalogu, używany przez serwer HPC na etapie obrazy dla wdrożenia.|  
  
### <a name="advanced-properties"></a>Właściwości zaawansowane  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|**Nazwa projektu**|Nazwa bieżącego [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] projekt lub rozwiązanie.|  
|**Czyszczenie, gdy narzędzie profiler jest zatrzymane**|W przypadku wartości true spowoduje usunięcie plików binarnych, które zostały wdrożone w katalogu wykonywania. Pliki i katalogi utworzone przez program użytkownika nie są usuwane w tym kroku. Jeśli katalogu wykonywania i katalog wdrożenia zostały utworzone przez środowisko IDE, IDE podejmie próbę usunięcia ich, ale nie zrobić, jeśli mają one pliki nie są wdrażane przez środowisko IDE.|  
|**Dodatkowe pliki do wdrożenia**|Określa listę rozdzielonych średnikami wszelkie dodatkowe pliki do wdrożenia w węźle obliczeniowym. Możesz kliknąć przycisk wielokropka (**...** ) aby wybrać wiele plików za pomocą okna dialogowego.|  
|**Polecenie Mpiexec**|Określa aplikację, która uruchamiania aplikacji MPI. Wartość domyślna to **mpiexec.exe**|  
|**Argumenty Mpiexec**|Określa argumenty do przekazania do polecenia mpiexec.exe.|  
|**Żądane węzły w klastrze**|Określa liczbę węzłów w klastrze, na którym chcesz uruchomić aplikację.|  
|**Wdrażanie plików CRT**|W przypadku wartości true powoduje wdrożenie C/C++, w czasie wykonywania w klastrze.|  
|**Skrypt przed profilu**|Określa ścieżkę i nazwę skryptu do uruchomienia na lokalnym komputerze deweloperskim, przed uruchomieniem sesji profilowania.|  
|**Argumenty skryptu przed profilu**|Określa argumenty do przekazania do skryptu przed profilu.|  
|**Po utworzeniu profilu skryptu**|Określa ścieżkę i nazwę skryptu do uruchomienia na lokalnym komputerze deweloperskim, po zakończeniu sesji profilowania.|  
|**Po utworzeniu profilu argumenty skryptu**|Określa argumenty do przekazania do skryptu po profilu.|
