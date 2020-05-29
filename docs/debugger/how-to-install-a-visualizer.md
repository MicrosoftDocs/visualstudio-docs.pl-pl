---
title: 'Instrukcje: Instalowanie wizualizatora | Microsoft Docs'
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
ms.openlocfilehash: c79fd5522447378b879443eb8dccabfe7081af4f
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2020
ms.locfileid: "84183629"
---
# <a name="how-to-install-a-visualizer"></a>Porady: instalacja programu Visualizer
Po utworzeniu wizualizatora należy zainstalować wizualizator, aby był dostępny w programie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Instalowanie wizualizatora jest prostym procesem.

> [!NOTE]
> W aplikacjach platformy UWP obsługiwane są tylko wizualizacje tekstu standardowego, HTML, XML i JSON. Wizualizacje niestandardowe (utworzone przez użytkownika) nie są obsługiwane.

::: moniker range=">=vs-2019"
### <a name="to-install-a-visualizer-for-visual-studio-2019"></a>Aby zainstalować wizualizator dla programu Visual Studio 2019
  
1. Znajdź bibliotekę DLL, która zawiera skompilowany wizualizator.

   Zazwyczaj najlepiej, jeśli zarówno Biblioteka DLL po stronie debugera, jak i Biblioteka DLL debugowanego obiektu określają **dowolny procesor** jako platformę docelową. Biblioteka DLL po stronie debugera musi być **dowolnym procesorem** lub **32-bitowym**. Platforma docelowa dla biblioteki DLL debugowanego obiektu powinna odpowiadać procesowi debugee.

2. Skopiuj bibliotekę DLL [po stronie debugera](create-custom-visualizers-of-data.md#to-create-the-debugger-side) (i wszystkie biblioteki DLL, od których zależy) do jednej z następujących lokalizacji:

    - *VisualStudioInstallPath*`\Common7\Packages\Debugger\Visualizers`

    - `My Documents\`*VisualStudioVersion*`\Visualizers`
    
3. Skopiuj bibliotekę DLL [po stronie debugowanego obiektu](create-custom-visualizers-of-data.md#to-create-the-visualizer-object-source-for-the-debuggee-side) do jednej z następujących lokalizacji:

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers\` *Struktura*

    - `My Documents\`*VisualStudioVersion* `\Visualizers\` *Struktura*

    gdzie *Framework* jest:
    - `net2.0`debuggees `.NET Framework` środowiska uruchomieniowego.
    - `netstandard2.0`dla debuggees przy użyciu środowiska uruchomieniowego, które obsługuje program `netstandard 2.0` ( `.NET Framework v4.6.1+` lub `.NET Core 2.0+` ).
    - `netcoreapp`debuggees `.NET Core` środowiska uruchomieniowego. (obsługuje `.NET Core 2.0+` )

4. Uruchom ponownie sesję debugowania.

> [!NOTE]
> Procedura różni się w programie Visual Studio 2017 i starszych. Zobacz [poprzednią wersję](how-to-install-a-visualizer.md?view=vs-2017) tego artykułu.
::: moniker-end

::: moniker range="vs-2017"
### <a name="to-install-a-visualizer-for-visual-studio-2017-and-older"></a>Aby zainstalować wizualizator dla programu Visual Studio 2017 i starszej wersji

> [!IMPORTANT]
> Tylko Wizualizatory .NET Framework są obsługiwane w programie Visual Studio 2017 i starszych.

1. Znajdź bibliotekę DLL, która zawiera skompilowany wizualizator.

2. Skopiuj bibliotekę DLL do jednej z następujących lokalizacji:

    - *VisualStudioInstallPath*`\Common7\Packages\Debugger\Visualizers`

    - `My Documents\`*VisualStudioVersion*`\Visualizers`

3. Uruchom ponownie sesję debugowania.

> [!NOTE]
> Jeśli chcesz użyć zarządzanego wizualizatora na potrzeby debugowania zdalnego, Skopiuj bibliotekę DLL do tej samej ścieżki na komputerze zdalnym.
::: moniker-end

## <a name="see-also"></a>Zobacz także
- [Tworzenie niestandardowych wizualizatorów](../debugger/create-custom-visualizers-of-data.md)
- [Porady: pisanie wizualizatora](create-custom-visualizers-of-data.md)
