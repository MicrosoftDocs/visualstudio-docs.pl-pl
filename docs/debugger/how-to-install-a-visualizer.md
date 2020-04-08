---
title: 'Jak: Instalowanie wizualizatora | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, visualizers
- visualizers, installing
ms.assetid: 3310ef43-515c-4d97-b0f9-51047247d3da
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 499d644cc8374b070cedaf058b0e4dc17d155bdc
ms.sourcegitcommit: 5d1b2895d3a249c6bea30eb12b0ad7c0f0862d85
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2020
ms.locfileid: "80880263"
---
# <a name="how-to-install-a-visualizer"></a>Porady: instalacja programu Visualizer
Po utworzeniu wizualizatora należy zainstalować wizualizator, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]aby był dostępny w programie . Instalacja wizualizatora jest prostym procesem.

> [!NOTE]
> W aplikacjach platformy uniwersalnej systemu Windows obsługiwane są tylko standardowe wizualizatory tekstu, HTML, XML i JSON. Niestandardowe wizualizatory (utworzone przez użytkownika) nie są obsługiwane.

::: moniker range=">=vs-2019"
### <a name="to-install-a-visualizer-for-visual-studio-2019"></a>Aby zainstalować wizualizator dla programu Visual Studio 2019
  
1. Znajdź bibliotekę DLL zawierającą wizualizator, który został utworzony.

   Zazwyczaj najlepiej jest, jeśli zarówno biblioteka DLL po stronie debugowania, jak i biblioteka DLL po stronie debuggee określają **dowolny procesor CPU** jako platformę docelową. Biblioteka DLL po stronie debugera musi być **dowolną jednostką CPU** lub **32-bitową**. Platforma docelowa dla biblioteki DLL po stronie debuggee powinna odpowiadać procesowi debugee.

2. Skopiuj bibliotekę DLL [po stronie debugera](create-custom-visualizers-of-data.md#to-create-the-debugger-side) (i dowolnych bibliotek DLL, od których zależy) do jednej z następujących lokalizacji:

    - *Ścieżka wizualna*`\Common7\Packages\Debugger\Visualizers`

    - `My Documents\`*VisualStudioVersion (VisualStudioVersion)*`\Visualizers`
    
3. Skopiuj bibliotekę DLL [po stronie debuggee](create-custom-visualizers-of-data.md#to-create-the-debuggee-side) do jednej z następujących lokalizacji:

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers\` *Framework*

    - `My Documents\`*Struktura VisualStudioVersion* `\Visualizers\` *Framework*

    w przypadku *gdy ramy są:*
    - `net2.0`dla debuggees `.NET Framework` uruchomionego środowiska wykonawczego.
    - `netstandard2.0`dla debuggów przy użyciu `netstandard 2.0` środowiska`.NET Framework v4.6.1+` `.NET Core 2.0+`uruchomieniowego, który obsługuje ( lub ).
    - `netcoreapp`dla debuggees `.NET Core` uruchomionego środowiska wykonawczego. (wsporniki) `.NET Core 2.0+`

4. Uruchom ponownie sesję debugowania.

> [!NOTE]
> Procedura jest inna w programie Visual Studio 2017 i starszych. Zobacz [poprzednią wersję](how-to-install-a-visualizer.md?view=vs-2017) tego artykułu.
::: moniker-end

::: moniker range="vs-2017"
### <a name="to-install-a-visualizer-for-visual-studio-2017-and-older"></a>Aby zainstalować wizualizator dla programu Visual Studio 2017 i starszych

> [!IMPORTANT]
> Tylko wizualizatory programu .NET Framework są obsługiwane w programie Visual Studio 2017 i starszych.

1. Znajdź bibliotekę DLL zawierającą wizualizator, który został utworzony.

2. Skopiuj bibliotekę DLL do jednej z następujących lokalizacji:

    - *Ścieżka wizualna*`\Common7\Packages\Debugger\Visualizers`

    - `My Documents\`*VisualStudioVersion (VisualStudioVersion)*`\Visualizers`

3. Uruchom ponownie sesję debugowania.

> [!NOTE]
> Jeśli chcesz użyć zarządzanego wizualizatora do zdalnego debugowania, skopiuj bibliotekę DLL do tej samej ścieżki na komputerze zdalnym.
::: moniker-end

## <a name="see-also"></a>Zobacz też
- [Tworzenie niestandardowych wizualizatorów](../debugger/create-custom-visualizers-of-data.md)
- [Porady: pisanie wizualizatora](create-custom-visualizers-of-data.md)
