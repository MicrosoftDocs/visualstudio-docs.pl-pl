---
title: 'Instrukcje: Instalacja programu Visualizer | Dokumentacja firmy Microsoft'
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e62637581fbb65eb8efd20e048cc364895cfbcdc
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53914574"
---
# <a name="how-to-install-a-visualizer"></a>Instrukcje: Instalacja programu Visualizer
Po utworzeniu wizualizatora, należy zainstalować wizualizatora tak, że będzie on dostępny w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Instalowanie wizualizatora jest prostym procesem.  
  
> [!NOTE]
>  W aplikacjach platformy UWP, tylko standardowy tekst, HTML, XML i JSON wizualizatory są obsługiwane. Wizualizatory niestandardowe (utworzone przez użytkownika) nie są obsługiwane.  
  
### <a name="to-install-a-visualizer"></a>Aby instalacja programu visualizer  
  
1.  Znajdź bibliotekę DLL, która zawiera visualizer, który został wcześniej utworzony.  
  
2.  Kopiuj bibliotekę DLL do jednej z następujących lokalizacji:  
  
    -   *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers`  
  
    -   `My Documents\` *VisualStudioVersion* `\Visualizers`  
  
3.  Jeśli chcesz użyć zarządzany Wizualizator dla zdalnego debugowania, należy skopiować bibliotekę DLL do tej samej ścieżki na komputerze zdalnym.  
  
4.  Uruchom ponownie sesję debugowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie niestandardowych Wizualizatorów](../debugger/create-custom-visualizers-of-data.md)   
 [Instrukcje: Pisanie wizualizatora](/visualstudio/debugger/create-custom-visualizers-of-data)