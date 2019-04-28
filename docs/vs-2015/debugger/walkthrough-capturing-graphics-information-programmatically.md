---
title: 'Przewodnik: Programowe przechwytywanie informacji graficznych | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: a5adeff9-afaf-4047-b5ce-ef0aefe710eb
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1eaa3547733432715c5362b20030fe3d4a886900
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63444331"
---
# <a name="walkthrough-capturing-graphics-information-programmatically"></a>Przewodnik: programowe przechwytywanie informacji graficznych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz użyć [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] diagnostyki grafiki, aby programowo przechwytywać informacje graficzne z aplikacji Direct3D.  
  
 Przechwytywanie programistyczne jest przydatne w scenariuszach takich jak:  
  
- Po grafiki nie korzysta z swapchain obecny, takie jak po renderowaniu produktu do tekstury programowo rozpocząć przechwytywania.  
  
- Po aplikacji nie renderuje, takie jak kiedy używa DirectCompute do wykonywania obliczeń programistycznie rozpocząć przechwytywania.  
  
- Wywołaj `CaptureCurrentFrame`po z problemem renderowania jest trudny do przewidywania i przechwytywania podczas testowania ręcznego, ale można przewidzieć programowo przy użyciu informacji o stanie aplikacji w czasie wykonywania.  
  
## <a name="CaptureDX11_2"></a> Przechwytywanie programistyczne w Windows 8.1  
 Tej części instruktażu pokazano Przechwytywanie programistyczne w aplikacjach korzystających z interfejsu API programu DirectX 11.2 na Windows 8.1, która używa metody przechwytywania niezawodne. Aby uzyskać informacje o sposobie używania Przechwytywanie programistyczne w aplikacjach korzystających z wcześniejszych wersji programu DirectX na Windows 8.0, zobacz [Przechwytywanie programistyczne w Windows 8.0 i starszych](#CaptureDX11_1) później w tym przewodniku.  
  
 W tej sekcji przedstawiono sposób wykonywania tych zadań:  
  
- Przygotowywanie aplikacji do użycia przechwycenie programowe  
  
- Pobieranie interfejsu IDXGraphicsAnalysis  
  
- Przechwytywanie informacji graficznych  
  
> [!NOTE]
> Poprzednich implementacjach funkcji Przechwytywanie programistyczne polegać Remote Tools for [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] umożliwiają korzystanie z funkcji przechwytywania, Windows 8.1 obsługuje przechwytywanie bezpośrednio za pomocą Direct3D 11.2. W rezultacie masz już zainstalował Remote Tools for Przechwytywanie programistyczne na Windows 8.1.  
  
### <a name="preparing-your-app-to-use-programmatic-capture"></a>Przygotowywanie aplikacji do użycia przechwycenie programowe  
 Aby użyć Przechwytywanie programistyczne w swojej aplikacji, musi on zawierać niezbędne nagłówki. Tych nagłówków są częścią zestawu SDK Windows 8.1.  
  
##### <a name="to-include-programmatic-capture-headers"></a>Aby uwzględnić nagłówki przechwycenie programowe  
  
- Obejmują tych nagłówków w pliku źródłowym, w którym będą definiować interfejsu IDXGraphicsAnalysis:  
  
    ```  
    #include <DXGItype.h>  
    #include <dxgi1_2.h>  
    #include <dxgi1_3.h>  
    #include <DXProgrammableCapture.h>  
    ```  
  
    > [!IMPORTANT]
    > Nie dołączaj nagłówka pliku vsgcapture.h—which obsługuje przechwytywanie programistyczne w Windows 8.0 i wcześniej — przeprowadzić Przechwytywanie programistyczne w aplikacjach Windows 8.1. Tego pliku nagłówkowego jest niezgodna z DirectX 11.2. Jeśli ten plik jest po nagłówku d3d11_2.h jest dołączony, kompilator generuje ostrzeżenie. Jeśli vsgcapture.h znajduje się przed d3d11_2.h, aplikacja nie zostanie uruchomiona.  
  
    > [!NOTE]
    > Jeśli czerwca 2010 DirectX SDK jest zainstalowany na komputerze i zawiera ścieżki dołączania projektu `%DXSDK_DIR%includex86`, przenieś go do końca ścieżki include. Zrób to samo dla Twojej ścieżki biblioteki.  
  
#### <a name="windows-phone-81"></a>Windows Phone 8,1  
 Ponieważ zestaw Windows Phone 8.1 SDK nie zawiera nagłówka DXProgrammableCapture.h, musisz zdefiniować `IDXGraphicsAnalysis` interfejs samodzielnie, tak aby można było używać `BeginCapture()` i `EndCapture()` metody. Obejmują innych nagłówków, zgodnie z opisem w poprzedniej sekcji.  
  
###### <a name="to-define-the-idxgraphicsanalysis-interface"></a>Aby zdefiniować interfejs IDXGraphicsAnalysis  
  
- Zdefiniuj interfejs IDXGraphicsAnalysis, w tym samym pliku, w której są uwzględniane pliki nagłówkowe.  
  
  ```  
  interface DECLSPEC_UUID("9f251514-9d4d-4902-9d60-18988ab7d4b5") DECLSPEC_NOVTABLE  
  IDXGraphicsAnalysis : public IUnknown  
  {  
      STDMETHOD_(void, BeginCapture)() PURE;  
      STDMETHOD_(void, EndCapture)() PURE;  
  };  
  ```  
  
  Dla wygody można wykonać te kroki w nowym pliku nagłówka, a następnie dołącz ją w razie potrzeby w swojej aplikacji.  
  
### <a name="getting-the-idxgraphicsanalysis-interface"></a>Pobieranie interfejsu IDXGraphicsAnalysis  
 Zanim będzie można przechwytywać informacje graficzne z DirectX 11.2, musisz uzyskać DXGI interfejsu debugowania.  
  
> [!IMPORTANT]
> Korzystając z Przechwytywanie programistyczne, nadal należy uruchomić aplikację pod nadzorem diagnostyki grafiki (Alt + F5 w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]) lub w obszarze [narzędzia wiersza polecenia do przechwytywania](../debugger/command-line-capture-tool.md).  
  
##### <a name="to-get-the-idxgraphicsanalysis-interface"></a>Aby uzyskać interfejs IDXGraphicsAnalysis  
  
- Użyj poniższego kodu, można dołączyć interfejsu IDXGraphicsAnalysis do interfejsu debugowania DXGI.  
  
    ```  
    IDXGraphicsAnalysis* pGraphicsAnalysis;  
    HRESULT getAnalysis = DXGIGetDebugInterface1(0, __uuidof(pGraphicsAnalysis), reinterpret_cast<void**>(&pGraphicsAnalysis));  
    ```  
  
     Należy koniecznie sprawdzić `HRESULT` zwrócone przez `DXGIGetDebugInterface1` aby upewnić się, Uzyskaj prawidłowy interfejs przed jego użyciem:  
  
    ```  
    if (FAILED(getAnalysis))  
    {  
        // Abort program or disable programmatic capture in your app.  
    }  
    ```  
  
    > [!NOTE]
    > Jeśli `DXGIGetDebugInterface1` zwraca `E_NOINTERFACE` (`error: E_NOINTERFACE No such interface supported`), upewnij się, że aplikacja jest uruchomiona w ramach diagnostyki grafiki (Alt + F5 w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]).  
  
### <a name="capturing-graphics-information"></a>Przechwytywanie informacji graficznych  
 Teraz, gdy masz prawidłową `IDXGraphicsAnalysis` interfejsu, można użyć `BeginCapture` i `EndCapture` do przechwytywania informacji graficznych.  
  
##### <a name="to-capture-graphics-information"></a>Do przechwytywania informacji graficznych  
  
- Aby rozpocząć, przechwytywanie informacji graficznych, użyj `BeginCapture`:  
  
    ```  
    ...  
    pGraphicsAnalysis->BeginCapture();  
    ...  
    ```  
  
     Przechwytywania rozpocznie się natychmiast po `BeginCapture` jest wywoływana funkcja nie czeka następnej ramki rozpocząć. Przechwytywanie zatrzymuje umieszczeniem bieżącej ramki, lub gdy wywołujesz `EndCapture`:  
  
    ```  
    ...  
    pGraphicsAnalysis->EndCapture();  
    ...  
    ```  
  
## <a name="CaptureDX11_1"></a> Przechwytywanie programistyczne w Windows 8.0 i starszych  
 Tej części instruktażu pokazano Przechwytywanie programistyczne w aplikacjach dla Windows 8.0 i starszych, korzystających z technologii DirectX 11.1 interfejsu API, który używa metody przechwytywania starszej wersji. Aby uzyskać informacje o sposobie używania Przechwytywanie programistyczne w aplikacjach korzystających z technologii DirectX 11.2 na Windows 8.1, zobacz [Programmatic przechwytywania w Windows 8.1](#CaptureDX11_2) wcześniej w tym przewodniku.  
  
 Ta część zawiera następujące zadania:  
  
- Trwa przygotowywanie komputera do użycia przechwycenie programowe  
  
- Przygotowywanie aplikacji do użycia przechwycenie programowe  
  
- Konfigurowanie nazwę i lokalizację pliku dziennika grafiki  
  
- Za pomocą `CaptureCurrentFrame` interfejsu API  
  
### <a name="preparing-your-computer-to-use-programmatic-capture"></a>Trwa przygotowywanie komputera do użycia przechwycenie programowe  
 Przechwytywanie programistyczne interfejsu API używa Remote Tools for [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] umożliwiają korzystanie z funkcji przechwytywania. Na komputerze, gdzie aplikacja będzie uruchamiana musi być remote tools, które są zainstalowane, nawet wtedy, gdy używasz Przechwytywanie programistyczne na komputerze lokalnym. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nie musi być uruchomiona, gdy wykonujesz Przechwytywanie programistyczne na komputerze lokalnym.  
  
 Aby używać zdalnego przechwytywania interfejsów API w aplikacji, która jest uruchomiona na komputerze, najpierw musisz zainstalować Remote Tools for [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] na tym komputerze. Różne wersje narzędzia zdalnej obsługi innych platform sprzętowych. Aby uzyskać informacje o sposobie instalowania narzędzi remote tools, zobacz [stronę pobierania narzędzia zdalnej](http://go.microsoft.com/fwlink/p/?LinkId=246691) w programie Microsoft pobierania witryny sieci Web.  
  
 Alternatywnie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] instaluje składniki niezbędne do przeprowadzenia zdalnego przechwytywania aplikacji 32-bitowych.  
  
> [!NOTE]
> Ponieważ większość aplikacji komputerowych Windows — w tym [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]— nie są obsługiwane w [!INCLUDE[win8](../includes/win8-md.md)] dla urządzeń ARM przy użyciu Remote Tools for [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] wraz z Przechwytywanie programistyczne interfejs API jest jedynym sposobem, aby przechwycić diagnostyki grafiki na urządzeniach ARM.  
  
### <a name="preparing-your-app-to-use-programmatic-capture"></a>Przygotowywanie aplikacji do użycia przechwycenie programowe  
 Aby korzystać z narzędzi programu Graphics Diagnostics, najpierw musisz przechwytywanie informacji graficznych, która opiera się na. Informacje można programowo Przechwyć, używając `CaptureCurrentFrame` interfejsu API.  
  
##### <a name="to-prepare-your-app-to-capture-graphics-information-programmatically"></a>Aby przygotować aplikację do programowe przechwytywanie informacji graficznych  
  
1. Upewnij się, że `vsgcapture.h` nagłówka znajduje się w kodzie źródłowym aplikacji. Może on być uwzględniony w tylko jednej lokalizacji — na przykład w pliku kodu źródłowego, na którym będzie wywoływać programowych Przechwytywanie interfejsu API — lub w pliku wstępnie skompilowanego nagłówka do wywołania interfejsu API z wielu plików kodu.  
  
2. W kodzie źródłowym aplikacji, w każdym przypadku, gdy mają być przechwytywane w pozostałej części bieżącej ramki, wywołaj `g_pVsgDbg->CaptureCurrentFrame()`. Ta metoda nie przyjmuje żadnych parametrów i nie zwraca wartości.  
  
### <a name="configuring-the-name-and-location-of-the-graphics-log-file"></a>Konfigurowanie nazwę i lokalizację pliku dziennika grafiki  
 Dziennik grafiki jest tworzony w lokalizacji, który jest definiowany przez `DONT_SAVE_VSGLOG_TO_TEMP` i `VSG_DEFAULT_RUN_FILENAME` makra.  
  
##### <a name="to-configure-the-name-and-location-of-the-graphics-log-file"></a>Aby skonfigurować nazwę i lokalizację pliku dziennika grafiki  
  
- Aby zapobiec przed zapisaniem do katalogu tymczasowego dziennika grafiki `#include <vsgcapture.h>` wiersz, dodaj to:  
  
  ```  
  #define DONT_SAVE_VSGLOG_TO_TEMP  
  ```  
  
   Można zdefiniować tę wartość, aby zapisać w dzienniku grafiki do lokalizacji, która jest określana względem katalogu roboczego lub do ścieżki bezwzględnej Jeśli definicja `VSG_DEFAULT_RUN_FILENAME` jest ścieżką bezwzględną.  
  
- Aby zapisać dziennik grafiki do innej lokalizacji, lub nadać mu inną nazwę pliku, zanim `#include <vsgcapture.h>` wiersz, dodaj to:  
  
  ```  
  #define VSG_DEFAULT_RUN_FILENAME <filename>  
  ```  
  
   Jeśli nie możesz wykonać ten krok, nazwa pliku jest default.vsglog. Jeżeli nie zdefiniujesz `DONT_SAVE_VSGLOG_TO_TEMP`, następnie lokalizacja pliku jest względną dla katalogu temp; w przeciwnym, jest względem katalogu roboczego lub w innej lokalizacji, jeśli określono bezwzględnej nazwy pliku.  
  
  Aby uzyskać [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikacji, lokalizację katalogu temp jest przeznaczony dla każdego użytkownika i aplikacji i zwykle znajduje się w lokalizacji takiej jak C:\users\\*username*\AppData\Local\Packages\\ *nazwy rodziny pakietów*\TempState\\. Dla aplikacji komputerowych, lokalizację katalogu temp jest specyficzne dla poszczególnych użytkowników i zwykle znajduje się w lokalizacji takiej jak C:\Users\\*username*\AppData\Local\Temp\\.  
  
> [!NOTE]
> Aby zapisać w określonej lokalizacji, musi mieć uprawnienia do zapisu w tej lokalizacji; w przeciwnym razie wystąpi błąd. Należy pamiętać, że [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikacje są bardziej ograniczone niż aplikacje komputerowe, o których one mogła zapisywać dane i mogą wymagać dodatkowej konfiguracji do zapisu w określonych lokalizacjach.  
  
### <a name="capturing-the-graphics-information"></a>Przechwytywanie informacji graficznych  
 Po przygotowanie aplikacji do Przechwytywanie programistyczne i opcjonalnie skonfigurować lokalizację i nazwę grafiki pliku dziennika, tworzenie aplikacji i następnie uruchamiania lub debugowania go do przechwycenia danych. nie należy uruchamiać narzędzie Diagnostyka grafiki z [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zastosowania Przechwytywanie programistyczne interfejsu API. Dziennik grafiki jest zapisywany do określonej lokalizacji. Jeśli chcesz zachować tę wersję dziennika, przenieś go do innej lokalizacji. w przeciwnym razie zostanie zastąpiony, gdy ponownie uruchom aplikację.  
  
> [!TIP]
> Możesz nadal przechwytywać informacje graficzne ręcznie podczas korzystania z przechwycenie programowe — za pomocą aplikacji w trybie koncentracji uwagi, wystarczy nacisnąć klawisz **klawisza Print Screen**. Ta metoda służy do przechwytywania informacji graficznych dodatkowe, które nie są przechwytywane przez Przechwytywanie programistyczne interfejsu API.  
  
## <a name="next-steps"></a>Następne kroki  
 W tym instruktażu zademonstrowano programowe przechwytywanie informacji graficznych. Kolejnym krokiem Rozważ użycie tej opcji:  
  
- Dowiedz się, jak analizować przechwycone informacje graficzne, przy użyciu narzędzi programu Graphics Diagnostics. Zobacz [Przegląd](../debugger/overview-of-visual-studio-graphics-diagnostics.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik: Przechwytywanie informacji graficznych](../debugger/walkthrough-capturing-graphics-information.md)   
 [Przechwytywanie informacji graficznych](../debugger/capturing-graphics-information.md)   
 [Narzędzie wiersza polecenia do przechwytywania](../debugger/command-line-capture-tool.md)
