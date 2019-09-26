---
title: 'Przewodnik: Programistyczne Przechwytywanie informacji graficznych | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 187328e4ef4d1de0c865120400f84e65385160fc
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "71252894"
---
# <a name="walkthrough-capturing-graphics-information-programmatically"></a>Przewodnik: programowe przechwytywanie informacji graficznych
Diagnostyka grafiki umożliwia programowe [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Przechwytywanie informacji graficznych z aplikacji Direct3D.

Przechwytywanie programistyczne jest przydatne w scenariuszach takich jak:

- Zacznij przechwycić program programowo, gdy aplikacja graficzna nie używa swapchain, na przykład podczas renderowania do tekstury.

- Rozpocznij przechwytywanie programowo, gdy aplikacja nie jest w ogóle renderowana, na przykład gdy używa DirectCompute do wykonywania obliczeń.

- Wywoływanie `CaptureCurrentFrame`, gdy problem z renderowaniem jest trudny do przewidzenia i przechwycenia w testowaniu ręcznym, ale można go przewidzieć programowo przy użyciu informacji o stanie aplikacji w czasie wykonywania.

## <a name="CaptureDX11_2"></a>Przechwycenie programowe w systemie Windows 10
Ta część przewodnika przedstawia programowe przechwytywanie w aplikacjach korzystających z interfejsu API DirectX 11,2 w systemie Windows 10, który używa niezawodnej metody przechwytywania.

W tej sekcji przedstawiono sposób wykonywania następujących zadań:

- Przygotowywanie aplikacji do korzystania z funkcji przechwytywania programistycznego

- Pobieranie interfejsu IDXGraphicsAnalysis

- Przechwytywanie informacji graficznych

> [!NOTE]
> Poprzednie implementacje funkcji przechwytywania programistycznego, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] które opierają się na Remote Tools for Visual Studio, aby zapewnić funkcje przechwytywania.

### <a name="preparing-your-app-to-use-programmatic-capture"></a>Przygotowywanie aplikacji do korzystania z funkcji przechwytywania programistycznego
Aby użyć funkcji przechwytywania programistycznego w aplikacji, musi ona zawierać niezbędne nagłówki. Te nagłówki są częścią zestawu SDK systemu Windows 10.

##### <a name="to-include-programmatic-capture-headers"></a>Aby dołączyć nagłówki przechwytywania programistycznego

- Dołącz te nagłówki do pliku źródłowego, w którym określisz interfejs IDXGraphicsAnalysis:

    ```cpp
    #include <DXGItype.h>
    #include <dxgi1_2.h>
    #include <dxgi1_3.h>
    #include <DXProgrammableCapture.h>
    ```

    > [!IMPORTANT]
    > Nie dołączaj pliku nagłówkowego vsgcapture. h — który obsługuje funkcję przechwytywania programowego w systemie Windows 8,0 i wcześniejszych — aby przeprowadzić funkcję przechwytywania programistycznego w aplikacjach systemu Windows 10. Ten nagłówek jest niezgodny z DirectX 11,2. Jeśli ten plik zostanie uwzględniony po dołączeniu nagłówka d3d11_2. h, kompilator generuje ostrzeżenie. Jeśli vsgcapture. h jest dołączony przed d3d11_2. h, aplikacja nie zostanie uruchomiona.

    > [!NOTE]
    > Jeśli na maszynie jest zainstalowany zestaw SDK programu DirectX 2010 dla czerwca, a ścieżka dołączania `%DXSDK_DIR%includex86`projektu zawiera, przenieś ją na koniec ścieżki dołączania. Wykonaj te same czynności dla ścieżki biblioteki.

### <a name="getting-the-idxgraphicsanalysis-interface"></a>Pobieranie interfejsu IDXGraphicsAnalysis
Aby można było przechwycić informacje graficzne z programu DirectX 11,2, należy uzyskać interfejs debugowania infrastruktury DXGI.

> [!IMPORTANT]
> W przypadku korzystania z funkcji przechwytywania programistycznego należy nadal uruchamiać aplikację w obszarze Diagnostyka grafiki (Alt + [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]F5) lub w [narzędziu do przechwytywania wiersza polecenia](command-line-capture-tool.md).

##### <a name="to-get-the-idxgraphicsanalysis-interface"></a>Aby uzyskać interfejs IDXGraphicsAnalysis

- Użyj poniższego kodu, aby podłączyć interfejs IDXGraphicsAnalysis do interfejsu debugowania infrastruktury DXGI.

  ```cpp
  IDXGraphicsAnalysis* pGraphicsAnalysis;
  HRESULT getAnalysis = DXGIGetDebugInterface1(0, __uuidof(pGraphicsAnalysis), reinterpret_cast<void**>(&pGraphicsAnalysis));
  ```

  Pamiętaj, `HRESULT` aby sprawdzić poprawność przez [DXGIGetDebugInterface1](/windows/desktop/api/dxgi1_3/nf-dxgi1_3-dxgigetdebuginterface1) , aby upewnić się, że otrzymasz prawidłowy interfejs, zanim go użyjesz:

  ```cpp
  if (FAILED(getAnalysis))
  {
      // Abort program or disable programmatic capture in your app.
  }
  ```

  > [!NOTE]
  > Jeśli `DXGIGetDebugInterface1` zwraca `E_NOINTERFACE` [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)](),upewnijsię,żeaplikacjadziaławramachdiagnostykigrafiki(Alt+F5).`error: E_NOINTERFACE No such interface supported`

### <a name="capturing-graphics-information"></a>Przechwytywanie informacji graficznych
Teraz, gdy masz prawidłowy `IDXGraphicsAnalysis` interfejs, możesz użyć `BeginCapture` funkcji i `EndCapture` do przechwytywania informacji graficznych.

##### <a name="to-capture-graphics-information"></a>Aby przechwycić informacje graficzne

- Aby rozpocząć przechwytywanie informacji graficznych, użyj `BeginCapture`:

    ```cpp
    ...
    pGraphicsAnalysis->BeginCapture();
    ...
    ```

    Przechwytywanie rozpocznie się `BeginCapture` natychmiast po wywołaniu; nie czeka na rozpoczęcie następnej klatki. Przechwytywanie jest zatrzymywane po wyświetleniu bieżącej ramki lub wywołaniu `EndCapture`:

    ```cpp
    ...
    pGraphicsAnalysis->EndCapture();
    ...
    ```

- Po wywołaniu `EndCapture`, zwolnij obiekt Graphics.

## <a name="next-steps"></a>Następne kroki
W tym instruktażu przedstawiono sposób programistycznego przechwytywania informacji graficznych. W następnym kroku należy wziąć pod uwagę tę opcję:

- Dowiedz się, jak analizować przechwycone informacje graficzne przy użyciu narzędzi Diagnostyka grafiki. Zobacz [Omówienie](overview-of-visual-studio-graphics-diagnostics.md).

## <a name="see-also"></a>Zobacz też
- [Przewodnik: Przechwytywanie informacji graficznych](walkthrough-capturing-graphics-information.md)
- [Przechwytywanie informacji graficznych](capturing-graphics-information.md)
- [Narzędzie wiersza polecenia do przechwytywania](command-line-capture-tool.md)
