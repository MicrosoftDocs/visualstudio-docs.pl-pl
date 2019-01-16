---
title: Narzędzie wiersza polecenia do przechwytywania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: db75b3a7-80b2-4a74-91d2-fd6e0f73b45d
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d4cafc8c066025f87d233d8b6db8a97be1aa16f5
ms.sourcegitcommit: 5a65ca6688a2ebb36564657d2d73c4b4f2d15c34
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "51770686"
---
# <a name="command-line-capture-tool"></a>Narzędzie wiersza polecenia do przechwytywania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DXCap.exe jest narzędziem wiersza polecenia do przechwytywania diagnostyki grafiki i odtwarzania. Obsługuje ona Direct3D 10 za pośrednictwem Direct3D 12 na wszystkich poziomach funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```ms-dos  
DXCap.exe [-file filename] [-frame frames | -period periods | -manual] -c app [args...]  
DXCap.exe -p [filename] [-debug | -warp | -hw] [-config] [-rawmode]  
DXCap.exe –p [filename] –screenshot [-frame frames]  
DXCap.exe –p [filename] –toXML [xml_filename]  
DXCap.exe –v [–file filename] [-examine events] [-haltonfail | -exitonfail] [-showprogress]  
DXCap.exe -e [search_string]  
DXCap.exe –info  
```  
  
#### <a name="parameters"></a>Parametry  
 `-file``filename`  
 W obszarze tryb przechwytywania (`-c`), `filename` Określa nazwę pliku dziennika grafiki, które informacje graficzne są rejestrowane w celu. Jeśli `filename` nie zostanie określony, informacje graficzne są rejestrowane w pliku o nazwie `<appname>-<date>-<time>.vsglog` domyślnie.  
  
 W ramach sprawdzania poprawności (-v) trybie `filename` Określa nazwę pliku dziennika grafiki, który ma zostać zweryfikowana. Jeśli `filename` nie zostanie określony, dziennik grafiki, która ostatniego sprawdzenia poprawności jest ponownie używany.  
  
 `-frame``frames`  
 W obszarze tryb przechwytywania `frames` określa ramek, które mają być przechwytywane. Pierwsza ramka to 1. Za pomocą przecinków i zakresów, można określić wiele ramek. Na przykład jeśli `frames` jest `2, 5, 7-9, 15`, następnie ramek `2`, `5`, `7`, `8`, `9`, i `15` są przechwytywane.  
  
 `-period``periods`  
 W obszarze tryb przechwytywania `periods` Określa zakresy czasu, w ciągu kilku sekund, podczas których chcesz przechwycić ramki. Można określić wiele kropek, za pomocą przecinków i zakresy. Na przykład jeśli `periods` jest `2.1-5, 7.0-9.3`, a następnie ramek, które mają być renderowane między `2.1` i `5` sekund oraz między`7` i `9.3` są przechwytywane w ciągu kilku sekund.  
  
 `-manual`  
 W obszarze tryb przechwytywania `-manual` Określa, że ramki będą przechwytywane ręcznie, naciskając klawisz Print Screen. Ramki mogą być przechwytywane, po uruchomieniu aplikacji; Aby zatrzymać przechwytywanie ramek, wróć do interfejsu wiersza polecenia, a następnie naciśnij klawisz enter.  
  
 `-c` `app` [`args...`]  
 Przechwyć trybu. W obszarze tryb przechwytywania `app` Określa nazwę aplikacji, którą chcesz przechwytywać informacje graficzne z; `args...` określa dodatkowe parametry wiersza polecenia do tej aplikacji.  
  
 `-p` [`filename`]  
 Tryb odtwarzania (`-p`). W trybie odtwarzania `filename` Określa nazwę pliku dziennika grafiki do odtworzenia. Jeśli `filename` nie zostanie określony, dziennik grafiki, który został ostatnio odtwarzany jest ponownie używany.  
  
 `-debug`  
 W trybie odtwarzania `-debug` określa tej odtwarzania, należy wykonać z włączoną warstwę debugowanie Direct3D.  
  
 `-warp`  
 W trybie odtwarzania `-warp` określa odtwarzania tego powinny być wykonywane przy użyciu modułu renderowania oprogramowania WARP.  
  
 `-hw`  
 W trybie odtwarzania `-hw` Określa, że odtwarzania powinny być wykonywane przy użyciu sprzęcie procesora GPU.  
  
 `-config`  
 W trybie odtwarzania `-config` Wyświetla informacje o komputerze który został użyty do przechwytywania pliku dziennika grafiki, jeśli te informacje został zarejestrowany w dzienniku.  
  
 `-rawmode`  
 W trybie odtwarzania `-rawmode` Określa, że odtwarzania powinno być wykonywane bez modyfikacji zarejestrowane zdarzenia. W ramach normalnych operacji trybie odtwarzania wprowadzać niewielkie zmiany odtwarzanie do uproszczenia, debugowania i przyspieszenia odtwarzania. Na przykład może zasymulować, dane wyjściowe łańcucha wymiany, a nie wykonywania poleceń w ramach łańcucha wymiany. Zazwyczaj nie jest to problem, ale może być konieczne odtwarzania w sposób, który jest bardziej wierne, aby zarejestrowane zdarzenia; na przykład służy tę opcję, aby przywrócić zachowanie renderowania pełnego ekranu do aplikacji, która została przechwycona w trybie pełnoekranowym.  
  
 `-toXML` [`xml_filename`]  
 W trybie odtwarzania `xml_filename` Określa nazwę pliku, w którym zapisywana jest reprezentacja XML odtwarzania. Jeśli `xml_filename` nie zostanie określony, reprezentacja XML są zapisywane w pliku o nazwie taki sam jak plik jest odtwarzany, ale biorąc pod uwagę `.xml` rozszerzenia.  
  
 `-v`  
 Tryb weryfikacji. W trybie weryfikacji przechwyconych klatek jest odtwarzany na sprzęt i WARP, a ich wyniki są porównywane za pomocą funkcji porównywania obrazu. Ta funkcja umożliwia szybkie identyfikowanie problemów sterowników, które mają wpływ na Twoje renderowania.  
  
 `-examine``events`  
 W trybie weryfikacji `events` określa zestaw zdarzenia grafiki, którego wyniki wprowadzenia są porównywane. Na przykład `-examine present,draw,copy,clear` ogranicza porównanie z tylko zdarzenia należące do tych kategorii.  
  
> [!TIP]
>  Zalecamy rozpoczęcie od `-examine present,draw,copy,clear` ponieważ spowoduje to ujawnić większości problemów, ale trwać znacznie krócej niż szerszy zestaw zdarzeń. Jeśli to konieczne, można określić zestaw większy lub różnych zdarzeń, aby zweryfikować te zdarzenia i wyświetlić inne rodzaje problemów.  
  
 `-haltonfail`  
 W trybie weryfikacji `-haltonfail` zatrzymuje sprawdzania poprawności po wykryciu różnic między sprzętem i renderowanie WARP. Sprawdzanie poprawności zostanie wznowione po naciśnięciu klawisza.  
  
 `-exitonfail`  
 W trybie weryfikacji `-exitonfail` kończy działanie sprawdzania poprawności natychmiast po wykryciu różnic między sprzętem i renderowanie WARP. Gdy program jest zamykany w ten sposób, zwraca `0` środowiska; w przeciwnym razie zwraca `1`.  
  
 `-showprogress`  
 W trybie weryfikacji `-showprogress` Wyświetla informacje o postępie o sesji sprawdzania poprawności. Postęp WARP jest wyświetlany po lewej stronie; postęp sprzętu jest wyświetlany po prawej stronie.  
  
 `-e``search_string`  
 Wylicza aplikacje Windows Store, które są zainstalowane. Te informacje można użyć do wykonania wiersza polecenia przechwytywania przy użyciu aplikacji Windows Store.  
  
 `-info`  
 Wyświetla informacje o bibliotece DLL maszyny i przechwytywania.  
  
## <a name="remarks"></a>Uwagi  
 DXCap.exe działa w trzech trybów:  
  
 Tryb przechwytywania (-c)  
 Przechwytywać informacje graficzne z uruchomionej aplikacji i zapisaniu go w pliku dziennika grafiki. Możliwości przechwytywania i formatu pliku są identyczne z programu Visual Studio.  
  
 Tryb odtwarzania (-p)  
 Odtwarzania zdarzenia grafiki przechwyconego wcześniej z istniejącego pliku dziennika grafiki. Domyślnie odtwarzanie odbywa się w oknie, nawet wtedy, gdy dziennika grafiki pliku przechwycone z poziomu aplikacji na pełnym ekranie. Odtwarzanie występuje w trybie pełnoekranowym, tylko gdy dziennika grafiki pliku został przechwycony z aplikacją pełny ekran i `–rawmode` jest określony.  
  
 Tryb weryfikacji (`-v`)  
 Sprawdza poprawność zachowanie renderowania odtwarzania przechwycone ramki na sprzęt i WARP, a następnie porównywanie ich wyników przy użyciu funkcji porównywania obrazu. Ta funkcja umożliwia szybkie identyfikowanie problemów sterowników, które mają wpływ na Twoje renderowania.  
  
 Oprócz tych trybów dxcap.exe wykonuje dwie funkcje, które nie wykonują przechwytywania i odtwarzania informacji graficznych.  
  
 Funkcję wyliczenia (`-e`)  
 Wyświetla szczegółowe informacje dotyczące aplikacji Windows Store, które są zainstalowane na maszynie. Te informacje obejmują nazwę pakietu i identyfikator aplikacji, które identyfikują pliku wykonywalnego w aplikacji Windows Store. Aby przechwytywać informacje graficzne z aplikacji do sklepu windows przy użyciu DXCap.exe, należy użyć nazwy pakietu i appid zamiast nazwy pliku wykonywalnego używanego podczas przechwytywania aplikacji klasycznej.  
  
 Informacje o funkcji)`-info)`  
 Wyświetla szczegóły dotyczące bibliotek DLL maszyny i przechwytywania.  
  
## <a name="examples"></a>Przykłady  
  
### <a name="capture-graphics-information-from-a-desktop-app"></a>Przechwytywać informacje graficzne z aplikacji klasycznej  
 Użyj `–c` określić aplikację, z którego chcesz przechwytywać informacje graficzne.  
  
```ms-dos  
DXCap.exe –c BasicHLSL11.exe  
```  
  
 Domyślnie informacje graficzne są rejestrowane w pliku o nazwie `<appname>-<date>-<time>.vsglog`. Użyj `–file` można określić inny plik do rejestrowania się.  
  
```ms-dos  
DXCap.exe –file regression_test_12.vsglog –c BasicHLSL11.exe  
```  
  
 Wymagają podania dodatkowych parametrów wiersza polecenia do aplikacji, która udało się przechwycić z uwzględniając po aplikacji nazwa_pliku.  
  
```ms-dos  
DXCap.exe –c "C:\Program Files\Internet Explorer\iexplorer.exe" "www.fishgl.com"  
```  
  
 Polecenia w powyższym przykładzie przechwytuje informacje graficzne z wersji klasycznej programu Internet Explorer podczas wyświetlania strony sieci Web, znajduje się w www.fishgl.com korzystającego z interfejsu API WebGL do renderowania zawartości 3D.  
  
> [!NOTE]
>  Ponieważ argumenty wiersza polecenia, które pojawiają się po aplikacji są przekazywane do niego, należy określić argumenty przeznaczonych do DXCap.exe przed rozpoczęciem korzystania z `–c` opcji.  
  
### <a name="capture-graphics-information-from-a-windows-store-app"></a>Przechwytywać informacje graficzne z aplikacji Windows Store.  
 Można przechwytywać informacje graficzne z aplikacji Windows Store.  
  
```ms-dos  
DXCap.exe –c Microsof.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe,AppexMaps  
```  
  
 Używanie DXCap.exe do przechwycenia z aplikacji Windows Store jest podobne do korzystania z niego do przechwycenia z aplikacji pulpitu Windows, ale zamiast tego identyfikowanie aplikacji komputerowej nazwy, ustalić aplikacji Windows Store przez jego pakiet nazwę i nazwę lub identyfikator pliku wykonywalnego wewnątrz tego pakietu okres ważności, które mają być przechwytywane z. Aby ułatwić dowiedzieć się, jak identyfikować aplikacje Windows Store, które są zainstalowane na komputerze, należy użyć `–e` opcji z DXCap.exe wyliczanie ich:  
  
```ms-dos  
DXCap.exe -e  
```  
  
 Możesz podać ciąg opcjonalne wyszukiwania, aby ułatwić znajdowanie aplikacji, którego szukasz. Jeśli zostanie podany ciąg wyszukiwania, DXCap.exe wylicza aplikacje Windows Store, w których nazwa pakietu, nazwę aplikacji lub identyfikatory aplikacji pasuje do ciągu wyszukiwania. Wyszukiwanie jest rozróżniana wielkość liter.  
  
```ms-dos  
DXCap.exe –e map  
```  
  
 Powyższe polecenie wylicza aplikacje Windows Store, spełniające "mapy"; Oto dane wyjściowe:  
  
 **Pakiet "Microsoft.BingMaps":**  
 **InstallDirectory: C:\Program Files\WindowsApps\Microsoft.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe**  
 **Imię i nazwisko: Microsoft.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe**  
 **UserSID: S-1-5-21-2127521184-1604012920-1887927527-5603533**  
 **Nazwa: Microsoft.BingMaps**  
 **Publisher        : CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US**  
 **Wersja: 2.1.2914.1734**  
 **Możliwych do uruchomienia aplikacji:**  
 **Identyfikator: AppexMaps**  
 **Exe: C:\Program Files\WindowsApps\Microsoft.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe\Map.exe**  
 **IsWWA: Brak**  
 **AppSpec (do uruchomienia): DXCap.exe - c Microsoft.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe,AppexMaps** ostatni wiersz danych wyjściowych dla każdej aplikacji wyliczany zawiera polecenia, można użyć, aby przechwytywać informacje graficzne z niego.  
  
### <a name="capture-specific-frames-or-frames-between-specific-times"></a>Przechwytywanie ramki określonego lub ramki między określonym czasie.  
 Użyj `–frame` określić ramek, które mają być przechwytywane za pomocą przecinków i zakresów:  
  
```ms-dos  
DXCap.exe –frame 2,5,7-9,15 –c SimpleBezier11.exe  
```  
  
 Możesz też korzystać z `–period` do określenia zestawu zakresy czasu, podczas której ramki. Zakresy czasu są określane w sekundach i można określić wiele zakresów:  
  
```ms-dos  
DXCap.exe –period 2.1-5, 7.0-9.3 –c SimpleBezier11.exe  
```  
  
### <a name="capture-frames-interactively"></a>Przechwytywanie ramek interaktywnie.  
 Użyj `–manual` interaktywnie przechwycić ramki. Naciśnij klawisz Enter, aby rozpocząć przechwytywania, a następnie naciśnij klawisz Enter, ponownie, aby zatrzymać.  
  
```ms-dos  
DXCap.exe –manual -c SimpleBezier11.exe  
```  
  
### <a name="play-back-a-graphics-log-file"></a>Odtwarzanie pliku dziennika grafiki  
 Użyj `-p` do odtwarzania pliku dziennika grafiki przechwyconego wcześniej.  
  
```ms-dos  
DXCap.exe –p regression_test_12.vsglog  
```  
  
 Opuść nazwę pliku, aby odtworzyć dziennik grafiki, przechwyconą ostatnio.  
  
```ms-dos  
DXCap.exe –p  
```  
  
### <a name="play-back-in-raw-mode"></a>Odtwarzanie w trybie raw  
 Użyj `-rawmode` do odtwarzania przechwyconych poleceń, dokładnie tak, jak ich wystąpienia. W obszarze normalne odtwarzanie niektórych poleceń są emulowane, na przykład plik dziennika grafiki przechwytywane z aplikacji pełny ekran zostaną odtworzone w oknie; z włączonym trybem raw ten sam plik będzie podejmować próby odtwarzania w trybie pełnoekranowym.  
  
```ms-dos  
DXCap.exe –p regression_test_12.vsglog -rawmode  
```  
  
### <a name="play-back-using-warp-or-a-hardware-device"></a>Odtwórz ponownie za pomocą WARP lub urządzenia sprzętowego  
 Możesz chcieć wymusić odtwarzania tylnej stronie plik dziennika grafiki, przechwycone na urządzenie sprzętowe, aby użyć WARP lub wymusić odtwarzania dziennika przechwycone na WARP, aby użyć urządzenia sprzętowego. Użyj `-warp` odtwarzanie ponownie za pomocą WARP.  
  
```ms-dos  
DXCap.exe –p regression_test_12.vsglog -warp  
```  
  
 Użyj `-hw` odtwarzanie ponownie za pomocą sprzętu.  
  
```ms-dos  
DXCap.exe –p regression_test_12.vsglog -hw  
```  
  
### <a name="validate-a-graphics-log-file-against-warp"></a>Sprawdzanie poprawności względem WARP plik dziennika grafiki  
 W trybie weryfikacji pliku dziennika grafiki jest odtwarzany na sprzęt i WARP, a jego wyniki są porównywane. Może to ułatwić identyfikację błędy renderowania, które są spowodowane przez sterownik. Użyj – v, aby zweryfikować poprawne zachowanie sprzęt graficzny względem WARP.  
  
```ms-dos  
DXCap.exe -v regression_test_12.vsglog  
```  
  
 Aby zmniejszyć ilość porównań, można określić podzestaw poleceń do sprawdzania poprawności do porównania i inne polecenia zostaną zignorowane. Użyj — Sprawdź, aby określić polecenie, którego wyniki chcesz porównać.  
  
```ms-dos  
DXCap.exe -v regression_test_12.vsglog –examine present,draw,copy,clear  
```  
  
### <a name="convert-a-graphics-log-file-to-pngs"></a>Konwertuj plik dziennika grafiki na PNG  
 Aby wyświetlić lub analizowanie ramek z pliku dziennika grafiki, DXCap.exe można zapisać przechwycone ramki jako .png pliki obrazów (Portable Network Graphics). Użyj `-screenshot` do w trybie odtwarzania, służący do wypełniania wyjściowego przechwycone ramki jako pliki PNG.  
  
```ms-dos  
DXCap.exe -p BasicHLSL11.vsglog -screenshot  
```  
  
 Użyj `–frame` z `–screenshot` określa ramki, które mają być danych wyjściowych.  
  
```ms-dos  
DXCap.exe -p BasicHLSL11.vsglog -screenshot –frame 5, 7-9  
```  
  
### <a name="convert-a-graphics-log-file-to-xml"></a>Konwertowanie pliku dziennika grafiki do pliku XML  
 Aby przetwarzać i analizować dzienniki grafiki przy użyciu znanych narzędzi, takich jak FindStr lub XSLT, DXCap.exe przekonwertować plik dziennika grafiki do pliku XML. Użyj `-toXML` w trybie odtwarzania, aby przekonwertować dziennika XML zamiast jego odtwarzanie kopii.  
  
```ms-dos  
DXCap.exe –p regression_test_12.vsglog –toXML  
```  
  
 Domyślnie dane wyjściowe XML są zapisywane w pliku z taką samą nazwę jak dziennika grafiki, ale która ma rozszerzenie .xml. W powyższym przykładzie będzie nazwę pliku XML **regression_test_12.xml**. Nazwij plik XML inny, określ je po `-toXML`.  
  
```ms-dos  
DXCap.exe –p regression_test_12.vsglog –toXML temp.xml  
```  
  
 Wynikowy plik będzie zawierać plik XML, który wygląda podobnie do następującej:  
  
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



