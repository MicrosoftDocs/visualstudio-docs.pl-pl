---
title: Hosty skryptów systemu Windows | Microsoft Docs
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
ms.openlocfilehash: 8468f578ee44487acd2575e81e01d65969110437
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72568812"
---
# <a name="windows-script-hosts"></a>Hosty skryptów systemu Windows
Podczas implementowania hosta skryptów systemu Microsoft Windows można bezpiecznie założyć, że aparat skryptów wywołuje interfejs [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) tylko w kontekście wątku podstawowego, o ile Host wykonuje następujące czynności:  
  
- Wybiera wątek podstawowy (na ogół wątek, który zawiera pętlę wiadomości).  
  
- Tworzy wystąpienie aparatu wykonywania skryptów w wątku podstawowym.  
  
- Wywołuje metody aparatu skryptów tylko z wątku podstawowego, chyba że jest to dozwolone, tak jak w przypadku [IActiveScript:: InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md) i [IActiveScript:: klon](../winscript/reference/iactivescript-clone.md).  
  
- Wywołuje obiekt wysyłania aparatu skryptów tylko z wątku podstawowego.  
  
- Zapewnia, że pętla komunikatów działa w wątku bazowym, jeśli zostanie podane dojście do okna.  
  
- Zapewnia, że obiekty w modelu obiektu hosta tylko zdarzenia źródłowe w wątku podstawowym.  
  
  Te reguły są automatycznie poprzedzane przez wszystkie hosty z jednym wątkiem. Model z ograniczeniami opisany powyżej jest celowo zbyt duży, aby umożliwić hostowi przerwanie zablokowanego skryptu przez wywołanie [IActiveScript:: InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md) z innego wątku (zainicjowanego przez program obsługi klawiszy Ctrl + Break lub podobne) lub do duplikowania skryptu w nowy wątek korzystający z [IActiveScript:: Clone](../winscript/reference/iactivescript-clone.md).  
  
## <a name="remarks"></a>Uwagi  
 Żadne z tych ograniczeń nie mają zastosowania do hosta, który wybiera zaimplementowanie bezpłatnego interfejsu [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) i modelu obiektów dowolnego wątku. Taki host może korzystać z interfejsu [IActiveScript](../winscript/reference/iactivescript.md) z dowolnego wątku bez ograniczeń.  
  
## <a name="see-also"></a>Zobacz także  
 [Interfejsy skryptów systemu Windows](../winscript/windows-script-interfaces.md)