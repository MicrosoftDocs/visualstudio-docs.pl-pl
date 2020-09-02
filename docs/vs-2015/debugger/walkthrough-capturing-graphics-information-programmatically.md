---
title: 'Przewodnik: programowe Przechwytywanie informacji graficznych | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: a5adeff9-afaf-4047-b5ce-ef0aefe710eb
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9de8e2a2ee69911f5505937494d2912c724326e9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75847812"
---
# <a name="walkthrough-capturing-graphics-information-programmatically"></a>Przewodnik: programowe przechwytywanie informacji graficznych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diagnostyka grafiki umożliwia programowe [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Przechwytywanie informacji graficznych z aplikacji Direct3D.  
  
 Przechwytywanie programistyczne jest przydatne w scenariuszach takich jak:  
  
- Zacznij przechwycić program programowo, gdy aplikacja graficzna nie używa swapchain, na przykład podczas renderowania do tekstury.  
  
- Rozpocznij przechwytywanie programowo, gdy aplikacja nie jest w ogóle renderowana, na przykład gdy używa DirectCompute do wykonywania obliczeń.  
  
- Wywoływanie `CaptureCurrentFrame` , gdy problem z renderowaniem jest trudny do przewidzenia i przechwycenia w testowaniu ręcznym, ale można go przewidzieć programowo przy użyciu informacji o stanie aplikacji w czasie wykonywania.  
  
## <a name="programmatic-capture-in-windows-81"></a><a name="CaptureDX11_2"></a> Przechwycenie programowe w Windows 8.1  
 W tej części przewodnika przedstawiono funkcję przechwytywania programowego w aplikacjach korzystających z interfejsu API DirectX 11,2 na Windows 8.1, który korzysta z niezawodnej metody przechwytywania. Informacje o sposobach używania funkcji przechwytywania programowego w aplikacjach korzystających z wcześniejszych wersji programu DirectX w systemie Windows 8,0 znajdują się w temacie programowe [przechwytywanie w systemie windows 8,0 i wcześniejszym](#CaptureDX11_1) w dalszej części tego przewodnika.  
  
 W tej sekcji przedstawiono sposób wykonywania następujących zadań:  
  
- Przygotowywanie aplikacji do korzystania z funkcji przechwytywania programistycznego  
  
- Pobieranie interfejsu IDXGraphicsAnalysis  
  
- Przechwytywanie informacji graficznych  
  
> [!NOTE]
> Poprzednie implementacje funkcji przechwytywania programistycznego korzystające z narzędzi zdalnych dla [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] programu w celu zapewnienia funkcji przechwytywania, Windows 8.1 obsługują przechwytywanie bezpośrednio przez program Direct3D 11,2. W związku z tym nie trzeba już instalować zdalnych narzędzi do przechwytywania programowego na Windows 8.1.  
  
### <a name="preparing-your-app-to-use-programmatic-capture"></a>Przygotowywanie aplikacji do korzystania z funkcji przechwytywania programistycznego  
 Aby użyć funkcji przechwytywania programistycznego w aplikacji, musi ona zawierać niezbędne nagłówki. Te nagłówki są częścią zestawu SDK Windows 8.1.  
  
##### <a name="to-include-programmatic-capture-headers"></a>Aby dołączyć nagłówki przechwytywania programistycznego  
  
- Dołącz te nagłówki do pliku źródłowego, w którym określisz interfejs IDXGraphicsAnalysis:  
  
    ```  
    #include <DXGItype.h>  
    #include <dxgi1_2.h>  
    #include <dxgi1_3.h>  
    #include <DXProgrammableCapture.h>  
    ```  
  
    > [!IMPORTANT]
    > Nie dołączaj pliku nagłówkowego vsgcapture. h — który obsługuje funkcję przechwytywania programowego w systemie Windows 8,0 i starszych wersjach, aby przeprowadzić funkcję przechwytywania programistycznego w aplikacjach Windows 8.1. Ten nagłówek jest niezgodny z DirectX 11,2. Jeśli ten plik zostanie uwzględniony po dołączeniu nagłówka d3d11_2. h, kompilator generuje ostrzeżenie. Jeśli vsgcapture. h jest dołączony przed d3d11_2. h, aplikacja nie zostanie uruchomiona.  
  
    > [!NOTE]
    > Jeśli na maszynie jest zainstalowany zestaw SDK programu DirectX 2010 dla czerwca, a ścieżka dołączania projektu zawiera `%DXSDK_DIR%includex86` , przenieś ją na koniec ścieżki dołączania. Wykonaj te same czynności dla ścieżki biblioteki.  
  
#### <a name="windows-phone-81"></a>Windows Phone 8,1  
 Ponieważ zestaw Windows Phone 8,1 SDK nie zawiera nagłówka DXProgrammableCapture. h, należy `IDXGraphicsAnalysis` samodzielnie zdefiniować interfejs, aby można było użyć `BeginCapture()` `EndCapture()` metod i. Dołącz inne nagłówki zgodnie z opisem w poprzedniej sekcji.  
  
###### <a name="to-define-the-idxgraphicsanalysis-interface"></a>Aby zdefiniować interfejs IDXGraphicsAnalysis  
  
- Zdefiniuj interfejs IDXGraphicsAnalysis w tym samym pliku, w którym znajdują się pliki nagłówkowe.  
  
  ```  
  interface DECLSPEC_UUID("9f251514-9d4d-4902-9d60-18988ab7d4b5") DECLSPEC_NOVTABLE  
  IDXGraphicsAnalysis : public IUnknown  
  {  
      STDMETHOD_(void, BeginCapture)() PURE;  
      STDMETHOD_(void, EndCapture)() PURE;  
  };  
  ```  
  
  Dla wygody można wykonać te kroki w nowym pliku nagłówkowym, a następnie dołączyć go do potrzeb aplikacji.  
  
### <a name="getting-the-idxgraphicsanalysis-interface"></a>Pobieranie interfejsu IDXGraphicsAnalysis  
 Aby można było przechwycić informacje graficzne z programu DirectX 11,2, należy uzyskać interfejs debugowania infrastruktury DXGI.  
  
> [!IMPORTANT]
> W przypadku korzystania z funkcji przechwytywania programistycznego należy nadal uruchamiać aplikację w obszarze Diagnostyka grafiki (Alt + F5 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ) lub w [narzędziu do przechwytywania wiersza polecenia](../debugger/command-line-capture-tool.md).  
  
##### <a name="to-get-the-idxgraphicsanalysis-interface"></a>Aby uzyskać interfejs IDXGraphicsAnalysis  
  
- Użyj poniższego kodu, aby podłączyć interfejs IDXGraphicsAnalysis do interfejsu debugowania infrastruktury DXGI.  
  
    ```  
    IDXGraphicsAnalysis* pGraphicsAnalysis;  
    HRESULT getAnalysis = DXGIGetDebugInterface1(0, __uuidof(pGraphicsAnalysis), reinterpret_cast<void**>(&pGraphicsAnalysis));  
    ```  
  
     Pamiętaj, aby `HRESULT` `DXGIGetDebugInterface1` przed użyciem sprawdzić poprawność interfejsu, aby upewnić się, że jest on prawidłowy:  
  
    ```  
    if (FAILED(getAnalysis))  
    {  
        // Abort program or disable programmatic capture in your app.  
    }  
    ```  
  
    > [!NOTE]
    > Jeśli `DXGIGetDebugInterface1` zwraca `E_NOINTERFACE` ( `error: E_NOINTERFACE No such interface supported` ), upewnij się, że aplikacja działa w ramach diagnostyki grafiki (Alt + F5 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ).  
  
### <a name="capturing-graphics-information"></a>Przechwytywanie informacji graficznych  
 Teraz, gdy masz prawidłowy `IDXGraphicsAnalysis` interfejs, możesz użyć `BeginCapture` `EndCapture` funkcji i do przechwytywania informacji graficznych.  
  
##### <a name="to-capture-graphics-information"></a>Aby przechwycić informacje graficzne  
  
- Aby rozpocząć przechwytywanie informacji graficznych, użyj `BeginCapture` :  
  
    ```  
    ...  
    pGraphicsAnalysis->BeginCapture();  
    ...  
    ```  
  
     Przechwytywanie rozpocznie się natychmiast po `BeginCapture` wywołaniu; nie czeka na rozpoczęcie następnej klatki. Przechwytywanie jest zatrzymywane po wyświetleniu bieżącej ramki lub wywołaniu `EndCapture` :  
  
    ```  
    ...  
    pGraphicsAnalysis->EndCapture();  
    ...  
    ```  
  
## <a name="programmatic-capture-in-windows-80-and-earlier"></a><a name="CaptureDX11_1"></a> Przechwycenie programowe w systemie Windows 8,0 i starszych  
 Ta część przewodnika przedstawia programowe przechwytywanie w aplikacjach dla systemu Windows 8,0 i starszych, które używają interfejsu API programu DirectX 11,1, który używa starszej metody przechwytywania. Aby uzyskać informacje dotyczące sposobu korzystania z funkcji przechwytywania programowego w aplikacjach korzystających z programu DirectX 11,2 na Windows 8.1, zobacz Funkcja [przechwytywania programowa w programie Windows 8.1](#CaptureDX11_2) wcześniej w tym instruktażu.  
  
 Ta część zawiera następujące zadania:  
  
- Przygotowywanie komputera do korzystania z funkcji przechwytywania programistycznego  
  
- Przygotowywanie aplikacji do korzystania z funkcji przechwytywania programistycznego  
  
- Konfigurowanie nazwy i lokalizacji pliku dziennika grafiki  
  
- Korzystanie z `CaptureCurrentFrame` interfejsu API  
  
### <a name="preparing-your-computer-to-use-programmatic-capture"></a>Przygotowywanie komputera do korzystania z funkcji przechwytywania programistycznego  
 Interfejs API przechwycenia programistycznego używa narzędzi zdalnych dla programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] w celu zapewnienia funkcji przechwytywania. Na komputerze, na którym zostanie uruchomiona aplikacja, muszą być zainstalowane narzędzia zdalne, nawet jeśli używasz funkcji przechwytywania programowego na komputerze lokalnym. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nie musi być uruchomiona w przypadku wykonywania funkcji przechwytywania programowego na komputerze lokalnym.  
  
 Aby korzystać z interfejsów API przechwytywania zdalnego w aplikacji uruchomionej na komputerze, należy najpierw zainstalować na nim narzędzia zdalne [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Różne wersje narzędzi zdalnych obsługują różne platformy sprzętowe. Aby uzyskać informacje na temat sposobu instalowania narzędzi zdalnych, zobacz [stronę pobierania narzędzi zdalnych](https://visualstudio.microsoft.com/downloads#remote-tools) w witrynie internetowej pobierania firmy Microsoft.  
  
 Alternatywnie program [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] instaluje składniki niezbędne do przeprowadzenia zdalnego przechwytywania dla aplikacji 32-bitowych.  
  
> [!NOTE]
> Ze względu na to, że większość aplikacji klasycznych systemu Windows — [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] w tym — nie są obsługiwane na [!INCLUDE[win8](../includes/win8-md.md)] urządzeniach ARM, korzystanie z zdalnych narzędzi dla programu wraz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] z interfejsem API przechwytywania programistycznego jest jedynym sposobem przechwytywania diagnostyki grafiki na urządzeniach ARM.  
  
### <a name="preparing-your-app-to-use-programmatic-capture"></a>Przygotowywanie aplikacji do korzystania z funkcji przechwytywania programistycznego  
 Aby skorzystać z narzędzi Diagnostyka grafiki, musisz najpierw przechwycić informacje o grafice, na których bazują. Można programowo przechwytywać informacje przy użyciu `CaptureCurrentFrame` interfejsu API.  
  
##### <a name="to-prepare-your-app-to-capture-graphics-information-programmatically"></a>Aby przygotować aplikację do programistycznego przechwytywania informacji graficznych  
  
1. Upewnij się, że `vsgcapture.h` nagłówek jest uwzględniony w kodzie źródłowym aplikacji. Może być zawarta w tylko jednej lokalizacji — na przykład w pliku kodu źródłowego, w którym będzie wywoływany interfejs API przechwytywania programowego — lub w pliku prekompilowanego nagłówka do wywołania interfejsu API z wielu plików kodu źródłowego.  
  
2. W kodzie źródłowym aplikacji, za każdym razem, gdy chcesz przechwycić resztę bieżącej ramki, wywołaj `g_pVsgDbg->CaptureCurrentFrame()` . Ta metoda nie przyjmuje parametrów i nie zwraca wartości.  
  
### <a name="configuring-the-name-and-location-of-the-graphics-log-file"></a>Konfigurowanie nazwy i lokalizacji pliku dziennika grafiki  
 Dziennik grafiki jest tworzony w lokalizacji zdefiniowanej przez `DONT_SAVE_VSGLOG_TO_TEMP` `VSG_DEFAULT_RUN_FILENAME` makro i.  
  
##### <a name="to-configure-the-name-and-location-of-the-graphics-log-file"></a>Aby skonfigurować nazwę i lokalizację pliku dziennika grafiki  
  
- Aby uniemożliwić zapisanie dziennika grafiki w katalogu tymczasowym przed `#include <vsgcapture.h>` wierszem, Dodaj następujące polecenie:  
  
  ```  
  #define DONT_SAVE_VSGLOG_TO_TEMP  
  ```  
  
   Można zdefiniować tę wartość, aby napisać dziennik grafiki do lokalizacji względnej dla katalogu roboczego lub ścieżki bezwzględnej, jeśli definicja `VSG_DEFAULT_RUN_FILENAME` jest ścieżką bezwzględną.  
  
- Aby zapisać dziennik grafiki w innej lokalizacji lub podać inną nazwę pliku przed `#include <vsgcapture.h>` wierszem, Dodaj następujące polecenie:  
  
  ```  
  #define VSG_DEFAULT_RUN_FILENAME <filename>  
  ```  
  
   Jeśli ten krok nie jest wykonywany, nazwa pliku to default. vsglog. Jeśli nie zdefiniowano programu `DONT_SAVE_VSGLOG_TO_TEMP` , lokalizacja pliku jest określana względem katalogu Temp; w przeciwnym razie odnosi się do katalogu roboczego lub w innej lokalizacji, jeśli określono bezwzględną nazwę pliku.  
  
  W przypadku [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikacji Lokalizacja katalogu tymczasowego jest specyficzna dla każdego użytkownika i aplikacji. zazwyczaj znajduje się ona w lokalizacji takiej jak \\ Nazwa użytkownika systemu C:\Users*username*\AppData\Local\Packages \\ *package family name* \\ . W przypadku aplikacji klasycznych Lokalizacja katalogu tymczasowego jest specyficzna dla każdego użytkownika i zwykle znajduje się w lokalizacji, takiej jak C:\Users \\ *username*\AppData\Local\Temp \\ .  
  
> [!NOTE]
> Aby zapisać w określonej lokalizacji, musisz mieć uprawnienia do zapisu w tej lokalizacji. w przeciwnym razie wystąpi błąd. Pamiętaj, że [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikacje są bardziej ograniczone niż aplikacje klasyczne, w których mogą zapisywać dane, i mogą wymagać dodatkowej konfiguracji do zapisu w określonych lokalizacjach.  
  
### <a name="capturing-the-graphics-information"></a>Przechwytywanie informacji graficznych  
 Po przygotowaniu aplikacji do przechwycenia programistycznego i opcjonalnie skonfigurowania lokalizacji i nazwy pliku dziennika grafiki należy skompilować aplikację, a następnie uruchomić lub debugować ją w celu przechwycenia danych. nie uruchamiaj diagnostyki grafiki z programu w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] przypadku korzystania z interfejsu API przechwytywania programowego. Dziennik grafiki zostanie zapisany w określonej lokalizacji. Jeśli chcesz zachować tę wersję dziennika, przenieś ją do innej lokalizacji. w przeciwnym razie zostanie nadpisany po ponownym uruchomieniu aplikacji.  
  
> [!TIP]
> Nadal można przechwytywać informacje graficzne ręcznie podczas korzystania z funkcji przechwytywania programowego — w przypadku aplikacji w fokusie wystarczy nacisnąć przycisk **Drukuj ekran**. Ta technika służy do przechwytywania dodatkowych informacji graficznych, które nie są przechwytywane przez interfejs API przechwytywania programowego.  
  
## <a name="next-steps"></a>Następne kroki  
 W tym instruktażu przedstawiono sposób programistycznego przechwytywania informacji graficznych. W następnym kroku należy wziąć pod uwagę tę opcję:  
  
- Dowiedz się, jak analizować przechwycone informacje graficzne przy użyciu narzędzi Diagnostyka grafiki. Zobacz [Omówienie](../debugger/overview-of-visual-studio-graphics-diagnostics.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik: Przechwytywanie informacji graficznych](../debugger/walkthrough-capturing-graphics-information.md)   
 [Przechwytywanie informacji graficznych](../debugger/capturing-graphics-information.md)   
 [Narzędzie wiersza polecenia do przechwytywania](../debugger/command-line-capture-tool.md)
