---
title: Narzędzie wiersza polecenia CONCURRENCY Visualizer (CVCollectionCmd) | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.performance.cvcollectioncmd
ms.assetid: 476601be-1608-4014-af15-5aba6ccbed1c
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4282b865bbe85a70e1565e17987600da5c7960e5
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63444054"
---
# <a name="concurrency-visualizer-command-line-utility-cvcollectioncmd"></a>Narzędzie wiersza polecenia Concurrency Visualizer (CVCollectionCmd)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Narzędzie wiersza polecenia Concurrency Visualizer (CVCollectionCmd.exe) służy do zbierania śladów z wiersza polecenia, aby wyświetlić w Wizualizatorze współbieżności dla programu Visual Studio. Ule może służyć na komputerach, które nie mają zainstalowanego programu Visual Studio.  
  
> [!NOTE]
> Narzędzie Concurrency Visualizer, począwszy od programu Visual Studio 2013 to opcjonalne rozszerzenie. (Wcześniej on miał została uwzględniona w programie Visual Studio.) Możesz pobrać [Concurrency Visualizer Collection Tools for Visual Studio 2015](http://www.microsoft.com/download/details.aspx?id=49103) z Centrum pobierania.  
  
## <a name="download-the-concurrency-visualizer-command-line-utility"></a>Pobierz narzędzie wiersza polecenia Concurrency Visualizer  
 Aby pobrać i zainstalować narzędzia wiersza polecenia, przejdź do [Concurrency Visualizer Collection Tools for Visual Studio 2015](http://www.microsoft.com/download/details.aspx?id=49103) i postępuj zgodnie z instrukcjami. Domyślnie CVCollectionCmd.exe jest zainstalowany w folderze %ProgramFiles%\Microsoft SDKs\Windows\v8.0a\bin\netfx kolekcji wizualizatora współbieżności (% ProgramFiles (x86) %\Microsoft Concurrency Visualizer kolekcji SDKs\Windows\v8.0a\bin\netfx na x64 komputerów).  
  
## <a name="collect-a-trace-with-cvcollectioncmd"></a>Zbierać dane śledzenia z CVCollectionCmd  
 Uruchamianie aplikacji za pomocą CVCollectionCmd lub dołączanie do niego, można zbierać dane śledzenia. Zobacz informacje o poleceniu poniżej dla opcji. Na przykład  
  
```  
<Path>CVCollectionCmd /launch c:\myapp\myapp.exe /outdir c:\myapp\data  
```  
  
## <a name="commands-and-parameters"></a>Polecenia i parametry  
 Aby uzyskać pomoc dotyczącą poleceń i parametrów w narzędziu wiersza polecenia, wpisz to polecenie w wierszu polecenia:  
  
 **CvCollectionCmd /?**  
  
|Opcja|Opis|Parametry|Zwracane wartości|  
|------------|-----------------|----------------|-------------------|  
|Zapytanie|Zwraca, czy można uruchomić kolekcjonowania.|Brak|0, jeśli kolekcja jest gotowy do uruchomienia.<br /><br /> 1, jeśli kolekcja jest już w toku.<br /><br /> 2, jeśli kolekcja nie jest w toku, ale co najmniej wymaganych [ETW](http://msdn.microsoft.com/library/ac99a063-e2d2-40cc-b659-d23c2f783f92) sesji jest włączony.|  
|Uruchom|Uruchamia określony proces w Wizualizatorze współbieżności.|Ścieżka pliku wykonywalnego.|0, jeśli działanie zakończyło się pomyślnie.<br /><br /> 1, jeśli działanie nie powiodło się, ponieważ nie można uruchomić aplikacji docelowej.<br /><br /> 13, jeśli działanie nie powiodło się, ponieważ CVCollectionCmd ma niewystarczające uprawnienia do zapisu w katalogu określonym produktem wyjściowym.|  
|Dołącz|Rozpoczyna się Kolekcjonowanie śladu całego systemu; w przeciwnym razie dołącza do procesu, jeśli mapa została określona.|Brak.|0, jeśli załącznika zakończyło się pomyślnie.<br /><br /> 1, jeśli załącznika nie powiodło się, ponieważ określony proces jest nieprawidłowa lub niejednoznaczna.<br /><br /> 13, jeśli załącznika nie powiodło się, ponieważ CVCollectionCmd ma niewystarczające uprawnienia do zapisu w katalogu określonym produktem wyjściowym.|  
|Odłącz|Zatrzymuje kolekcję.|Brak.|0, jeśli odłączenie zakończyło się pomyślnie.<br /><br /> 1, jeśli odłączenie nie powiodło się, ponieważ kolekcja nie jest obecnie w toku.<br /><br /> 2, jeśli odłączenie nie powiodło się, ponieważ nie można zatrzymać kolekcji.|  
|Analiza|Analizuje określony śledzenia.|Pełna ścieżka pliku CVTrace.|0, jeśli analiza powiodła się.<br /><br /> 1, jeśli analiza nie można uruchomić, ponieważ śledzenia w określonym został całego systemu, ale nie określono żadnego procesu docelowego.<br /><br /> określono wartość 2, jeśli nie można rozpocząć analizy, ponieważ ślad nie był na poziomie systemu i procesu.<br /><br /> 3, jeśli analiza nie powiodła się, ponieważ określony proces jest nieprawidłowy.<br /><br /> 4, jeśli analiza nie powiodła się, ponieważ określony plik CVTrace jest nieprawidłowy.|  
|LaunchArgs|Określa argumenty pliku wykonywalnego docelowego. Ta opcja dotyczy tylko za pomocą polecenia uruchamiania.|Argumenty wiersza polecenia do aplikacji.|Brak.|  
|Outdir|Określa katalog, w której chcesz zapisać pliki śledzenia. Ma zastosowanie do dołączania i uruchamiania poleceń.|Ścieżka katalogu lub ścieżką względną.|Brak.|  
|Proces|Określa proces do dołączenia podczas wykonywania polecenia Attach lub procesu w śladzie do analizowania podczas wykonywania polecenia analizy. Ma zastosowanie do polecenia Attach i analizy.|Identyfikator PID lub nazwę procesu.|Brak.|  
|Konfiguracja|Określa ścieżkę pliku konfiguracji, jeśli chcesz, aby ustawienia kolekcji innych niż domyślne.   Ma zastosowanie do polecenia uruchomienia, Dołącz i analizy.|Ścieżka katalogu lub ścieżka względna pliku konfiguracyjnego XML.|Brak.|  
  
## <a name="customizing-configuration-settings"></a>Dostosowywanie ustawień konfiguracji  
 Jeśli używasz CVCollectionCmd zbierać dane śledzenia, i chcesz dostosować ustawienia kolekcji, a następnie określ je przy użyciu pliku konfiguracji.  
  
> [!NOTE]
> Gdy zbieranie danych śledzenia przy użyciu programu Visual Studio, nie należy bezpośrednio modyfikować pliku konfiguracji.  Zamiast tego należy użyć [Zaawansowane ustawienia](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) okno dialogowe, aby zmodyfikować ustawienia.  
  
 Aby zmodyfikować ustawienia zbierania, należy utworzyć plik konfiguracji na komputerze, w którym będą uruchamiane narzędzie CVCollectionCmd. Plik konfiguracji można utworzyć od podstaw lub można skopiować pliku konfiguracji na komputerze, na którym jest zainstalowany program Visual Studio i zmodyfikować to. Plik `UserConfig.xml` i znajduje się w **lokalnych danych aplikacji** folderu. Po uruchomieniu narzędzia, należy użyć opcji konfiguracji, w połączeniu z polecenia uruchomienia, Dołącz lub analizy.  W parametr, który jest skojarzony z opcją konfiguracji należy określić ścieżkę do pliku konfiguracji.  
  
### <a name="configuration-file-tags"></a>Tagi plików konfiguracji  
 Plik konfiguracji jest oparty na formacie XML. Poniżej przedstawiono prawidłowe tagi i wartości:  
  
|Tag|Opis|Wartości|  
|---------|-----------------|------------|  
|Konfiguracja|Rozgranicza ogólnej pliku konfiguracji.|Musi zawierać następujące elementy:<br /><br /> -MinorVersion<br />-Brak elementu MajorVersion|  
|Brak elementu MajorVersion|Określa wersji głównej pliku konfiguracji.|Musi mieć wartość 1 dla [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] projektów. W przeciwnym razie 1, narzędzie nie będzie działać.|  
|MinorVersion|Określa wersję pomocniczą w pliku konfiguracji.|Musi mieć wartość 0 odpowiadającą [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] projektów. W przeciwnym razie 0, narzędzie nie będzie działać.|  
|IncludeEnvSymbolPath|Ustawia wartość określającą, czy jest używane środowisko ścieżki symboli (_NT_SYMBOL_PATH).|— Wartość true<br />— Wartość false|  
|DeleteEtlsAfterAnalysis|Ustawia wartość określającą, czy pliki ETL są usuwane po zakończeniu analizy.|— Wartość true<br />— Wartość false|  
|SymbolPath|Określa ścieżkę serwera symboli. Aby uzyskać więcej informacji, zobacz [Użyj Microsoft Symbol Server do uzyskania plików symboli debugowania](http://go.microsoft.com/fwlink/?LinkID=149389).|Nazwa katalogu lub adres URL.|  
|Znaczniki|Zawiera listę dostawców znaczników.|Może zawierać zero lub więcej elementów MarkerProvider.|  
|MarkerProvider|Określa dostawcę jednego znacznika.|Musi zawierać następujące elementy:<br /><br /> -Level<br />— IDENTYFIKATOR GUID<br />— Nazwa<br /><br /> Może zawierać następujące elementy:<br /><br /> -Kategorii<br />-IsEnabled|  
|Poziom|Ustawia poziom ważności MarkerProvider.|-Niski<br />-Normalny<br />-Wysoka<br />-Krytyczne<br />— Wszystko|  
|Guid|Globalnie unikatowy identyfikator znacznika dostawcy funkcji ETW.|IDENTYFIKATOR GUID.|  
|Nazwa|Określa opis dostawcę znaczników.|Ciąg.|  
|Kategorie|Określa kategorie zbierane na potrzeby dostawcę znaczników.|Rozdzielana przecinkami ciąg liczb lub zakresy liczb.|  
|isEnabled|Ustawia wartość określającą, czy dostawca znacznika jest włączony dla kolekcji.|— Wartość true<br />— Wartość false|  
|FilterConfig|Określa listę opcji konfiguracji zdarzeń ETW, które zostały przefiltrowane z kolekcji.|Może zawierać następujące elementy:<br /><br /> -CollectClrEvents<br />-ClrCollectionOptions<br />-CollectSampleEvents<br />-CollectGpuEvents<br />-   CollectFileIO|  
|CollectClrEvents|Wartość, która określa, czy są zbierane zdarzenia CLR.|— Wartość true<br />— Wartość false|  
|ClrCollectionOptions|Określa, czy służąca do gromadzenia zdarzeń CLR w przypadku aplikacji natywnych i czy służąca do gromadzenia zdarzeń podsumowania NGEN.|Może zawierać jeden, zarówno lub żadna z tych wartości:<br /><br /> -CollectForNative<br />-DisableNGenRundown|  
|CollectSampleEvents|Ustawia wartość określającą, czy próbkowane zdarzenia są zbierane.|— Wartość true<br />— Wartość false|  
|CollectGpuEvents|Ustawia wartość określającą, czy zdarzenia wygenerowane przez DX są zbierane.|— Wartość true<br />— Wartość false|  
|CollectFileIO|Ustawia wartość określającą, czy są zbierane zdarzenia We/Wy pliku.|— Wartość true<br />— Wartość false|  
|UserBufferSettings|Określa listę parametrów ustawienia bufora użytkownika.|Musi zawierać następujące elementy:<br /><br /> -BufferFlushTimer<br />-BufferSize<br />-MinimumBuffers<br />-MaximumBuffers|  
|KernelBufferSettings|Określa listę parametrów ustawień buforu jądra.|Musi zawierać następujące elementy:<br /><br /> -BufferFlushTimer<br />-BufferSize<br />-MinimumBuffers<br />-MaximumBuffers|  
|BufferFlushTimer|Określa Czasomierz opróżniania buforów ETW.|Dodatnia liczba całkowita.|  
|BufferSize|Ilość pamięci przydzielona do każdego buforu sesji śledzenia zdarzeń, w kilobajtach.|Liczba z przedziału od 0 do 1024.|  
|MinimumBuffers|Minimalna liczba buforów, które są przydzielane dla puli buforów sesji śledzenia zdarzeń.|Dodatnia liczba całkowita większa lub równa dwa razy liczba rdzeni logicznych.|  
|MaximumBuffers|Maksymalna liczba buforów, które są przydzielane dla puli buforów sesji śledzenia zdarzeń.|Liczba większa niż lub równa MinimumBuffers.|  
|JustMyCode|Określa listę katalogów tylko mój kod.|Lista elementów MyCodeDirectory zero lub więcej.|  
|MyCodeDirectory|Określa katalog, który zawiera kod.|Ścieżka bezwzględna.|  
  
### <a name="example"></a>Przykład  
 Zamiast tworzenia pliku konfiguracji, od początku, możesz skopiować poniższy przykład, a następnie zmodyfikuj je zgodnie z wymaganiami.  
  
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
