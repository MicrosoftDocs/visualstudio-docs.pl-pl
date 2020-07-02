---
title: Profilowanie na klastrach HPC (przetwarzanie o wysokiej wydajności) | Microsoft Docs
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
ms.openlocfilehash: b63f9ddf29ff74a4aa4bf089c266e12e37bb2f50
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85535541"
---
# <a name="profiling-on-hpc-high-performance-computing-clusters"></a>Profilowanie na klastrach HPC (przetwarzanie o wysokiej wydajności)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można profilować węzły obliczeniowe klastrów HPC systemu Microsoft Windows przy użyciu metody próbkowania [!INCLUDE[vsPreExt](../includes/vspreext-md.md)] lub [!INCLUDE[vsUltExt](../includes/vsultext-md.md)] narzędzia profilowania. Aby uzyskać więcej informacji na temat HPC zobacz [duże ilości obliczeń: hpc & Batch](https://azure.microsoft.com/solutions/big-compute/) w witrynie sieci Web firmy Microsoft.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby profilować w węźle obliczeniowym HPC, należy wykonać następujące czynności:  
  
- Zainstaluj pakiet Microsoft HPC Pack 2008 na tym samym komputerze, co [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] . Komputer nie musi być częścią klastra HPC. Pakiet HPC Pack można zainstalować w [Centrum pobierania Microsoft](https://www.microsoft.com/download/details.aspx?id=2800).  
  
- Zainstaluj i autonomiczną [!INCLUDE[net_v40_long](../includes/net-v40-long-md.md)] wersję narzędzia profilowania w węźle obliczeniowym HPC. Zainstaluj programy zarówno dla programu [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] , jak i dla autonomicznego profilera są dostępne na [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] nośniku instalacyjnym programu. **Uwaga** Po zainstalowaniu [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] programu i przed zainstalowaniem narzędzia profilowania należy ponownie uruchomić obliczenia.  
  
  Aby zainstalować [!INCLUDE[net_v40_long](../includes/net-v40-long-md.md)] i autonomiczną narzędzia profilowania na aktywnym węźle obliczeniowym HPC i włączyć profilowanie na maszynie klastra, wykonaj następujące kroki:  
  
1. Otwórz okno wiersza polecenia, które jest instalowane z pakietem HPC Pack.  
  
2. Wpisz następujące polecenia w oddzielnych wierszach polecenia:  
  
    1. `clusrun /all /scheduler:`*% Węzła głównego%% FxPath%*`/q /norestart`  
  
    2. `clusrun /all /scheduler:`*% Węzła głównego%*`shutdown /r /t 0 /d u:4:2 /c "Microsoft .NET Framework install required restart"`  
  
    3. `clusrun /all /scheduler:`*% Węzła głównego%% ProfilerPath%*`/q /norestart`  
  
|Element składni|Opis|  
|-|-|  
|*Węzła głównego*|Nazwa węzła głównego klastra.|  
|*%FxPath%*|Ścieżka do [!INCLUDE[net_v40_long](../includes/net-v40-long-md.md)] Instalatora. Na [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] nośniku instalacyjnym ścieżka jest: WCU\dotNetFramework\dotNetFx40_Full_x86_x64.exe|  
|*%ProfilerPath%*|Ścieżka do autonomicznej wersji Instalatora narzędzia profilowania. Na [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] nośniku instalacyjnym ścieżka jest: autonomiczna Profiler\x64\vs_profiler.exe|  
  
## <a name="profiling-on-an-hpc-compute-node"></a>Profilowanie w węźle obliczeniowym HPC  
 Aby określić klaster HPC i informacje docelowe, należy skonfigurować sesję profilowania przy użyciu Kreatora wydajności HPC. Dodatkowe opcje można ustawić na stronie właściwości sesji wydajności. Narzędzia profilowania automatycznie wdrażać niezbędne docelowe pliki binarne i uruchamiać Profiler i aplikację HPC.  
  
#### <a name="to-profile-on-an-hpc-compute-node"></a>Aby profilować węzeł obliczeniowy HPC  
  
1. W menu **Analizuj** kliknij polecenie **Uruchom Kreatora wydajności HPC**. Jeśli polecenie jest niedostępne, upewnij się, że masz wymienione powyżej wymagania wstępne.  
  
2. Kliknij przycisk **dalej** na pierwszej stronie kreatora.  
  
3. Na drugiej stronie kreatora wybierz aplikację, którą chcesz profilować.  
  
    - Aby profilować projekt, który jest aktualnie otwarty w programie [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] , wybierz opcję **co najmniej jeden dostępny projekt** , a następnie wybierz nazwę projektu z listy.  
  
    - Aby profilować plik binarny, który nie znajduje się w otwartym projekcie, wybierz **plik wykonywalny (. Plik EXE)** .  
  
4. Kliknij przycisk **Dalej**.  
  
5. Na trzeciej stronie kreatora:  
  
    - Jeśli tworzysz plik wykonywalny, który nie znajduje się w otwartym projekcie, określ ścieżkę do pliku binarnego, w którym **jest pełna ścieżka do pliku wykonywalnego**.  
  
    - Jeśli tworzysz plik wykonywalny, który nie znajduje się w otwartym projekcie, możesz określić argumenty wiersza polecenia do przekazania do procesu w **argumentach wiersza polecenia**.  
  
    - W obszarze **zdalny katalog roboczy**określ ścieżkę do folderu, który jest używany przez wystąpienia procesów w poszczególnych węzłach obliczeniowych.  
  
    - W obszarze **Lokalizacja wdrożenia**określ ścieżkę do katalogu, którego serwer HPC używa do przygotowywania obrazów do wdrożenia.  
  
6. Kliknij przycisk **Dalej**.  
  
7. Na czwartej stronie kreatora:  
  
    - Na liście **węzeł główny** kliknij komputer, który działa jako węzeł główny HPC w przebiegu profilowania. Węzłem głównym może być "localhost", który umożliwia profilowanie na komputerze lokalnym bez potrzeby klastra.  
  
    - Na liście **liczba procesów** kliknij liczbę wystąpień aplikacji do uruchomienia.  
  
    - Z listy **Opcje profilowania** wybierz element docelowy profilowania.  
  
         Aby profilować określony proces w klastrze, wybierz pozycję **profil w opcji ranga** , a następnie wybierz rangę procesu z listy rozwijanej.  
  
         Aby profilować proces lub procesy uruchamiane w określonym węźle w klastrze HPC, zaznacz opcję **profil w węźle** , a następnie wybierz węzeł z listy rozwijanej.  
  
8. Kliknij przycisk **Dalej**.  
  
9. Na piątej stronie kreatora można natychmiast uruchomić Profiler i proces profilowania lub uruchomić profilowanie później przy użyciu Eksplorator wydajności.  
  
    - Wybierz pozycję **Uruchom profilowanie po zakończeniu pracy Kreatora** , aby natychmiast rozpocząć profilowanie, lub usuń zaznaczenie tego pola wyboru, aby uruchomić profilowanie ręcznie.  
  
10. Kliknij przycisk **Zakończ**.  
  
## <a name="setting-hpc-profiling-properties-by-using-performance-session-property-pages"></a>Ustawianie właściwości profilowania HPC przy użyciu stron właściwości sesji wydajności  
 Można zmienić właściwości sesji wydajności ustawione w Kreatorze profilowania HPC na stronie właściwości uruchamiania HPC na stronie właściwości sesji wydajności. Dodatkowe opcje można ustawić na stronie właściwości zaawansowane HPC.  
  
#### <a name="to-open-the-performance-session-property-pages"></a>Aby otworzyć strony właściwości sesji wydajności  
  
1. W razie potrzeby Otwórz plik sesji wydajności (. psess) w Eksplorator wydajności. W menu **plik** kliknij polecenie **Otwórz** i Znajdź plik.  
  
2. W Eksplorator wydajności kliknij prawym przyciskiem myszy nazwę sesji wydajności, a następnie kliknij polecenie **Właściwości**.  
  
3. W oknie dialogowym strony właściwości Użyj jednej z następujących metod:  
  
    - Kliknij pozycję **Ogólne** , a następnie wybierz pozycję **Zbieraj w klastrze HPC** , aby włączyć profilowanie HPC, lub usuń zaznaczenie tego pola wyboru, aby wyłączyć profilowanie HPC.  
  
    - Kliknij pozycję **Właściwości uruchomienia HPC** , aby zmienić właściwości, które uruchamiają aplikację HPC.  
  
    - Kliknij pozycję **Właściwości zaawansowane HPC** , aby ustawić dodatkowe opcje  
  
### <a name="hpc-launch-properties"></a>Właściwości uruchamiania HPC  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|**Węzeł główny**|Określa komputer, który działa jako węzeł główny HPC w przebiegu profilowania.|  
|**Liczba procesów**|Określa liczbę wystąpień aplikacji do uruchomienia w profilowanej aplikacji.|  
|**Profil na rangi**|Aby profilować określony proces w klastrze, wybierz pozycję **profil w opcji ranga** , a następnie wybierz rangę procesu z listy rozwijanej.|  
|**Profil w węźle**|Aby profilować proces lub procesy uruchamiane w określonym węźle w klastrze HPC, zaznacz opcję **profil w węźle** , a następnie wybierz węzeł z listy rozwijanej.|  
|**Zdalny katalog roboczy**|Określa ścieżkę do folderu, który jest używany przez wystąpienia procesów w poszczególnych węzłach obliczeniowych.|  
|**Lokalizacja wdrożenia**|Określa ścieżkę do katalogu, którego serwer HPC używa do przygotowywania obrazów do wdrożenia.|  
  
### <a name="advanced-properties"></a>Właściwości zaawansowane  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|**Nazwa projektu**|Nazwa bieżącego [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] projektu lub rozwiązania.|  
|**Wyczyść po zatrzymaniu profilera**|W przypadku wartości true program usuwa pliki binarne, które zostały wdrożone w katalogu wykonywania. Pliki i katalogi utworzone przez program użytkownika nie są usuwane w tym kroku. Jeśli katalog wykonywania i katalog wdrożenia zostały utworzone przez IDE, środowisko IDE próbuje je usunąć, ale nie tak, jeśli mają pliki, które nie są wdrażane przez IDE.|  
|**Dodatkowe pliki do wdrożenia**|Określa rozdzielaną średnikami listę dodatkowych plików do wdrożenia w węźle obliczeniowym. Możesz kliknąć przycisk wielokropka (**...**), aby wybrać wiele plików przy użyciu okna dialogowego.|  
|**Mpiexec — polecenie**|Określa aplikację, która uruchamia aplikację MPI. Wartość domyślna to **mpiexec.exe**|  
|**Argumenty mpiexec**|Określa argumenty, które zostaną przekazane do polecenia mpiexec.exe.|  
|**Żądane węzły w klastrze**|Określa liczbę węzłów w klastrze, na którym ma zostać uruchomiona aplikacja.|  
|**Wdróż pliki CRT**|W przypadku wartości true program wdraża w klastrze czas wykonywania C/C++.|  
|**Skrypt przed profilem**|Określa ścieżkę i nazwę pliku skryptu do uruchomienia na lokalnym komputerze deweloperskim przed rozpoczęciem sesji profilowania.|  
|**Argumenty skryptu przed profilem**|Określa argumenty, które mają zostać przekazane do skryptu przed profilem.|  
|**Skrypt po profilu**|Określa ścieżkę i nazwę pliku skryptu do uruchomienia na lokalnym komputerze deweloperskim po zakończeniu sesji profilowania.|  
|**Argumenty skryptu po profilu**|Określa argumenty, które mają zostać przekazane do skryptu po profilu.|
