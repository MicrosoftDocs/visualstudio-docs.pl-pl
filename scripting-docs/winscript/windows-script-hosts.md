---
title: Windows Script hosty | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Windows Script Host, implementing hosts
ms.assetid: 9d5f6471-b318-40f3-be01-d9cd0b1cdd47
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eec1824bd3ba1a8acb7e3c540656151cd4b11d1f
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58145112"
---
# <a name="windows-script-hosts"></a>Hosty skryptów systemu Windows
Podczas implementowania systemu Microsoft Windows Script host, można bezpiecznie przyjąć silnik wykonywania skryptów tylko wywołuje [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) interfejsu w kontekście wątku podstawowy, tak długo, jak host wykonuje następujące czynności:  
  
- Wybiera podstawowego wątku (zazwyczaj wątkiem, który zawiera pętli komunikatów).  
  
- Tworzy silnik wykonywania skryptów w podstawowej wątku.  
  
- Wywołania skryptów metod silnika tylko z wątku w podstawowej, z wyjątkiem sytuacji, w przypadku, gdy zezwolenie, tak jak w przypadku [IActiveScript::InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md) i [IActiveScript::Clone](../winscript/reference/iactivescript-clone.md).  
  
- Wywołuje obiekt wysyłania silnik wykonywania skryptów, tylko z podstawowego wątku.  
  
- Zapewnia, że pętli komunikatów działa w podstawowy wątek, jeśli podano uchwyt okna.  
  
- Zapewnia, że obiektów w obiekcie hosta modelu tylko źródło zdarzenia w podstawowej wątku.  
  
  Te reguły są automatycznie po wszystkich hostów apartamentem. Model ograniczonych opisanych powyżej jest celowo nie będzie wystarczająco umożliwia hosta przerwać skryptu zablokowane przez wywołanie metody [IActiveScript::InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md) z innego wątku (inicjowane przez program obsługi CTRL + BREAK lub podobne) lub do Duplikuj skryptu za pomocą nowego wątku [IActiveScript::Clone](../winscript/reference/iactivescript-clone.md).  
  
## <a name="remarks"></a>Uwagi  
 Żadna z tych ograniczeń zastosowanie do hosta, który zdecyduje się na implementacji, bezwątkowy [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) interfejsu i bezwątkowy obiektu modelu. Można użyć takiego hosta [IActiveScript](../winscript/reference/iactivescript.md) interfejs z żadnym z wątków, bez ograniczeń.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy skryptów systemu Windows](../winscript/windows-script-interfaces.md)