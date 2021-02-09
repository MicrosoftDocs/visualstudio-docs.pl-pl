---
title: Narzędzie do przechwytywania Command-Line | Microsoft Docs
description: Dowiedz się więcej na temat DXCap.exe, narzędzia wiersza polecenia do przechwytywania i odtwarzania diagnostyki grafiki, które obsługuje program Direct3D 10 za pośrednictwem programu Direct3D 12 na wszystkich poziomach funkcji.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: db75b3a7-80b2-4a74-91d2-fd6e0f73b45d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ee7acfd6256affee7a8204c2e70e18210c5f3dcf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877736"
---
# <a name="command-line-capture-tool"></a>Narzędzie wiersza polecenia do przechwytywania
DXCap.exe to narzędzie wiersza polecenia do przechwytywania i odtwarzania diagnostyki grafiki. Obsługuje ona program Direct3D 10 za pośrednictwem Direct3D 12 na wszystkich poziomach funkcji.

## <a name="syntax"></a>Składnia

```cmd
DXCap.exe [-file filename] [-frame frames | -period periods | -manual] -c app [args...]
DXCap.exe -p [filename] [-debug | -warp | -hw] [-config] [-rawmode]
DXCap.exe -p [filename] -screenshot [-frame frames]
DXCap.exe -p [filename] -toXML [xml_filename]
DXCap.exe -v [-file filename] [-examine events] [-haltonfail | -exitonfail] [-showprogress]
DXCap.exe -e [search_string]
DXCap.exe -info
```

#### <a name="parameters"></a>Parametry
 `-file``filename`W obszarze Tryb przechwytywania ( `-c` ) `filename` określa nazwę pliku dziennika grafiki, do którego są rejestrowane informacje o grafice. Jeśli `filename` nie zostanie określony, informacje o grafice są rejestrowane w pliku o nazwie `<appname>-<date>-<time>.vsglog` domyślnie.

 W obszarze Tryb walidacji (-v) `filename` określa nazwę pliku dziennika grafiki do zweryfikowania. Jeśli `filename` nie zostanie określony, zostanie użyty ponownie dziennik grafiki, który został ostatnio sprawdzony.

 `-frame``frames`W obszarze Tryb przechwytywania `frames` określa ramki, które mają być przechwytywane. Pierwsza klatka to 1. Możesz określić kilka ramek przy użyciu przecinków i zakresów. Na przykład, jeśli `frames` jest `2, 5, 7-9, 15` , ramki `2` ,,,, `5` `7` `8` `9` , i `15` są przechwytywane.

> [!TIP]
> Użyj, `-frame` `manual` Aby określić, że ramki będą przechwytywane ręcznie przez naciśnięcie klawisza Print Screen. Ramki mogą być przechwytywane podczas uruchamiania aplikacji; Aby zatrzymać przechwytywanie ramek, Wróć do interfejsu wiersza polecenia i naciśnij klawisz ENTER.

 `-period``periods`W obszarze Tryb przechwytywania `periods` określa zakresy czasu (w sekundach), w ciągu którego mają być przechwytywane ramki. Możesz określić kilka okresów, używając przecinków i zakresów. Na przykład `periods` , jeśli jest `2.1-5, 7.0-9.3` , ramki, które są renderowane między `2.1` i `5` sekund, i między `7` i `9.3` sekund są przechwytywane.

 `-c``app`[ `args...` ] Tryb przechwytywania. W obszarze Tryb przechwytywania `app` określa nazwę aplikacji, z której mają być przechwytywane informacje graficzne; `args...` określa dodatkowe parametry wiersza polecenia dla tej aplikacji.

 `-p` [ `filename` ] Tryb odtwarzania ( `-p` ). W obszarze Tryb odtwarzania `filename` określa nazwę pliku dziennika grafiki, który ma być odtwarzany. Jeśli `filename` nie zostanie określony, ponownie zostanie użyty dziennik grafiki, który został ostatnio odtworzony z powrotem.

 `-debug` W obszarze Tryb odtwarzania `-debug` określa, że odtwarzanie ma być odtwarzane przy włączonej warstwie debugowania Direct3D.

 `-warp` W obszarze Tryb odtwarzania program `-warp` określa, że odtwarzanie powinno być odtwarzane przy użyciu modułu renderowania oprogramowania.

 `-hw` W obszarze Tryb odtwarzania program `-hw` określa, że odtwarzanie ma być odtwarzane przy użyciu sprzętu procesora GPU.

 `-config` W obszarze Tryb odtwarzania `-config` wyświetla wszystkie informacje o komputerze, który został użyty do przechwycenia pliku dziennika grafiki.

 `-rawmode` W obszarze Tryb odtwarzania program `-rawmode` określa, że odtwarzanie ma być wykonywane bez konieczności modyfikacji zarejestrowanych zdarzeń. W przypadku normalnego działania tryb odtwarzania może wprowadzać drobne zmiany w celu uproszczenia debugowania i przyspieszenia odtwarzania. Na przykład może symulować wyjście łańcucha wymiany zamiast wykonywać polecenia zamiany łańcucha. Zwykle to odtwarzanie nie jest problemem, ale może być konieczne odtwarzanie w taki sposób, aby miało miejsce w taki sposób, że rejestrowane zdarzenie. Można na przykład użyć tej opcji, aby przywrócić zachowanie renderowania pełnego ekranu do aplikacji, która została przechwycona podczas działania w trybie pełnoekranowym.

 `-toXML` [ `xml_filename` ] W obszarze Tryb odtwarzania `xml_filename` określa nazwę pliku, w którym jest zapisywana Reprezentacja XML odtwarzania. Jeśli `xml_filename` nie jest określony, Reprezentacja XML jest zapisywana w pliku o nazwie takiej samej jak plik, który jest odtwarzany z powrotem, ale ma `.xml` rozszerzenie.

 `-v` Tryb walidacji. W trybie walidacji przechwycone ramki są odtwarzane na sprzęcie i OSNOWie, a ich wyniki są porównywane przy użyciu funkcji porównywania obrazu. Za pomocą tej funkcji można szybko identyfikować problemy z sterownikiem, które wpływają na renderowanie.

 `-examine``events`W obszarze Tryb walidacji `events` określa zestaw zdarzeń graficznych, których bezpośrednie wyniki są porównywane. Na przykład `-examine present,draw,copy,clear` ogranicza porównanie tylko do zdarzeń należących do tych kategorii.

> [!TIP]
> Zalecamy rozpoczęcie od `-examine present,draw,copy,clear` , ponieważ spowoduje to ujawnienie większości problemów, ale zajmuje znacznie mniej czasu niż bardziej obszerny zestaw zdarzeń. W razie potrzeby można określić większy lub różny zbiór zdarzeń, aby zweryfikować te zdarzenia i ujawnić inne rodzaje problemów.

 `-haltonfail` W obszarze Tryb walidacji `-haltonfail` zatrzymuje sprawdzanie poprawności w przypadku wykrycia różnic między sprzętem a renderowaniem. Weryfikacja zostanie wznowiona po naciśnięciu klawisza.

 `-exitonfail` W obszarze Tryb walidacji program `-exitonfail` natychmiast kończy sprawdzanie poprawności w przypadku wykrycia różnic między sprzętem a renderowaniem. Gdy program zostanie zakończony w ten sposób, powróci `0` do środowiska; w przeciwnym razie zwraca `1` .

 `-showprogress` W obszarze Tryb walidacji `-showprogress` wyświetla informacje o postępie sesji walidacji. Postęp ZNIEKSZTAŁCAnia jest wyświetlany po lewej stronie; po prawej stronie jest wyświetlany postęp sprzętowy.

 `-e``search_string`Wylicza zainstalowane aplikacje platformy UWP. Te informacje służą do wykonywania przechwycenia wiersza polecenia za pomocą aplikacji platformy UWP.

 `-info` Wyświetla informacje o maszynie i przechwytywania bibliotek DLL.

## <a name="remarks"></a>Uwagi
 DXCap.exe działa w trzech trybach:

 Tryb przechwytywania (-c) Przechwyć informacje graficzne z działającej aplikacji i zapisze ją w pliku dziennika grafiki. Możliwości przechwytywania i format pliku są takie same jak w programie Visual Studio.

 Tryb odtwarzania (-p) odtwarzanie wcześniej przechwyconych zdarzeń grafiki z istniejącego pliku dziennika grafiki. Domyślnie odtwarzanie odbywa się w oknie, nawet gdy plik dziennika grafiki został przechwycony z poziomu aplikacji w trybie pełnoekranowym. Odtwarzanie odbywa się na pełnym ekranie tylko wtedy, gdy plik dziennika grafiki został przechwycony z pełnoekranowego i `-rawmode` został określony.

 Tryb walidacji ( `-v` ) sprawdza poprawność renderowania, odtwarzając przechwycone ramki na sprzęcie i osnowie, a następnie porównując ich wyniki przy użyciu funkcji porównywania obrazu. Za pomocą tej funkcji można szybko identyfikować problemy z sterownikiem, które wpływają na renderowanie.

 Oprócz tych trybów dxcap.exe wykonuje dwie inne funkcje, które nie wykonują przechwytywania ani odtwarzania informacji graficznych.

 Funkcja Enumeration ( `-e` ) wyświetla szczegółowe informacje o aplikacjach platformy UWP zainstalowanych na komputerze. Te szczegóły obejmują nazwę pakietu i identyfikator aplikacji, które identyfikują plik wykonywalny w aplikacji platformy UWP. Aby przechwycić informacje graficzne z aplikacji ze sklepu Windows przy użyciu DXCap.exe, użyj nazwy pakietu i identyfikatora AppID zamiast pliku wykonywalnego, który jest używany podczas przechwytywania aplikacji klasycznej.

 Info — funkcja ( `-info)` wyświetla szczegóły dotyczące maszyny i przechwytywania bibliotek DLL.

## <a name="examples"></a>Przykłady

### <a name="capture-graphics-information-from-a-desktop-app"></a>Przechwytywanie informacji graficznych z aplikacji klasycznej
 Użyj `-c` , aby określić aplikację, z której mają być przechwytywane informacje graficzne.

```cmd
DXCap.exe -c BasicHLSL11.exe
```

 Domyślnie informacje o grafice są rejestrowane w pliku o nazwie `<appname>-<date>-<time>.vsglog` . Użyj `-file` , aby określić inny plik do zarejestrowania.

```cmd
DXCap.exe -file regression_test_12.vsglog -c BasicHLSL11.exe
```

 Określ dodatkowe parametry wiersza polecenia dla aplikacji, z której są przechwytywane dane, uwzględniając je po nazwie pliku aplikacji.

```cmd
DXCap.exe -c "C:\Program Files\Internet Explorer\iexplorer.exe" "www.fishgl.com"
```

 Polecenie w powyższym przykładzie przechwytuje informacje graficzne z wersji klasycznej programu Internet Explorer podczas wyświetlania strony sieci Web znajdującej się w www.fishgl.com, która używa interfejsu API WebGL do renderowania zawartości 3-D.

> [!NOTE]
> Ponieważ argumenty wiersza polecenia, które pojawiają się po przekazaniu aplikacji do niej, należy określić argumenty przewidziane dla DXCap.exe przed użyciem `-c` opcji.

### <a name="capture-graphics-information-from-a-uwp-app"></a>Przechwyć informacje graficzne z aplikacji platformy UWP.
 Możesz przechwytywać informacje graficzne z aplikacji platformy UWP.

```cmd
DXCap.exe -c Microsof.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe,AppexMaps
```

 Używanie DXCap.exe do przechwytywania z aplikacji platformy UWP przypomina korzystanie z niej do przechwytywania z aplikacji klasycznej systemu Windows, ale zamiast identyfikowania aplikacji klasycznej według nazwy pliku, należy zidentyfikować aplikację platformy UWP przy użyciu jej nazwa pakietu oraz nazwy lub identyfikatora pliku wykonywalnego w tym pakiecie, który ma zostać przechwycony. Aby ułatwić dowiedzieć się, jak zidentyfikować aplikacje platformy UWP zainstalowane na maszynie, użyj `-e` opcji z DXCap.exe, aby je wyliczyć:

```cmd
DXCap.exe -e
```

 Możesz podać opcjonalny ciąg wyszukiwania, aby pomóc znaleźć szukaną aplikację. W przypadku podanego ciągu wyszukiwania DXCap.exe wylicza aplikacje platformy UWP, których nazwa pakietu, nazwa aplikacji lub identyfikatory aplikacji pasują do ciągu wyszukiwania. W wyszukiwaniu nie jest rozróżniana wielkość liter.

```cmd
DXCap.exe -e map
```

 Powyższe polecenie wylicza aplikacje platformy UWP, które pasują do "map"; Oto dane wyjściowe:

 **Package "Microsoft. BingMaps":** **InstallDirectory: C: \ Program Files \ WindowsApps \ Microsoft. BingMaps_2.1.2914.1734_X64__8wekyb3d8bbwe** **FullName: Microsoft. BingMaps_2.1.2914.1734 _x64__8wekyb3d8bbwe** **UserSID: S-1-5-21-2127521184-1604012920-1887927527-5603533** **Nazwa: Microsoft. BingMaps** **Publisher: CN = Microsoft Corporation, O = Microsoft Corporation, L = Redmond, S = Waszyngton, C = wersja US** **: 2.1.2914.1734** **aplikacje do uruchomienia:** **Identyfikator: AppexMaps** **exe: C: \ Program Files\WindowsApps\Microsoft.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe\Map.exe** **IsWWA: brak** **appspec (do uruchomienia): DXCap.exe-C Microsoft. BingMaps_2.1.2914.1734 _x64__8wekyb3d8bbwe, AppexMaps** ostatni wiersz danych wyjściowych dla każdej wyliczeniowej aplikacji wyświetla polecenie, którego można użyć do przechwytywania z niego informacji graficznych.

### <a name="capture-specific-frames-or-frames-between-specific-times"></a>Przechwyć określone ramki lub ramki między określonymi czasami.
 Użyj `-frame` , aby określić ramki, które mają być przechwytywane przy użyciu przecinków i zakresów:

```cmd
DXCap.exe -frame 2,5,7-9,15 -c SimpleBezier11.exe
```

 Lub użyj, `-period` Aby określić zestaw zakresów czasu, w których mają być przechwytywane ramki. Zakresy czasu są określone w sekundach i można określić wiele zakresów:

```cmd
DXCap.exe -period 2.1-5, 7.0-9.3 -c SimpleBezier11.exe
```

### <a name="capture-frames-interactively"></a>Przechwyć ramki interaktywnie.
 Użyj `-manual` , aby przechwycić ramki interaktywnie. Naciśnij klawisz ENTER, aby rozpocząć przechwytywanie, a następnie ponownie naciśnij klawisz ENTER, aby zatrzymać.

```cmd
DXCap.exe -manual -c SimpleBezier11.exe
```

### <a name="play-back-a-graphic-log-file"></a>Odtwórz graficzny plik dziennika
 Służy `-p` do odtwarzania wcześniej przechwyconego pliku dziennika grafiki.

```cmd
DXCap.exe -p regression_test_12.vsglog
```

 Pozostaw nazwę pliku, aby odtworzyć dziennik grafiki, który został przechwycony ostatnio.

```cmd
DXCap.exe -p
```

### <a name="play-back-in-raw-mode"></a>Odtwórz w trybie nieprzetworzonym
 Służy `-rawmode` do odtwarzania przechwyconych poleceń dokładnie tak, jak wystąpiły. W przypadku normalnego odtwarzania niektóre polecenia są emulowane, na przykład plik dziennika grafiki przechwycone z aplikacji pełnoekranowego będzie odtwarzany w oknie; w trybie nieprzetworzonym ten sam plik będzie podejmować próby odtwarzania na pełnym ekranie.

```cmd
DXCap.exe -p regression_test_12.vsglog -rawmode
```

### <a name="play-back-using-warp-or-a-hardware-device"></a>Odtwórz przy użyciu wypaczenia lub urządzenia sprzętowego
 Może zajść potrzeba wymuszenia odtwarzania pliku dziennika grafiki przechwyconego na urządzeniu sprzętowym w celu użycia wypaczenia lub wymuszenia odtwarzania dziennika przechwyconego przy użyciu urządzenia sprzętowego. Użyj `-warp` , aby odtworzyć przy użyciu osnowy.

```cmd
DXCap.exe -p regression_test_12.vsglog -warp
```

 Służy `-hw` do odtwarzania sprzętu.

```cmd
DXCap.exe -p regression_test_12.vsglog -hw
```

### <a name="validate-a-graphics-log-file-against-warp"></a>Sprawdź poprawność pliku dziennika grafiki przed wypaczeniem
 W obszarze Tryb walidacji plik dziennika grafiki jest odtwarzany na sprzęcie i OSNOWie, a ich wyniki są porównywane. Może to pomóc w zidentyfikowaniu błędów renderowania, które są spowodowane przez sterownik. Użyj-v, aby sprawdzić poprawność zachowania sprzętu graficznego przed ZNIEKSZTAŁCENIem.

```cmd
DXCap.exe -v regression_test_12.vsglog
```

 Aby zmniejszyć liczbę porównań, można określić podzbiór poleceń do porównania, a inne polecenia zostaną zignorowane. Użyj-Sprawdź, aby określić polecenia, których wyniki chcesz porównać.

```cmd
DXCap.exe -v regression_test_12.vsglog -examine present,draw,copy,clear
```

### <a name="convert-a-graphics-log-file-to-pngs"></a>Konwertuj plik dziennika grafiki na PNGs
 Aby wyświetlić lub przeanalizować ramki z pliku dziennika grafiki, DXCap.exe może zapisywać przechwycone ramki jako pliki obrazów PNG (Portable Network Graphics). Użyj opcji `-screenshot` do w obszarze Tryb odtwarzania, aby wychwycić przechwycone ramki jako pliki PNG.

```cmd
DXCap.exe -p BasicHLSL11.vsglog -screenshot
```

 Użyj polecenia `-frame` with, `-screenshot` Aby określić ramki, które mają być wyprowadzane.

```cmd
DXCap.exe -p BasicHLSL11.vsglog -screenshot -frame 5, 7-9
```

### <a name="convert-a-graphics-log-file-to-xml"></a>Konwertuj plik dziennika grafiki do formatu XML
 Aby przetwarzać i analizować dzienniki grafiki przy użyciu znanych narzędzi, takich jak FindStr lub XSLT, DXCap.exe może skonwertować plik dziennika grafiki do formatu XML. Użyj `-toXML` opcji w trybie odtwarzania, aby przekonwertować dziennik na kod XML zamiast go odtworzyć.

```cmd
DXCap.exe -p regression_test_12.vsglog -toXML
```

 Domyślnie dane wyjściowe XML są zapisywane w pliku o tej samej nazwie co dziennik grafiki, ale ma rozszerzenie. XML. W powyższym przykładzie plik XML będzie miał nazwę **regression_test_12.xml**. Aby nadać plikowi XML inną nazwę, określ ją po `-toXML` .

```cmd
DXCap.exe -p regression_test_12.vsglog -toXML temp.xml
```

 Wynikowy plik będzie zawierać kod XML, który wygląda podobnie do tego:

```xml
<Moment value="67"/>
<Method name="CreateDXGIFactory1" >
    <Return type="HRESULT" value="S_OK" />
    <Parameter name="riid" type="IID" value="770AAE78-F26F-4DBA-A829-253C83D1B387" />
    <Parameter name="ppFactory" type="void" handle="1" isOutput="true" />
</Method>

<Moment value="167"/>
<Method name="D3D11CreateDevice" >
    <Return type="HRESULT" value="S_OK" />
    <Parameter name="pAdapter" type="IDXGIAdapter" handle="34" />
    <Parameter name="DriverType" type="D3D_DRIVER_TYPE" value="D3D_DRIVER_TYPE_UNKNOWN" />
    <Parameter name="Software" type="HMODULE" value="pointer" />
    <Parameter name="Flags" type="UINT" value="0" />
    <Parameter name="pFeatureLevels" type="D3D_FEATURE_LEVEL" arrSize="1" >
        <Element value="D3D_FEATURE_LEVEL_11_0" />
    </Parameter>
    <Parameter name="FeatureLevels" type="UINT" value="1" />
    <Parameter name="SDKVersion" type="UINT" value="7" />
    <Parameter name="ppDevice" type="ID3D11Device" handle="35" isOutput="true" />
    <Parameter name="pFeatureLevel" type="D3D_FEATURE_LEVEL" value="D3D_FEATURE_LEVEL_11_0" isOutput="true" />
    <Parameter name="ppImmediateContext" type="ID3D11DeviceContext" value="nullptr" isOutput="true" />
</Method>
```

## <a name="requirements"></a>Wymagania