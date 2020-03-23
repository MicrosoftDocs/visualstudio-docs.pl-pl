---
title: Narzędzie wiersza polecenia wizualizatora współbieżności (CVCollectionCmd) | Dokumenty firmy Microsoft
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
ms.openlocfilehash: 2721798ee9f0c7e006acdedbecaecbd56068be3f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "72911206"
---
# <a name="concurrency-visualizer-command-line-utility-cvcollectioncmd"></a>Narzędzie wiersza polecenia wizualizatora współbieżności (CVCollectionCmd)
Narzędzie wiersza polecenia Wizualizatora współbieżności (*CVCollectionCmd.exe*) służy do zbierania śladów z wiersza polecenia, dzięki czemu można je wyświetlić w wizualizatorze współbieżności dla programu Visual Studio. Narzędzia mogą być używane na komputerach, które nie mają zainstalowanego programu Visual Studio.

> [!NOTE]
> Począwszy od programu Visual Studio 2013 wizualizator współbieżności jest rozszerzeniem opcjonalnym. (Wcześniej został on uwzględniony w programie Visual Studio. Narzędzia do [zbierania wizualizatora współbieżności dla programu Visual Studio 2015](https://www.microsoft.com/download/details.aspx?id=49103) można pobrać z Centrum pobierania.

## <a name="download-the-concurrency-visualizer-command-line-utility"></a>Pobierz narzędzie wiersza polecenia Wizualizator współbieżności
 Aby pobrać i zainstalować narzędzie wiersza polecenia, przejdź do [narzędzia do zbierania narzędzi współbieżności visualizer dla programu Visual Studio 2015](https://www.microsoft.com/download/details.aspx?id=49103) i postępuj zgodnie z instrukcjami. Domyślnie *program CVCollectionCmd.exe* jest instalowany w programie %ProgramFiles%\Microsoft Concurrency Visualizer Collection Tools\ (%ProgramFiles(x86)%\Microsoft Concurrency Visualizer Collection Tools\ na komputerach x64).

## <a name="collect-a-trace-with-cvcollectioncmd"></a>Zbierz ślad z CVCollectionCmd
 Można zebrać śledzenia, uruchamiając aplikację z CVCollectionCmd lub dołączając do niego. Opcje można znaleźć w poniższym poleceniu. Na przykład:

```cmd
<Path>CVCollectionCmd /launch c:\myapp\myapp.exe /outdir c:\myapp\data
```

## <a name="commands-and-parameters"></a>Polecenia i parametry
 Aby uzyskać pomoc dotyczącą poleceń i parametrów w narzędziu wiersza polecenia, wpisz to w wierszu polecenia:

 **CvCollectionCmd /?**

|Opcja|Opis|Parametry|Zwracane wartości|
|------------|-----------------|----------------|-------------------|
|Zapytanie|Zwraca, czy można uruchomić kolekcję.|Brak|0, jeśli kolekcja jest gotowa do uruchomienia.<br /><br /> 1, jeśli kolekcja jest już w toku.<br /><br /> 2 jeśli kolekcja nie jest w toku, ale co najmniej jedna z wymaganych sesji [ETW](/dotnet/framework/wcf/samples/etw-tracing) jest już włączona.|
|Uruchom|Uruchamia określony proces w obszarze Wizualizator współbieżności.|Ścieżka pliku wykonywalnego.|0, jeśli bieg się powiódł.<br /><br /> 1, jeśli uruchomienie nie powiodło się, ponieważ nie można uruchomić aplikacji docelowej.<br /><br /> 13, jeśli uruchomienie nie powiodło się, ponieważ CVCollectionCmd ma niewystarczające uprawnienia do zapisu w określonym katalogu wyjściowym.|
|Attach|Rozpoczyna zbieranie śledzenia całego systemu; w przeciwnym razie dołącza do procesu, jeśli jest określony.|Brak.|0, jeśli załącznik się powiódł.<br /><br /> 1, jeśli załącznik nie powiódł się, ponieważ określony proces jest nieprawidłowy lub niejednoznaczny.<br /><br /> 13, jeśli załącznik nie powiódł się, ponieważ CVCollectionCmd ma niewystarczające uprawnienia do zapisu w określonym katalogu wyjściowym.|
|Detach|Zatrzymuje kolekcję.|Brak.|0, jeśli oddział się powiódł.<br /><br /> 1 jeśli odłączenie nie powiodło się, ponieważ kolekcja nie jest obecnie w toku.<br /><br /> 2 jeśli odłączenie nie powiodło się, ponieważ nie można zatrzymać kolekcji.|
|Analiza|Analizuje określony ślad.|Pełna ścieżka pliku CVTrace.|0, jeśli analiza powiodła się.<br /><br /> 1, jeśli analiza nie może się rozpocząć, ponieważ określony ślad był w całym systemie, ale nie określono procesu docelowego.<br /><br /> 2, jeśli analiza nie może się rozpocząć, ponieważ śledzenia nie był systemowy i określono proces.<br /><br /> 3, jeśli analiza nie powiodła się, ponieważ określony proces jest nieprawidłowy.<br /><br /> 4 jeśli analiza nie powiodła się, ponieważ określony plik CVTrace jest nieprawidłowy.|
|LaunchArgs (LaunchArgs)|Określa docelowe argumenty wykonywalne. Ta opcja dotyczy tylko polecenia Uruchom.|Argumenty wiersza polecenia do aplikacji.|Brak.|
|Outdir|Określa katalog, w którym mają być zapisywane pliki śledzenia. Dotyczy poleceń Uruchom i Dołącz.|Ścieżka katalogu lub ścieżka względna.|Brak.|
|Proces|Określa proces dołączania do po wykonaniu polecenia Dołącz lub proces w śledzeniu do analizy podczas wykonywania polecenia Analizuj. Dotyczy poleceń Dołącz i Analizuj.|Pid lub nazwę procesu.|Brak.|
|Config|Określa ścieżkę pliku konfiguracyjnego, jeśli chcesz, aby ustawienia kolekcji były inne niż ustawienia domyślne.   Dotyczy poleceń Uruchom, Dołącz i Analizuj.|Ścieżka katalogu lub ścieżka względna pliku konfiguracyjnego XML.|Brak.|

## <a name="customize-configuration-settings"></a>Dostosowywanie ustawień konfiguracji
 Jeśli używasz CVCollectionCmd do zbierania śladów i chcesz dostosować ustawienia kolekcji, a następnie użyj pliku konfiguracji, aby je określić.

> [!NOTE]
> Korzystając z programu Visual Studio do zbierania śladów, nie należy bezpośrednio modyfikować pliku konfiguracji.  Zamiast tego użyj okna dialogowego [Ustawienia zaawansowane,](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) aby zmodyfikować ustawienia.

 Aby zmodyfikować ustawienia kolekcji, należy utworzyć plik konfiguracyjny na komputerze, na którym zostanie uruchomione narzędzie CVCollectionCmd. Można utworzyć plik konfiguracyjny od podstaw lub skopiować plik konfiguracyjny na komputerze, na który jest zainstalowany program Visual Studio i zmodyfikować go. Plik nosi nazwę *UserConfig.xml* i znajduje się w folderze *Local AppData.* Po uruchomieniu narzędzia użyj opcji Konfiguruj w połączeniu z poleceniem Uruchom, Dołącz lub Analizuj.  W parametrze skojarzonym z opcją Config określ ścieżkę pliku konfiguracyjnego.

### <a name="configuration-file-tags"></a>Znaczniki plików konfiguracji
 Plik konfiguracyjny jest oparty na języku XML. Oto prawidłowe tagi i wartości:

| Tag | Opis | Wartości |
|-------------------------| - | - |
| Config | Wyznacza ogólny plik konfiguracyjny. | Musi zawierać następujące elementy:<br /><br /> - MinorVersion<br />- MajorVersion |
| MajorVersion (Wersja główna) | Określa główną wersję pliku konfiguracyjnego. | Musi być 1 dla [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] projektów. Jeśli nie 1, narzędzie nie będzie działać. |
| MinorVersion (Wersja pomocnicza) | Określa pomocniczą wersję pliku konfiguracyjnego. | Musi być 0 dla [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] projektów. Jeśli nie 0, narzędzie nie będzie działać. |
| Ścieżka InsymbolPath IncludeEnvSymbolPath | Ustawia wartość, która określa, czy używana jest ścieżka symbolu środowiska (_NT_SYMBOL_PATH). | - Prawda<br />- Fałsz |
| DeleteEtlsPoanalizie | Ustawia wartość, która określa, czy pliki ETL są usuwane po zakończeniu analizy. | - Prawda<br />- Fałsz |
| Ścieżka symboli | Określa ścieżkę serwera symboli. Aby uzyskać więcej informacji, zobacz [Korzystanie z serwera symboli firmy Microsoft w celu uzyskania plików symboli debugowania](/windows/win32/dxtecharts/debugging-with-symbols). | Nazwa katalogu lub adres URL. |
| Znaczniki | Zawiera listę dostawców znaczników. | Może zawierać zero lub więcej MarkerProvider elementów. |
| MarkerProvider | Określa jednego dostawcę znaczników. | Musi zawierać następujące elementy:<br /><br /> - Poziom<br />- Identyfikator GUID<br />- Imię i nazwisko<br /><br /> Może zawierać następujące elementy:<br /><br /> - Kategorie<br />- IsEnabled |
| Poziom | Ustawia poziom ważności MarkerProvider. | - Niski<br />- Normalne<br />- Wysoka<br />- Krytyczne<br />- Wszystko |
| Guid (identyfikator GUID) | Unikatowy na skalę globalną identyfikator dostawcy znaczników ETW. | Identyfikator GUID. |
| Nazwa | Określa opis dostawcy znaczników. | Ciąg. |
| Kategorie | Określa kategorie zebrane dla dostawcy znaczników. | Ciąg liczb lub zakresów liczb rozdzielanych przecinkami. |
| IsEnabled | Ustawia wartość, która określa, czy dostawca znaczników jest włączony dla kolekcji. | - Prawda<br />- Fałsz |
| FiltrConfig | Określa listę opcji konfiguracji zdarzeń ETW, które są filtrowane z kolekcji. | Może zawierać następujące elementy:<br /><br /> - CollectClrEvents<br />- ClrCollectionOptions<br />- CollectSampleEvents<br />- CollectGpuEvents<br />- CollectFileIO |
| CollectClrEvents | Ustaw wartość, która określa, czy zdarzenia CLR są zbierane. | - Prawda<br />- Fałsz |
| ClrCollectionOptions | Określa, czy mają być zbierane zdarzenia CLR dla aplikacji natywnych i czy zbierać zdarzenia wybiegiem NGEN. | Może zawierać jedną, obie lub żadną z tych wartości:<br /><br /> - CollectForNative<br />- DisableNGenRundown |
| CollectSampleEvents | Ustawia wartość, która określa, czy zdarzenia próbki są zbierane. | - Prawda<br />- Fałsz |
| CollectGpuEvents | Ustawia wartość, która określa, czy zdarzenia generowane przez DX są zbierane. | - Prawda<br />- Fałsz |
| CollectFileIO | Ustawia wartość, która określa, czy zdarzenia we/wy pliku są zbierane. | - Prawda<br />- Fałsz |
| Ustawienia userbuffersettings | Określa listę parametrów ustawień buforu użytkownika. | Musi zawierać następujące elementy:<br /><br /> - BufferFlushTimer<br />- Rozmiar bufora<br />- MinimumBuffers<br />- MaximumBuffers |
| JądroBufferSettings | Określa listę parametrów ustawień buforu jądra. | Musi zawierać następujące elementy:<br /><br /> - BufferFlushTimer<br />- Rozmiar bufora<br />- MinimumBuffers<br />- MaximumBuffers |
| BufferFlushTimer | Określa czasomierz opróżniania buforów ETW. | Dodatnia wartość całkowita. |
| Buffersize | Ilość pamięci, która jest alokowana dla każdego buforu sesji śledzenia zdarzeń w kilobajtach. | Liczba od 0 do 1024. |
| Minimalnebuffers | Minimalna liczba buforów, które są przydzielane dla puli buforów sesji śledzenia zdarzeń. | Dodatnia liczba całkowita większa lub równa dwukrotności liczby rdzeni logicznych. |
| Maksymalnebuffery | Maksymalna liczba buforów, które są przydzielane dla puli buforów sesji śledzenia zdarzeń. | Liczba większa lub równa MinimumBuffers. |
| Kod JustMy | Określa listę katalogów Just My Code. | Lista zero lub więcej elementów MyCodeDirectory. |
| MyCodeDirectory (MyCodeDirectory) | Określa katalog zawierający kod. | Ścieżka absolutna. |

### <a name="example"></a>Przykład
 Zamiast tworzyć plik konfiguracji od początku, można skopiować poniższy przykład, a następnie zmodyfikować go, aby spełnić wymagania.

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
