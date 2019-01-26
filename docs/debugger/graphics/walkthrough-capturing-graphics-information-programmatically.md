---
title: 'Przewodnik: Programowe przechwytywanie informacji graficznych | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 379180c21bfe1bbb36faa0ad1becad162068e698
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55001189"
---
# <a name="walkthrough-capturing-graphics-information-programmatically"></a>Przewodnik: Programowe przechwytywanie informacji graficznych
Możesz użyć [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] diagnostyki grafiki, aby programowo przechwytywać informacje graficzne z aplikacji Direct3D.  
  
 Przechwytywanie programistyczne jest przydatne w scenariuszach takich jak:  
  
-   Po grafiki nie korzysta z swapchain obecny, takie jak po renderowaniu produktu do tekstury programowo rozpocząć przechwytywania.  
  
-   Po aplikacji nie renderuje, takie jak kiedy używa DirectCompute do wykonywania obliczeń programistycznie rozpocząć przechwytywania.  
  
-   Wywołaj `CaptureCurrentFrame`po z problemem renderowania jest trudny do przewidywania i przechwytywania podczas testowania ręcznego, ale można przewidzieć programowo przy użyciu informacji o stanie aplikacji w czasie wykonywania.  
  
##  <a name="CaptureDX11_2"></a> Przechwytywanie programistyczne w systemie Windows 10  
 Tej części instruktażu pokazano Przechwytywanie programistyczne w aplikacjach korzystających z interfejsu API programu DirectX 11.2 w systemie Windows 10, który używa metody przechwytywania niezawodne.
  
 W tej sekcji przedstawiono sposób wykonywania tych zadań:  
  
-   Przygotowywanie aplikacji do użycia przechwycenie programowe  
  
-   Pobieranie interfejsu IDXGraphicsAnalysis  
  
-   Przechwytywanie informacji graficznych  
  
> [!NOTE]
>  Poprzednich implementacjach funkcji Przechwytywanie programistyczne polegać Remote Tools for Visual Studio dla [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] umożliwiają korzystanie z funkcji przechwytywania.
  
### <a name="preparing-your-app-to-use-programmatic-capture"></a>Przygotowywanie aplikacji do użycia przechwycenie programowe  
 Aby użyć Przechwytywanie programistyczne w swojej aplikacji, musi on zawierać niezbędne nagłówki. Tych nagłówków są częścią zestawu Windows 10 SDK.  
  
##### <a name="to-include-programmatic-capture-headers"></a>Aby uwzględnić nagłówki przechwycenie programowe  
  
-   Obejmują tych nagłówków w pliku źródłowym, w którym będą definiować interfejsu IDXGraphicsAnalysis:  
  
    ```cpp
    #include <DXGItype.h>  
    #include <dxgi1_2.h>  
    #include <dxgi1_3.h>  
    #include <DXProgrammableCapture.h>  
    ```  
  
    > [!IMPORTANT]
    >  Nie dołączaj nagłówka pliku vsgcapture.h—which obsługuje przechwytywanie programistyczne w Windows 8.0 i wcześniej — przeprowadzić Przechwytywanie programistyczne w aplikacjach systemu Windows 10. Tego pliku nagłówkowego jest niezgodna z DirectX 11.2. Jeśli ten plik jest po nagłówku d3d11_2.h jest dołączony, kompilator generuje ostrzeżenie. Jeśli vsgcapture.h znajduje się przed d3d11_2.h, aplikacja nie zostanie uruchomiona.  
  
    > [!NOTE]
    >  Jeśli czerwca 2010 DirectX SDK jest zainstalowany na komputerze i zawiera ścieżki dołączania projektu `%DXSDK_DIR%includex86`, przenieś go do końca ścieżki include. Zrób to samo dla Twojej ścieżki biblioteki.  
  
### <a name="getting-the-idxgraphicsanalysis-interface"></a>Pobieranie interfejsu IDXGraphicsAnalysis  
 Zanim będzie można przechwytywać informacje graficzne z DirectX 11.2, musisz uzyskać DXGI interfejsu debugowania.  
  
> [!IMPORTANT]
>  Korzystając z Przechwytywanie programistyczne, nadal należy uruchomić aplikację pod nadzorem diagnostyki grafiki (Alt + F5 w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]) lub w obszarze [narzędzia wiersza polecenia do przechwytywania](command-line-capture-tool.md).  
  
##### <a name="to-get-the-idxgraphicsanalysis-interface"></a>Aby uzyskać interfejs IDXGraphicsAnalysis  
  
- Użyj poniższego kodu, można dołączyć interfejsu IDXGraphicsAnalysis do interfejsu debugowania DXGI.  
  
  ```cpp
  IDXGraphicsAnalysis* pGraphicsAnalysis;  
  HRESULT getAnalysis = DXGIGetDebugInterface1(0, __uuidof(pGraphicsAnalysis), reinterpret_cast<void**>(&pGraphicsAnalysis));  
  ```  
  
   Należy koniecznie sprawdzić `HRESULT` zwrócone przez [DXGIGetDebugInterface1](/windows/desktop/api/dxgi1_3/nf-dxgi1_3-dxgigetdebuginterface1) aby upewnić się, Uzyskaj prawidłowy interfejs przed jego użyciem:  
  
  ```cpp
  if (FAILED(getAnalysis))  
  {  
      // Abort program or disable programmatic capture in your app.  
  }  
  ```  
  
  > [!NOTE]
  >  Jeśli `DXGIGetDebugInterface1` zwraca `E_NOINTERFACE` (`error: E_NOINTERFACE No such interface supported`), upewnij się, że aplikacja jest uruchomiona w ramach diagnostyki grafiki (Alt + F5 w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]).  
  
### <a name="capturing-graphics-information"></a>Przechwytywanie informacji graficznych  
 Teraz, gdy masz prawidłową `IDXGraphicsAnalysis` interfejsu, można użyć `BeginCapture` i `EndCapture` do przechwytywania informacji graficznych.  
  
##### <a name="to-capture-graphics-information"></a>Do przechwytywania informacji graficznych  
  
- Aby rozpocząć, przechwytywanie informacji graficznych, użyj `BeginCapture`:  
  
    ```cpp
    ...  
    pGraphicsAnalysis->BeginCapture();  
    ...  
    ```  
  
     Przechwytywania rozpocznie się natychmiast po `BeginCapture` jest wywoływana funkcja nie czeka następnej ramki rozpocząć. Przechwytywanie zatrzymuje umieszczeniem bieżącej ramki, lub gdy wywołujesz `EndCapture`:  
  
    ```cpp
    ...  
    pGraphicsAnalysis->EndCapture();  
    ...  
    ```  

- Po wywołaniu `EndCapture`, zwolnij obiekt grafiki. 
  
## <a name="next-steps"></a>Następne kroki  
 W tym instruktażu zademonstrowano programowe przechwytywanie informacji graficznych. Kolejnym krokiem Rozważ użycie tej opcji:  
  
-   Dowiedz się, jak analizować przechwycone informacje graficzne, przy użyciu narzędzi programu Graphics Diagnostics. Zobacz [Przegląd](overview-of-visual-studio-graphics-diagnostics.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik: Przechwytywanie informacji graficznych](walkthrough-capturing-graphics-information.md)   
 [Przechwytywanie informacji graficznych](capturing-graphics-information.md)   
 [Narzędzie wiersza polecenia do przechwytywania](command-line-capture-tool.md)
