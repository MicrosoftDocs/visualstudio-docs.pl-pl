---
title: Narzędzie wiersza polecenia wizualizatora współbieżności
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.performance.cvcollectioncmd
ms.assetid: 476601be-1608-4014-af15-5aba6ccbed1c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 762a3563e64a3437c34b9e12e372f5d578e0c7ac
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808906"
---
# <a name="concurrency-visualizer-command-line-utility-cvcollectioncmd"></a>Narzędzie wiersza polecenia Concurrency Visualizer (CVCollectionCmd)
Za pomocą narzędzia wiersza polecenia wizualizatora współbieżności (*CVCollectionCmd.exe*) można zbierać ślady z wiersza polecenia, aby można było je wyświetlić w wizualizatorze współbieżności dla programu Visual Studio. Narzędzia te mogą być używane na komputerach, na których nie zainstalowano programu Visual Studio.

> [!NOTE]
> Począwszy od Visual Studio 2013, Wizualizator współbieżności jest opcjonalnym rozszerzeniem. (Poprzednio został on uwzględniony w programie Visual Studio). [Narzędzia do zbierania danych Concurrency Visualizer dla programu Visual Studio 2015](https://www.microsoft.com/download/details.aspx?id=49103) można pobrać z centrum pobierania.

## <a name="download-the-concurrency-visualizer-command-line-utility"></a>Pobierz narzędzie wiersza polecenia wizualizatora współbieżności
 Aby pobrać i zainstalować narzędzie wiersza polecenia, przejdź do narzędzia do [zbierania danych Concurrency Visualizer dla programu Visual Studio 2015](https://www.microsoft.com/download/details.aspx?id=49103) i postępuj zgodnie z instrukcjami. Domyślnie *CVCollectionCmd.exe* jest zainstalowana w narzędziach kolekcji%ProgramFiles%\Microsoft concurrency wizualizatora \ (% ProgramFiles (x86)% \ narzędzia kolekcji Microsoft Concurrency Visualizer \ na komputerach x64.

## <a name="collect-a-trace-with-cvcollectioncmd"></a>Zbierz ślad z CVCollectionCmd
 Można zbierać ślady, uruchamiając aplikację z CVCollectionCmd lub dołączając do niej. Zapoznaj się z poleceniem poniżej, aby poznać odpowiednie opcje. Na przykład

```cmd
<Path>CVCollectionCmd /launch c:\myapp\myapp.exe /outdir c:\myapp\data
```

## <a name="commands-and-parameters"></a>Polecenia i parametry
 Aby uzyskać pomoc dotyczącą poleceń i parametrów w narzędziu wiersza polecenia, wpisz w wierszu polecenia:

 **CvCollectionCmd/?**

|Opcja|Opis|Parametry|Wartości zwracane|
|------------|-----------------|----------------|-------------------|
|Zapytanie|Zwraca czy można rozpocząć zbieranie danych.|Brak|0, jeśli zbieranie danych jest gotowe do rozpoczęcia.<br /><br /> 1, jeśli kolekcja jest już w toku.<br /><br /> 2 Jeśli kolekcja nie jest w toku, ale co najmniej jedna z wymaganych sesji [ETW](/dotnet/framework/wcf/samples/etw-tracing) jest już włączona.|
|Uruchom|Uruchamia określony proces w ramach wizualizatora współbieżności.|Ścieżka pliku wykonywalnego.|0, Jeśli uruchomienie zakończyło się pomyślnie.<br /><br /> 1 Jeśli uruchomienie nie powiodło się, ponieważ nie można uruchomić aplikacji docelowej.<br /><br /> 13 Jeśli uruchomienie nie powiodło się, ponieważ CVCollectionCmd ma niewystarczające uprawnienia do zapisu w określonym katalogu wyjściowym.|
|Dołącz|Rozpoczyna zbieranie śladów całego systemu; w przeciwnym razie dołącza do procesu, jeśli został określony.|Brak.|0, jeśli załącznik zakończył się pomyślnie.<br /><br /> 1 Jeśli załącznik nie powiódł się, ponieważ określony proces jest nieprawidłowy lub niejednoznaczny.<br /><br /> 13 Jeśli załącznik nie powiódł się, ponieważ CVCollectionCmd ma niewystarczające uprawnienia do zapisu w określonym katalogu wyjściowym.|
|Odłącz|Kończy zbieranie.|Brak.|0 w przypadku pomyślnego odłączenia.<br /><br /> 1 Jeśli odłączenie nie powiodło się, ponieważ kolekcja nie jest obecnie w toku.<br /><br /> 2 Jeśli odłączenie nie powiodło się, ponieważ nie można zatrzymać kolekcjonowania.|
|Analiza|Analizuje określony ślad.|Pełna ścieżka pliku CVTrace.|0, jeśli analiza powiodła się.<br /><br /> 1 Jeśli nie można rozpocząć analizy, ponieważ określony ślad dotyczył całego systemu, ale żaden proces docelowy nie został określony.<br /><br /> 2 Jeśli nie można rozpocząć analizy, ponieważ ślad nie był na poziomie systemu i został określony proces.<br /><br /> 3 Jeśli analiza nie powiodła się, ponieważ określony proces jest nieprawidłowy.<br /><br /> 4 Jeśli analiza nie powiodła się, ponieważ określony plik CVTrace jest nieprawidłowy.|
|LaunchArgs|Określa docelowe argumenty pliku wykonywalnego. Ta opcja ma zastosowanie tylko do polecenia Uruchom.|Argumenty wiersza polecenia do aplikacji.|Brak.|
|OutDir|Określa katalog, w którym mają zostać zapisane pliki śledzenia. Dotyczy poleceń uruchamiania i dołączania.|Ścieżka katalogu lub ścieżka względna.|Brak.|
|Proces|Określa proces dołączania po wykonaniu polecenia Attach lub proces w śladach do analizy podczas wykonywania polecenia Analizuj. Dotyczy poleceń Attach i Analizuj.|Identyfikator PID lub nazwa procesu.|Brak.|
|Config|Określa ścieżkę pliku konfiguracji, jeśli chcesz, aby ustawienia kolekcji były inne niż domyślne.   Dotyczy poleceń uruchamiania, dołączania i analizowania.|Ścieżka katalogu lub względna ścieżka pliku konfiguracyjnego XML.|Brak.|

## <a name="customize-configuration-settings"></a>Dostosuj ustawienia konfiguracji
 Jeśli używasz CVCollectionCmd do zbierania śladów i chcesz dostosować ustawienia kolekcji, użyj pliku konfiguracji, aby je określić.

> [!NOTE]
> Gdy używasz programu Visual Studio do zbierania śladów, nie Modyfikuj bezpośrednio pliku konfiguracji.  Zamiast tego użyj okna dialogowego [Ustawienia zaawansowane](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) , aby zmodyfikować ustawienia.

 Aby zmodyfikować ustawienia kolekcji, Utwórz plik konfiguracji na komputerze, na którym zostanie uruchomione narzędzie CVCollectionCmd. Plik konfiguracji można utworzyć od podstaw lub skopiować plik konfiguracyjny na komputerze, na którym jest zainstalowany program Visual Studio i zmodyfikować go. Plik ma nazwę *UserConfig.xml* i znajduje się w lokalnym folderze *AppData* . Po uruchomieniu narzędzia Użyj opcji konfiguracji w połączeniu z poleceniem uruchamiania, dołączania lub analizowania.  W parametrze, który jest skojarzony z opcją konfiguracji, określ ścieżkę do pliku konfiguracji.

### <a name="configuration-file-tags"></a>Tagi pliku konfiguracji
 Plik konfiguracji jest oparty na języku XML. Oto prawidłowe Tagi i wartości:

| Tag | Opis | Wartości |
|-------------------------| - | - |
| Config | Rozgranicza ogólny plik konfiguracji. | Musi zawierać następujące elementy:<br /><br /> - MinorVersion<br />-MajorVersion |
| MajorVersion | Określa wersję główną pliku konfiguracyjnego. | Dla projektów musi być 1 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] . Jeśli nie, narzędzie nie będzie działało. |
| MinorVersion | Określa wersję pomocniczą pliku konfiguracyjnego. | Musi mieć wartość 0 dla [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] projektów. Jeśli nie jest równa 0, narzędzie nie będzie działało. |
| IncludeEnvSymbolPath | Ustawia wartość określającą, czy jest używana ścieżka symboli środowiska (_NT_SYMBOL_PATH). | -True<br />-FAŁSZ |
| DeleteEtlsAfterAnalysis | Ustawia wartość określającą, czy pliki ETL zostaną usunięte po zakończeniu analizy. | -True<br />-FAŁSZ |
| SymbolPath — | Określa ścieżkę serwera symboli. Aby uzyskać więcej informacji, zobacz [Korzystanie z serwera symboli firmy Microsoft w celu uzyskania plików symboli debugowania](/windows/win32/dxtecharts/debugging-with-symbols). | Nazwa lub adres URL katalogu. |
| Znaczniki | Zawiera listę dostawców znaczników. | Może zawierać zero lub więcej elementów MarkerProvider. |
| MarkerProvider | Określa dostawcę pojedynczego znacznika. | Musi zawierać następujące elementy:<br /><br /> -Poziom<br />-Identyfikator GUID<br />-Nazwa<br /><br /> Może zawierać następujące elementy:<br /><br /> -Kategorie<br />-IsEnabled |
| Poziom | Ustawia poziom ważności MarkerProvider. | — Niska<br />-Normalny<br />— Wysoka<br />-Krytyczny<br />— Wszystko |
| Guid (identyfikator GUID) | Unikatowy identyfikator globalny dostawcy znaczników ETW. | IDENTYFIKATOR GUID. |
| Nazwa | Określa opis dostawcy znaczników. | Ciąg. |
| Kategorie | Określa kategorie zebrane dla dostawcy znaczników. | Rozdzielany przecinkami ciąg liczb lub zakresów liczb. |
| IsEnabled | Ustawia wartość określającą, czy dostawca znacznika jest włączony dla kolekcji. | -True<br />-FAŁSZ |
| FilterConfig | Określa listę opcji konfiguracji zdarzeń ETW, które są filtrowane z kolekcji. | Może zawierać następujące elementy:<br /><br /> - CollectClrEvents<br />- ClrCollectionOptions<br />- CollectSampleEvents<br />- CollectGpuEvents<br />- CollectFileIO |
| CollectClrEvents | Ustaw wartość określającą, czy są zbierane zdarzenia środowiska CLR. | -True<br />-FAŁSZ |
| ClrCollectionOptions | Określa, czy mają być zbierane zdarzenia środowiska CLR dla aplikacji natywnych oraz czy mają być zbierane zdarzenia dotyczące uwalniania NGEN. | Może zawierać jedną z następujących wartości:<br /><br /> - CollectForNative<br />- DisableNGenRundown |
| CollectSampleEvents | Ustawia wartość określającą, czy będą zbierane Przykładowe zdarzenia. | -True<br />-FAŁSZ |
| CollectGpuEvents | Ustawia wartość określającą, czy zdarzenia generowane przez DX są zbierane. | -True<br />-FAŁSZ |
| CollectFileIO | Ustawia wartość określającą, czy zbierane są zdarzenia we/wy pliku. | -True<br />-FAŁSZ |
| UserBufferSettings | Określa listę parametrów ustawień buforu użytkownika. | Musi zawierać następujące elementy:<br /><br /> - BufferFlushTimer<br />-BufferSize<br />- MinimumBuffers<br />- MaximumBuffers |
| KernelBufferSettings | Określa listę parametrów dla ustawień buforu jądra. | Musi zawierać następujące elementy:<br /><br /> - BufferFlushTimer<br />-BufferSize<br />- MinimumBuffers<br />- MaximumBuffers |
| BufferFlushTimer | Określa czasomierz opróżniania buforów ETW. | Dodatnia liczba całkowita. |
| BufferSize | Ilość pamięci przydzieloną dla każdego buforu sesji śledzenia zdarzeń w kilobajtach. | Liczba z przewartości od 0 do 1024. |
| MinimumBuffers | Minimalna liczba buforów przyznanych dla puli buforów sesji śledzenia zdarzeń. | Dodatnia liczba całkowita większa lub równa podwójnej liczbie rdzeni logicznych. |
| MaximumBuffers | Maksymalna liczba buforów przyznanych dla puli buforów sesji śledzenia zdarzeń. | Liczba większa niż lub równa MinimumBuffers. |
| JustMyCode | Określa listę katalogów Tylko mój kod. | Lista elementów MyCodeDirectory, które są równe zero lub więcej. |
| MyCodeDirectory | Określa katalog, który zawiera kod. | Ścieżka bezwzględna. |

### <a name="example"></a>Przykład
 Zamiast tworzyć plik konfiguracji od początku, można skopiować Poniższy przykład, a następnie zmodyfikować go w celu spełnienia wymagań.

```xml
<?xml version="1.0"?>
<LocalConfig xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" MajorVersion="1" MinorVersion="0">

  <IncludeEnvSymbolPath>true</IncludeEnvSymbolPath>

  <DeleteEtlsAfterAnalysis>true</DeleteEtlsAfterAnalysis>

  <TraceLocation>C:\traces</TraceLocation>

  <SymbolPath>http://symweb</SymbolPath>

  <Markers>
    <MarkerProvider Name="Default" Guid="8d4925ab-505a-483b-a7e0-6f824a07a6f0" Level="Low" />
    <MarkerProvider Name="TPL" Guid="2e5dba47-a3d2-4d16-8ee0-6671ffdcd7b5" Level="Normal" />
    <MarkerProvider Name="TPL Dataflow" Guid="16f53577-e41d-43d4-b47e-c17025bf4025" Level="Normal" />
    <MarkerProvider Name="TPL Synchronization" Guid="ec631d38-466b-4290-9306-834971ba0217" Level="Normal" />
    <MarkerProvider Name="PLINQ" Guid="159eeeec-4a14-4418-a8fe-faabcd987887" Level="Normal" />
    <MarkerProvider Name="Concurrency Runtime" Guid="f7b697a3-4db5-4d3b-be71-c4d284e6592f" Level="Normal" />
    <MarkerProvider Name="Scenario Markers" Guid="fb9244c9-f23a-4966-8a9c-97a51f8c355b" Level="Low" />

    <!-- The IsEnabled and Categories elements are optional -->
    <MarkerProvider Name="myMarker1" Guid="d0dbb3a3-895c-4ce6-96d9-28f69d664dc3" Level="Critical" IsEnabled="false" Categories="0,1,3-5,8" />
    <MarkerProvider Name="myMarker2" Guid="03452127-a617-4302-9e30-c0d10442e4ee" Level="Low" IsEnabled="false" Categories="0,1,3-5,8-10,11-13" />
  </Markers>

  <FilterConfig>
    <CollectClrEvents>true</CollectClrEvents>
    <ClrCollectionOptions>CollectForNative DisableNGenRundown</ClrCollectionOptions>
    <CollectSampleEvents>true</CollectSampleEvents>
    <CollectGpuEvents>true</CollectGpuEvents>
    <CollectFileIO>true</CollectFileIO>
  </FilterConfig>

  <UserBufferSettings>
    <BufferFlushTimer>0</BufferFlushTimer>
    <BufferSize>256</BufferSize>
    <MinimumBuffers>512</MinimumBuffers>
    <MaximumBuffers>1024</MaximumBuffers>
  </UserBufferSettings>

  <KernelBufferSettings>
    <BufferFlushTimer>0</BufferFlushTimer>
    <BufferSize>256</BufferSize>
    <MinimumBuffers>512</MinimumBuffers>
    <MaximumBuffers>1024</MaximumBuffers>
  </KernelBufferSettings>

  <!-- List of MyCodeDirectory directories -->
  <JustMyCode>
    <MyCodeDirectory>C:\myBinaries1</MyCodeDirectory>
    <MyCodeDirectory>C:\myBinaries2</MyCodeDirectory>
  </JustMyCode>
</LocalConfig>

```
