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
ms.openlocfilehash: 494287c6691d27eb636f92eff324eecf49daf5fa
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73187578"
---
# <a name="how-to-install-a-visualizer"></a>Porady: instalacja programu Visualizer
Po utworzeniu wizualizatora należy zainstalować wizualizator, aby był dostępny w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Instalowanie wizualizatora jest prostym procesem.

> [!NOTE]
> W aplikacjach platformy UWP obsługiwane są tylko wizualizacje tekstu standardowego, HTML, XML i JSON. Wizualizacje niestandardowe (utworzone przez użytkownika) nie są obsługiwane.

### <a name="to-install-a-visualizer"></a>Aby zainstalować wizualizator

1. Znajdź bibliotekę DLL, która zawiera skompilowany wizualizator.

2. Skopiuj bibliotekę DLL do jednej z następujących lokalizacji:

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers`

    - `My Documents\` *VisualStudioVersion* `\Visualizers`

3. Jeśli chcesz użyć zarządzanego wizualizatora na potrzeby debugowania zdalnego, Skopiuj bibliotekę DLL do tej samej ścieżki na komputerze zdalnym.

4. Uruchom ponownie sesję debugowania.

## <a name="see-also"></a>Zobacz także
- [Tworzenie niestandardowych wizualizatorów](../debugger/create-custom-visualizers-of-data.md)
- [Instrukcje: pisanie wizualizatora](create-custom-visualizers-of-data.md)