---
title: 'Instrukcje: Instalowanie wizualizatora | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, visualizers
- visualizers, installing
ms.assetid: 3310ef43-515c-4d97-b0f9-51047247d3da
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5726cea8b2e81c53b5f3fff963357946f26b199f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64796962"
---
# <a name="how-to-install-a-visualizer"></a>Porady: instalacja programu Visualizer
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Po utworzeniu wizualizatora należy zainstalować wizualizator, aby był dostępny w programie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Instalowanie wizualizatora jest prostym procesem.  
  
> [!NOTE]
> W aplikacjach ze **sklepu** obsługiwane są tylko Wizualizatory tekstu standardowego, HTML, XML i JSON. Wizualizacje niestandardowe (utworzone przez użytkownika) nie są obsługiwane.  
  
### <a name="to-install-a-visualizer"></a>Aby zainstalować wizualizator  
  
1. Znajdź bibliotekę DLL, która zawiera skompilowany wizualizator.  
  
2. Skopiuj bibliotekę DLL do jednej z następujących lokalizacji:  
  
    - *VisualStudioInstallPath*`\Common7\Packages\Debugger\Visualizers`  
  
    - `My Documents\`*VisualStudioVersion*`\Visualizers`  
  
3. Jeśli chcesz użyć zarządzanego wizualizatora na potrzeby debugowania zdalnego, Skopiuj bibliotekę DLL do tej samej ścieżki na komputerze zdalnym.  
  
4. Uruchom ponownie sesję debugowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie wizualizacji niestandardowych](../debugger/create-custom-visualizers-of-data.md)   
 [Porady: pisanie wizualizatora](../debugger/how-to-write-a-visualizer.md)
