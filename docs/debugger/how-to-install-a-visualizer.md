---
title: Instalowanie aplikacji Visualizer | Microsoft Docs
description: Dowiedz się, jak zainstalować wizualizator, aby był dostępny do debugowania w Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 07/02/2021
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 611347acfe48e561653d644097d56d029b6a4fa6
ms.sourcegitcommit: 4cd3eb514e9fa48e586279e38fe7c2e111ebb304
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2021
ms.locfileid: "113298260"
---
# <a name="how-to-install-a-visualizer"></a>Porady: instalacja programu Visualizer
Po utworzeniu wizualizatora należy zainstalować wizualizator, aby był dostępny w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Instalowanie wizualizatora to prosty proces.

> [!NOTE]
> W aplikacjach platformy uniwersalnej systemu Windows obsługiwane są tylko standardowe wizualizatory tekstu, HTML, XML i JSON. Niestandardowe wizualizatory (utworzone przez użytkownika) nie są obsługiwane.

::: moniker range=">=vs-2019"
### <a name="to-install-a-visualizer-for-visual-studio-2019"></a>Aby zainstalować wizualizator dla programu Visual Studio 2019

1. Znajdź bibliotekę DLL zawierającą sbudowaną wizualizator.

   Zazwyczaj najlepszym rozwiązaniem jest określenie jako platformy docelowej zarówno biblioteki DLL  po stronie debugera, jak i biblioteki DLL po stronie debugera. Biblioteką DLL po stronie debugera musi być dowolny **procesor CPU** lub **32-bitowy .** Platforma docelowa dla biblioteki DLL po stronie debugera powinna odpowiadać procesowi debugowania.

   >[!NOTE]
   > Wizualizator po stronie debugera jest ładowany w Visual Studio, więc musi to być .NET Framework DLL. Strona debugera może być .NET Framework lub .NET Standard w zależności od tego, który proces jest debugowany w Visual Studio.

2. Skopiuj [bibliotekę](create-custom-visualizers-of-data.md#to-create-the-debugger-side) DLL po stronie debugera (i wszystkie biblioteki DLL, od których zależy) do jednej z następujących lokalizacji:

    - *VisualStudioInstallPath*`\Common7\Packages\Debugger\Visualizers`

    - `My Documents\`*VisualStudioVersion*`\Visualizers`

3. Skopiuj [bibliotekę DLL po stronie](create-custom-visualizers-of-data.md#to-create-the-visualizer-object-source-for-the-debuggee-side) debugera do jednej z następujących lokalizacji:

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers\` *Framework (Framework)*

    - `My Documents\`*VisualStudioVersion* `\Visualizers\` *Framework (Framework)*

    gdzie *framework* to:
    - `net2.0` w przypadku debugerów z uruchomionym środowiskiem `.NET Framework` uruchomieniowym.
    - `netstandard2.0` Dla debugerów przy użyciu środowiska uruchomieniowego, które obsługuje `netstandard 2.0` ( `.NET Framework v4.6.1+` lub `.NET Core 2.0+` ).
    - `netcoreapp` w przypadku debugerów z uruchomionym środowiskiem `.NET Core` uruchomieniowym. (obsługuje `.NET Core 2.0+` )

   Biblioteka DLL po stronie debugera jest niezbędna, jeśli chcesz utworzyć autonomiczny wizualizator. Ta biblioteka DLL zawiera kod obiektu danych, który może implementować metody <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource> .

   W przypadku wieloadresowego kodu po stronie debugera biblioteka DLL po stronie debugera musi zostać umieszczona w folderze, aby program TFM obsługiował minimalną ilość danych.

4. Uruchom ponownie sesję debugowania.

> [!NOTE]
> Procedura różni się w Visual Studio 2017 i starszych. Zobacz [poprzednią wersję](how-to-install-a-visualizer.md?view=vs-2017&preserve-view=true) tego artykułu.
::: moniker-end

::: moniker range="vs-2017"
### <a name="to-install-a-visualizer-for-visual-studio-2017-and-older"></a>Aby zainstalować wizualizator dla Visual Studio 2017 i starszych

> [!IMPORTANT]
> W programie .NET Framework 2017 i starszych obsługiwane są tylko Visual Studio wizualizatory.

1. Znajdź bibliotekę DLL zawierającą sbudowaną wizualizator.

2. Skopiuj bibliotekę DLL do jednej z następujących lokalizacji:

    - *VisualStudioInstallPath*`\Common7\Packages\Debugger\Visualizers`

    - `My Documents\`*VisualStudioVersion*`\Visualizers`

3. Uruchom ponownie sesję debugowania.

> [!NOTE]
> Jeśli chcesz użyć zarządzanego wizualizatora do zdalnego debugowania, skopiuj bibliotekę DLL do tej samej ścieżki na komputerze zdalnym.
::: moniker-end

## <a name="see-also"></a>Zobacz też
- [Tworzenie niestandardowych wizualizatorów](../debugger/create-custom-visualizers-of-data.md)
- [Porady: pisanie wizualizatora](create-custom-visualizers-of-data.md)
