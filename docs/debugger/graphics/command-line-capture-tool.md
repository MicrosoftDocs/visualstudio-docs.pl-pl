---
title: Narzędzie Command-Line Capture | Microsoft Docs
description: Dowiedz się DXCap.exe, narzędziu wiersza polecenia do przechwytywania i odtwarzania diagnostyki grafiki, które obsługuje funkcję Direct3D od 10 do Direct3D 12 na wszystkich poziomach funkcji.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: db75b3a7-80b2-4a74-91d2-fd6e0f73b45d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b305d2f2f84d4b3f52d9be40f18fe02c9eb93df2
ms.sourcegitcommit: aeed3eb503d0b282537b073ebae8c028c4fef750
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/15/2021
ms.locfileid: "114232716"
---
# <a name="command-line-capture-tool"></a>Narzędzie wiersza polecenia do przechwytywania
DXCap.exe to narzędzie wiersza polecenia do przechwytywania i odtwarzania diagnostyki grafiki. Obsługuje on funkcje Direct3D od 10 do Direct3D 12 na wszystkich poziomach funkcji.

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
 `-file`W trybie przechwytywania ( ) określa nazwę pliku dziennika grafiki, w których są rejestrowane `filename` `-c` informacje `filename` graficzne. Jeśli `filename` nie zostanie określony, informacje graficzne są rejestrowane w pliku o nazwie `<appname>-<date>-<time>.vsglog` domyślnie.

 W trybie weryfikacji (-v) `filename` określa nazwę pliku dziennika grafiki do weryfikacji. Jeśli `filename` nie zostanie określony, dziennik grafiki, który został ostatnio zweryfikowany jest używany ponownie.

 `-frame``frames`W obszarze tryb przechwytywania `frames` określa ramki, które chcesz przechwycić. Pierwsza ramka to 1. Można określić kilka ramek przy użyciu przecinków i zakresów. Na przykład jeśli to `frames` , ramki , , , , i są `2, 5, 7-9, 15` `2` `5` `7` `8` `9` `15` przechwytywane.

> [!TIP]
> Użyj klawisza , aby określić, że ramki będą `-frame` `manual` przechwytywane ręcznie, naciskając klawisz Print Screen. Ramki mogą być przechwytywane podczas uruchamiania aplikacji. aby zatrzymać przechwytywanie ramek, wróć do interfejsu wiersza polecenia i naciśnij klawisz Enter.

 `-period`W obszarze tryb przechwytywania określa zakres czasu (w sekundach), w którym `periods` `periods` mają być przechwytywane ramki. Można określić kilka kropek przy użyciu przecinków i zakresów. Jeśli na przykład jest wartością , przechwytywane są ramki, które są renderowane między `periods` `2.1-5, 7.0-9.3` i `2.1` `5` sekundami oraz między i `7` `9.3` .

 `-c``app`[ `args...` ] Tryb przechwytywania. W obszarze tryb przechwytywania określa nazwę aplikacji, z której chcesz przechwytywać informacje graficzne; określa dodatkowe parametry wiersza polecenia `app` `args...` dla tej aplikacji.

 `-p` [ `filename` ] Tryb odtwarzania ( `-p` ). W obszarze trybu odtwarzania określa nazwę pliku dziennika `filename` grafiki, który ma być odtwarzany. Jeśli nie zostanie określony, dziennik grafiki, który został ostatnio odtwarzany `filename` jest używany ponownie.

 `-debug` W trybie odtwarzania `-debug` określa, że odtwarzanie powinno być odtwarzane z włączoną warstwą debugowania Direct3D.

 `-warp` W obszarze trybu `-warp` odtwarzania określa, że odtwarzanie powinno być odtwarzane przy użyciu programowego programu renderowego WARP.

 `-hw` W obszarze trybu `-hw` odtwarzania określa, że odtwarzanie powinno być odtwarzane przy użyciu sprzętu GPU.

 `-config` W trybie `-config` odtwarzania program wyświetla wszystkie informacje o maszynie użytej do przechwycenia pliku dziennika grafiki.

 `-rawmode` W trybie `-rawmode` odtwarzania określa, że odtwarzanie powinno być wykonywane bez modyfikacji zarejestrowanych zdarzeń. Podczas normalnego działania tryb odtwarzania może wprowadzać drobne zmiany w odtwarzaniu, aby uprościć debugowanie i przyspieszyć odtwarzanie. Na przykład może symulować dane wyjściowe łańcucha wymiany zamiast wykonywania poleceń łańcucha wymiany. Zazwyczaj to odtwarzanie nie jest problemem, ale może być konieczne odtwarzanie w sposób, który jest bardziej chłoniany do zarejestrowanego zdarzenia. Na przykład można użyć tej opcji, aby przywrócić zachowanie renderowania pełnoekranowego do aplikacji, która została przechwycona podczas działania w trybie pełnoekranowym.

 `-toXML` [ ] W trybie odtwarzania określa nazwę pliku, w którym jest zapisywana `xml_filename` `xml_filename` reprezentacja XML odtwarzania. Jeśli nie zostanie określony, reprezentacja XML jest zapisywana w pliku o nazwie takiej samej jak plik, który `xml_filename` jest odtwarzany, ale na podstawie `.xml` rozszerzenia.

 `-v` Tryb weryfikacji. W trybie weryfikacji przechwycone ramki są odtwarzane na sprzęcie i warP, a ich wyniki są porównywane przy użyciu funkcji porównywania obrazów. Ta funkcja umożliwia szybkie identyfikowanie problemów ze sterownikami, które mają wpływ na renderowanie.

 `-examine``events`W trybie `events` weryfikacji określa zestaw zdarzeń graficznych, których natychmiastowe wyniki są porównywane. Na przykład `-examine present,draw,copy,clear` ogranicza porównanie tylko do zdarzeń należących do tych kategorii.

> [!TIP]
> Zalecamy rozpoczęcie od , ponieważ spowoduje to ujawnienie większości problemów, ale zajmie to znacznie mniej czasu `-examine present,draw,copy,clear` niż w przypadku bardziej rozbudowanych zdarzeń. W razie potrzeby można określić większy lub inny zestaw zdarzeń, aby zweryfikować te zdarzenia i ujawnić inne rodzaje problemów.

 `-haltonfail` W trybie weryfikacji `-haltonfail` program zatrzymuje walidację, gdy zostaną wykryte różnice między sprzętem a programem renderowym WARP. Walidacja zostanie wznowiona po naciśnięciu klawisza.

 `-exitonfail` W trybie weryfikacji program natychmiast kończy sprawdzanie poprawności po wykryciu różnic między sprzętem a `-exitonfail` programem renderowym WARP. Gdy program zakończy działanie w ten sposób, powraca do środowiska. W przeciwnym razie `0` zwraca wartość `1` .

 `-showprogress` W trybie `-showprogress` weryfikacji program wyświetla informacje o postępie sesji weryfikacji. Postęp WARP jest wyświetlany po lewej stronie; postęp sprzętu jest wyświetlany po prawej stronie.

 `-e``search_string`Wylicza zainstalowane aplikacje platformy UWP. Te informacje mogą być służące do wykonywania przechwytywania w wierszu polecenia za pomocą aplikacji platformy UWP.

 `-info` Wyświetla informacje o maszynie i przechwytywanie bibliotek DLL.

## <a name="remarks"></a>Uwagi
 DXCap.exe działa w trzech trybach:

 Tryb przechwytywania (-c) Przechwytywanie informacji graficznych z uruchomionej aplikacji i rejestrowanie ich w pliku dziennika grafiki. Możliwości przechwytywania i format pliku są identyczne z możliwościami Visual Studio.

 Tryb odtwarzania (-p) Odtwarzanie przechwyconych wcześniej zdarzeń graficznych z istniejącego pliku dziennika grafiki. Domyślnie odtwarzanie odbywa się w oknie, nawet wtedy, gdy plik dziennika grafiki został przechwycony z aplikacji pełnoekranowej. Odtwarzanie odbywa się na pełnym ekranie tylko wtedy, gdy plik dziennika grafiki został przechwycony z aplikacji `-rawmode` pełnoekranowej i jest określony.

 Tryb weryfikacji ( ) weryfikuje zachowanie renderowania, odtwarzając przechwycone ramki na sprzęcie i WARP, a następnie porównując ich wyniki przy użyciu `-v` funkcji porównywania obrazów. Ta funkcja umożliwia szybkie identyfikowanie problemów ze sterownikami, które mają wpływ na renderowanie.

 Oprócz tych trybów program dxcap.exe dwie inne funkcje, które nie wykonują przechwytywania ani odtwarzania informacji graficznych.

 Funkcja wyliczania ( `-e` ) Wyświetla szczegółowe informacje o aplikacjach platformy UWP zainstalowanych na maszynie. Te szczegóły obejmują nazwę pakietu i appid identyfikujące plik wykonywalny w aplikacji platformy uniwersalnej systemu Windows. Aby przechwytywać informacje graficzne z aplikacji ze Sklepu Windows przy użyciu usługi DXCap.exe, użyj nazwy pakietu i appid zamiast nazwy pliku wykonywalnego używanego podczas przechwytywania aplikacji klasycznej.

 Info function `-info)` (Wyświetla szczegółowe informacje o maszynie i przechwytuje biblioteki DLL.

## <a name="examples"></a>Przykłady

### <a name="capture-graphics-information-from-a-desktop-app"></a>Przechwytywanie informacji graficznych z aplikacji klasycznej
 Użyj `-c` , aby określić aplikację, z której chcesz przechwytywać informacje graficzne.

```cmd
DXCap.exe -c BasicHLSL11.exe
```

 Domyślnie informacje graficzne są rejestrowane w pliku o nazwie `<appname>-<date>-<time>.vsglog` . Użyj `-file` , aby określić inny plik do nagrania.

```cmd
DXCap.exe -file regression_test_12.vsglog -c BasicHLSL11.exe
```

 Określ dodatkowe parametry wiersza polecenia dla przechwytywanej aplikacji, uwzględniając je po nazwie pliku aplikacji.

```cmd
DXCap.exe -c "C:\Program Files\Internet Explorer\iexplorer.exe" "www.fishgl.com"
```

 Polecenie w powyższym przykładzie przechwytuje informacje graficzne z wersji klasycznej programu Internet Explorer podczas przeglądania strony sieci Web znajdującej się w witrynie www.fishgl.com która używa interfejsu API WebGL do renderowania zawartości 3-D.

> [!NOTE]
> Ponieważ argumenty wiersza polecenia, które pojawiają się po przekazyniu aplikacji, należy określić argumenty przeznaczone dla DXCap.exe przed użyciem `-c` opcji .

### <a name="capture-graphics-information-from-a-uwp-app"></a>Przechwytywanie informacji graficznych z aplikacji platformy UWP.
 Informacje graficzne można przechwytywać z aplikacji platformy uniwersalnej systemu Windows.

```cmd
DXCap.exe -c Microsof.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe,AppexMaps
```

 Przechwytywanie z aplikacji platformy uniwersalnej systemu Windows przy użyciu narzędzia DXCap.exe jest podobne do przechwytywania z aplikacji klasycznej platformy Windows. Zamiast tego identyfikowanie aplikacji klasycznej według nazwy pliku pozwala zidentyfikować aplikację platformy uniwersalnej systemu Windows według nazwy pakietu oraz nazwy lub identyfikatora pliku wykonywalnego wewnątrz tego pakietu, z którego ma zostać przechwycony plik. Aby ułatwić znalezienie sposobu identyfikowania aplikacji platformy UWP zainstalowanych na maszynie, użyj opcji z DXCap.exe, aby `-e` je wyliczyć:

```cmd
DXCap.exe -e
```

 Możesz podać opcjonalny ciąg wyszukiwania, który pomoże Ci znaleźć szukaną aplikację. Po podano ciąg wyszukiwania, program DXCap.exe aplikacje platformy UWP, których nazwa pakietu, nazwa aplikacji lub identyfikatory aplikacji pasują do ciągu wyszukiwania. W wyszukiwaniu nie jest uwzględniania ich litera.

```cmd
DXCap.exe -e map
```

 Powyższe polecenie wylicza aplikacje platformy UWP zgodne z "mapą"; oto dane wyjściowe:

 Pakiet **"Microsoft.BingMaps":** **InstallDirectory : C:\Program Files\WindowsApps\Microsoft.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe FullName : Microsoft.BingMaps_2.1.2914.1734_x64__8wekyb** **UserSID 3d8bbwe** : **S-1-5-21-2127521184-1604012920-1887927527-56035333** **Name : Microsoft.BingMaps** **Publisher: CN=Microsoft Corporation, O=Microsoft Corporation, L =Redmond, S = Waszyngton, C = US** **wersji: 2.1.2914.1734** **launchable applications:** **Id: AppexMaps** **Exe: C:\Program Files\WindowsApps\Microsoft.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe\Map.exe** **IsWWA: No** **AppSpec (to launch): DXCap.exe -c Microsoft.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe,AppexMaps** Ostatni wiersz danych wyjściowych dla każdej wyliczenia aplikacji wyświetla polecenie, za pomocą których można przechwytywać informacje graficzne.

### <a name="capture-specific-frames-or-frames-between-specific-times"></a>Przechwytywanie określonych ramek lub ramek między określonymi godzinami.
 Użyj , aby określić ramki do przechwycenia `-frame` przy użyciu przecinków i zakresów:

```cmd
DXCap.exe -frame 2,5,7-9,15 -c SimpleBezier11.exe
```

 Można też użyć `-period` funkcji , aby określić zestaw zakresów czasu, w których mają być przechwytywane ramki. Zakresy czasu są określone w sekundach i można określić wiele zakresów:

```cmd
DXCap.exe -period 2.1-5, 7.0-9.3 -c SimpleBezier11.exe
```

### <a name="capture-frames-interactively"></a>Interaktywne przechwytywanie ramek.
 Użyj `-manual` funkcji , aby interaktywnie przechwytywać ramki. Naciśnij klawisz Enter, aby rozpocząć przechwytywanie, a następnie naciśnij klawisz Enter ponownie, aby zatrzymać.

```cmd
DXCap.exe -manual -c SimpleBezier11.exe
```

### <a name="play-back-a-graphic-log-file"></a>Odtwarzanie pliku dziennika grafiki
 Użyj `-p` , aby odtworzyć wcześniej przechwycony plik dziennika grafiki.

```cmd
DXCap.exe -p regression_test_12.vsglog
```

 Pozostaw nazwę pliku, aby odtworzyć dziennik grafiki, który został ostatnio przechwycony.

```cmd
DXCap.exe -p
```

### <a name="play-back-in-raw-mode"></a>Odtwarzanie w trybie nieprzetworzonego
 Użyj `-rawmode` polecenia , aby odtworzyć przechwycone polecenia dokładnie tak, jak wystąpiły. Podczas normalnego odtwarzania niektóre polecenia są emulowane, na przykład plik dziennika grafiki przechwycony z aplikacji pełnoekranowej będzie odtwarzany w oknie; z włączonym trybem nieprzetworzonym ten sam plik spróbuje odtworzyć w trybie pełnoekranowym.

```cmd
DXCap.exe -p regression_test_12.vsglog -rawmode
```

### <a name="play-back-using-warp-or-a-hardware-device"></a>Odtwarzanie przy użyciu warp lub urządzenia sprzętowego
 Można wymusić odtwarzanie pliku dziennika grafiki przechwyconego na urządzeniu sprzętowym w celu użycia warP lub wymusić odtwarzanie dziennika przechwyconego na warp do korzystania z urządzenia sprzętowego. Użyj `-warp` , aby odtworzyć przy użyciu warp.

```cmd
DXCap.exe -p regression_test_12.vsglog -warp
```

 Użyj `-hw` , aby odtworzyć przy użyciu sprzętu.

```cmd
DXCap.exe -p regression_test_12.vsglog -hw
```

### <a name="validate-a-graphics-log-file-against-warp"></a>Weryfikowanie pliku dziennika grafiki przed WARP
 W trybie weryfikacji plik dziennika grafiki jest odtwarzany na sprzęcie i WARP, a ich wyniki są porównywane. Może to ułatwić zidentyfikowanie błędów renderowania, które są spowodowane przez sterownik. Użyj -v, aby zweryfikować poprawne zachowanie sprzętu graficznego przed WARP.

```cmd
DXCap.exe -v regression_test_12.vsglog
```

 Aby zmniejszyć liczbę porównań, można określić podzbiór poleceń do porównania, a inne polecenia zostaną zignorowane. Użyj -examine, aby określić polecenia, których wyniki chcesz porównać.

```cmd
DXCap.exe -v regression_test_12.vsglog -examine present,draw,copy,clear
```

### <a name="convert-a-graphics-log-file-to-pngs"></a>Konwertowanie pliku dziennika grafiki na elementy PNG
 Aby wyświetlić lub przeanalizować ramki z pliku dziennika grafiki, DXCap.exe zapisać przechwycone ramki jako .png (Portable Network Graphics) obrazów. Użyj `-screenshot` funkcji , aby w trybie odtwarzania wyprowadzać przechwycone ramki .png plików.

```cmd
DXCap.exe -p BasicHLSL11.vsglog -screenshot
```

 Użyj `-frame` z , aby określić `-screenshot` ramki, które mają być wyprowadzane.

```cmd
DXCap.exe -p BasicHLSL11.vsglog -screenshot -frame 5, 7-9
```

### <a name="convert-a-graphics-log-file-to-xml"></a>Konwertowanie pliku dziennika grafiki do formatu XML
 Aby przetwarzać i analizować dzienniki grafiki przy użyciu znanych narzędzi, takich jak FindStr lub XSLT, DXCap.exe przekonwertować plik dziennika grafiki na xml. Użyj `-toXML` w trybie odtwarzania, aby przekonwertować dziennik na xml zamiast odtwarzania go.

```cmd
DXCap.exe -p regression_test_12.vsglog -toXML
```

 Domyślnie dane wyjściowe XML są zapisywane w pliku o takiej samej nazwie jak dziennik grafiki, ale który ma .xml rozszerzenia. W powyższym przykładzie plik XML będzie miał nazwę **regression_test_12.xml**. Aby nadać plikowi XML inną nazwę, określ go po `-toXML` .

```cmd
DXCap.exe -p regression_test_12.vsglog -toXML temp.xml
```

 Wynikowy plik będzie zawierać kod XML podobny do tego:

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