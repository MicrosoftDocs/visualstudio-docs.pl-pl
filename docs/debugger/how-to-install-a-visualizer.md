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
ms.openlocfilehash: 1df72c6978f5ab34a86c74dbc1ea349db5aa4457
ms.sourcegitcommit: b5cb0eb09369677514ee1f44d5d7050d34c7fbc1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/26/2019
ms.locfileid: "74491308"
---
# <a name="how-to-install-a-visualizer"></a>Porady: instalacja programu Visualizer
Po utworzeniu wizualizatora należy zainstalować wizualizator, aby był dostępny w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Instalowanie wizualizatora jest prostym procesem.

> [!NOTE]
> W aplikacjach platformy UWP obsługiwane są tylko wizualizacje tekstu standardowego, HTML, XML i JSON. Wizualizacje niestandardowe (utworzone przez użytkownika) nie są obsługiwane.

### <a name="to-install-a-visualizer-for-visual-studio-2019"></a>Aby zainstalować wizualizator dla programu Visual Studio 2019
  
1. Znajdź bibliotekę DLL, która zawiera skompilowany wizualizator.

2. Skopiuj bibliotekę DLL [po stronie debugera](create-custom-visualizers-of-data.md#to-create-the-debugger-side) do jednej z następujących lokalizacji:

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers`

    - `My Documents\` *VisualStudioVersion* `\Visualizers`
    
3. Skopiuj bibliotekę DLL [po stronie debugowanego obiektu](create-custom-visualizers-of-data.md#to-create-the-debuggee-side) do jednej z następujących lokalizacji:

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers\` *Framework*

    - `My Documents\` *VisualStudioVersion* `\Visualizers\` *Framework*

    Gdzie *Framework* jest:
    - `net2.0` dla debuggees, w którym działa środowisko uruchomieniowe `.NET Framework`.
    - `netstandard2.0` dla debuggees przy użyciu środowiska uruchomieniowego obsługującego `netstandard 2.0` (`.NET Framework v4.6.1+` lub `.NET Core 2.0+`).
    - `netcoreapp` dla debuggees, w którym działa środowisko uruchomieniowe `.NET Core`. (obsługuje `.NET Core 2.0+`)

4. Uruchom ponownie sesję debugowania.

### <a name="to-install-a-visualizer-for-visual-studio-2017-and-older"></a>Aby zainstalować wizualizator dla programu Visual Studio 2017 i starszej wersji

> [!IMPORTANT]
> Tylko Wizualizatory .NET Framework są obsługiwane w programie Visual Studio 2017 i starszych

1. Znajdź bibliotekę DLL, która zawiera skompilowany wizualizator.

2. Skopiuj bibliotekę DLL do jednej z następujących lokalizacji:

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers`

    - `My Documents\` *VisualStudioVersion* `\Visualizers`

3. Uruchom ponownie sesję debugowania.

> [!NOTE]
> Jeśli chcesz użyć zarządzanego wizualizatora na potrzeby debugowania zdalnego, Skopiuj bibliotekę DLL do tej samej ścieżki na komputerze zdalnym.

## <a name="see-also"></a>Zobacz także
- [Tworzenie niestandardowych wizualizatorów](../debugger/create-custom-visualizers-of-data.md)
- [Instrukcje: pisanie wizualizatora](create-custom-visualizers-of-data.md)
