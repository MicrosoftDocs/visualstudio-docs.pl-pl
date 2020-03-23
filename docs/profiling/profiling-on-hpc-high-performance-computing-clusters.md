---
title: Profilowanie w klastrach HPC (High Performance Computing) | Dokumenty firmy Microsoft
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: f2d3949194dedab6d7e7ea2faa1aea304d889bc4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74772123"
---
# <a name="profile-on-hpc-high-performance-computing-clusters"></a>Profil w klastrach HPC (high performance computing)

Można profilować w węzłach obliczeniowych klastrów HPC systemu Microsoft Windows przy użyciu metody próbkowania narzędzi profilowania programu Visual Studio. Aby uzyskać więcej informacji na temat HPC, zobacz [HpC systemu Windows](https://azure.microsoft.com/solutions/big-compute/) w witrynie firmy Microsoft w sieci Web.

## <a name="prerequisites"></a>Wymagania wstępne

Aby profilować w węźle obliczeniowym HPC, należy wykonać następujące czynności:

- Zainstaluj pakiet Microsoft HPC Pack 2008 na tym samym komputerze co program Visual Studio. Komputer nie musi być częścią klastra HPC. Pakiet HPC Pack można zainstalować w [Centrum pobierania Microsoft](https://www.microsoft.com/download/details.aspx?id=4812).

- Zainstaluj program .NET Framework 4 i autonomiczną wersję narzędzi profilowania w węźle obliczeniowym HPC. Instalowanie programów dla programu .NET Framework i autonomicznego profilera są dostępne na nośniku instalacyjnym programu Visual Studio. **Uwaga** Należy ponownie uruchomić obliczenia po zainstalowaniu programu .NET Framework i przed zainstalowaniem narzędzi profilowania.

  Aby zainstalować program .NET Framework 4 i autonomiczne narzędzia profilowania w aktywnym węźle obliczeniowym HPC i włączyć profilowanie na komputerze klastra, wykonaj następujące kroki:

1. Otwórz okno wiersza polecenia zainstalowanego z pakietem HPC.

2. W osobnych wierszach polecenia wpisz następujące polecenia:

    1. `clusrun /all /scheduler:`*%HeadNode% %FxPath%*`/q /norestart`

    2. `clusrun /all /scheduler:`*%HeadNode%*`shutdown /r /t 0 /d u:4:2 /c "Microsoft .NET Framework install required restart"`

    3. `clusrun /all /scheduler:`*%HeadNode% %ProfilerPath%*`/q /norestart`

| | |
|------------------| - |
| *%HeadNode%* | Nazwa węzła głównego klastra. |
| *%FxPath%* | Ścieżka do instalatora .NET Framework 4. Na nośniku instalacyjnym programu Visual Studio ścieżka to: WCU\dotNetFramework\dotNetFx40_Full_x86_x64.exe |
| *%ProfilerPath%* | Ścieżka do autonomicznej wersji instalatora narzędzi profilowania. Na nośniku instalacyjnym programu Visual Studio ścieżka to: Standalone Profiler\x64\vs_profiler.exe |

## <a name="profile-on-an-hpc-compute-node"></a>Profil w węźle obliczeniowym HPC

Sesję profilowania można skonfigurować za pomocą Kreatora wydajności HPC w celu określenia klastra HPC i informacji o obiektach docelowych. Na stronach właściwości sesji wydajności można ustawić dodatkowe opcje. Narzędzia profilowania automatycznie wdrażają niezbędne pliki binarne docelowych i uruchamiają profiler i aplikację HPC.

1. W menu **Analiza** kliknij polecenie **Uruchom Kreatora wydajności HPC**. Jeśli polecenie nie jest dostępne, upewnij się, że masz wymagania wstępne wymienione powyżej.

2. Kliknij **przycisk Dalej** na pierwszej stronie kreatora.

3. Na drugiej stronie kreatora wybierz aplikację, którą chcesz profilować.

   - Aby profilować projekt, który [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]jest aktualnie otwarty, wybierz opcję **Jeden lub więcej dostępnych projektów,** a następnie wybierz nazwę projektu z listy.

   - Aby profilować plik binarny, który nie znajduje się w otwartym projekcie, wybierz **opcję Plik wykonywalny (. exe).**

4. Kliknij przycisk **alej**.

5. Na trzeciej stronie kreatora:

    - Jeśli profilujesz plik wykonywalny, który nie znajduje się w otwartym projekcie, określ ścieżkę do pliku binarnego w **co to jest pełna ścieżka do pliku wykonywalnego**.

    - W przypadku profilowania pliku wykonywalnego, który nie znajduje się w otwartym projekcie, można określić wszystkie argumenty wiersza polecenia, które mają być przerzucene do procesu w **argumentach wiersza polecenia**.

    - W **katalogu pracy zdalnej**określ ścieżkę do folderu, który jest używany przez wystąpienia procesu w poszczególnych węzłach obliczeniowych.

    - W **lokalizacji wdrożenia**określ ścieżkę do katalogu używanego przez serwer HPC do przygotowania obrazów do wdrożenia.

6. Kliknij przycisk **alej**.

7. Na czwartej stronie kreatora:

    - Na liście **Węzeł główny** kliknij komputer, który działa jako węzeł główny HPC w przebiegu profilowania. Węzeł główny może być "localhost", który umożliwia profilowanie na komputerze lokalnym bez konieczności posiadania klastra.

    - Na liście **Liczba procesów** kliknij liczbę wystąpień aplikacji do uruchomienia.

    - Na liście **Opcji profilowania** wybierz cel profilowania.

         Aby profilować określony proces w klastrze, wybierz opcję **Profil na poziomie,** a następnie wybierz rangę procesu z listy rozwijanej.

         Aby profilować proces lub procesy uruchamiane w określonym węźle w klastrze HPC, wybierz opcję **Profil w węźle,** a następnie wybierz węzeł z listy rozwijanej.

8. Kliknij przycisk **alej**.

9. Na piątej stronie kreatora można natychmiast uruchomić profiler i proces profilowania lub rozpocząć profilowanie później przy użyciu Eksploratora wydajności.

    - Wybierz **pozycję Uruchom profilowanie po zakończeniu pracy kreatora,** aby natychmiast rozpocząć profilowanie, lub wyczyść to pole wyboru, aby rozpocząć profilowanie ręcznie.

10. Kliknij przycisk **Zakończ**.

## <a name="set-hpc-profiling-properties-by-using-performance-session-property-pages"></a>Ustawianie właściwości profilowania HPC przy użyciu stron właściwości sesji wydajności

Właściwości sesji wydajności ustawione w Kreatorze profilowania HPC można zmienić na stronie Właściwości uruchamiania HPC na stronie właściwości sesji wydajności. Możesz ustawić dodatkowe opcje na stronie HPC Advanced Properties.

### <a name="to-open-the-performance-session-property-pages"></a>Aby otworzyć strony właściwości sesji wydajności

1. W razie potrzeby otwórz plik sesji wydajności (psess) w Eksploratorze wydajności. W menu **Plik** kliknij polecenie **Otwórz** i znajdź plik.

2. W Eksploratorze wydajności kliknij prawym przyciskiem myszy nazwę sesji wydajności, a następnie kliknij polecenie **Właściwości**.

3. W oknie dialogowym Strony właściwości użyj jednej z następujących metod:

    - Kliknij **pozycję Ogólne,** a następnie wybierz pozycję **Zbieraj w klastrze HPC,** aby włączyć profilowanie HPC lub wyczyścić pole wyboru, aby wyłączyć profilowanie HPC.

    - Kliknij **przycisk Właściwości uruchamiania HPC,** aby zmienić właściwości uruchamiane przez aplikację HPC.

    - Kliknij **przycisk HpC Advanced Properties,** aby ustawić dodatkowe opcje

### <a name="hpc-launch-properties"></a>Właściwości startowe HPC

|Właściwość|Opis|
|--------------|-----------------|
|**Węzeł główny**|Określa komputer, który działa jako węzeł główny HPC w przebiegu profilowania.|
|**Liczba procesów**|Określa liczbę wystąpień aplikacji do uruchomienia w profilowanych aplikacji.|
|**Profil na randze**|Aby profilować określony proces w klastrze, wybierz opcję **Profil na poziomie,** a następnie wybierz rangę procesu z listy rozwijanej.|
|**Profil w węźle**|Aby profilować proces lub procesy uruchamiane w określonym węźle w klastrze HPC, wybierz opcję **Profil w węźle,** a następnie wybierz węzeł z listy rozwijanej.|
|**Katalog pracy zdalnej**|Określa ścieżkę do folderu używanego przez wystąpienia procesów w poszczególnych węzłach obliczeniowych.|
|**Lokalizacja wdrożenia**|Określa ścieżkę do katalogu używanego przez serwer HPC do przygotowania obrazów do wdrożenia.|

### <a name="advanced-properties"></a>Właściwości zaawansowane

| Właściwość | Opis |
|---------------------------------------| - |
| **Nazwa projektu** | Nazwa bieżącego [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] projektu lub rozwiązania. |
| **Czyszczenie po zatrzymaniu profilera** | Gdy true, usuwa pliki binarne, które zostały wdrożone do katalogu wykonywania. Pliki i katalogi utworzone przez program użytkownika nie są usuwane w tym kroku. Jeśli katalog wykonywania i katalog wdrażania zostały utworzone przez IDE, IDE próbuje je usunąć, ale nie robi tego, jeśli mają pliki nie wdrożone przez IDE. |
| **Dodatkowe pliki do wdrożenia** | Określa listę oddzielonych średnikami dodatkowych plików do wdrożenia w węźle obliczeniowym. Możesz kliknąć przycisk wielokropka (**...**), aby wybrać wiele plików za pomocą okna dialogowego. |
| **Mpiexec, polecenie** | Określa aplikację, która uruchamia aplikację MPI. Wartością domyślną jest **mpiexec.exe** |
| **Argumenty Mpiexec** | Określa argumenty, które mają być przesuwające do polecenia mpiexec.exe. |
| **Żądane węzły w klastrze** | Określa liczbę węzłów w klastrze, na których ma być uruchamiana aplikacja. |
| **Wdrażanie plików CRT** | Gdy true, wdraża czas wykonywania języka C/C++ w klastrze. |
| **Skrypt wstępny** | Określa ścieżkę i nazwę pliku skryptu do uruchomienia na lokalnym komputerze deweloperskim przed rozpoczęciem sesji profilowania. |
| **Argumenty skryptu przed profilem** | Określa argumenty, które mają być przesuwają do skryptu pre-profile. |
| **Skrypt postprofilowy** | Określa ścieżkę i nazwę pliku skryptu uruchamianego na lokalnym komputerze deweloperskim po zakończeniu sesji profilowania. |
| **Argumenty skryptu postprofilowego** | Określa argumenty, które mają być przesuwają do skryptu postprofilowego. |
