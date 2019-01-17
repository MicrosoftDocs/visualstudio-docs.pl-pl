---
title: IDebugApplicationThreadEvents110 Interface | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThreadEvents110 Interface
ms.assetid: 91a98b0e-7c81-4118-af75-82f75fd4f25a
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: db20440d4dc797ce9a0f21c3ac0c6c89c5d4e036
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348246"
---
# <a name="idebugapplicationthreadevents110-interface"></a>Interfejs IDebugApplicationThreadEvents110
Dodaje więcej wydarzeń wątku. Te zdarzenia są tylko lokalne. Oznacza to, możesz zasubskrybować je tylko w trwa proces debugowania, przy użyciu [IConnectionPoint](http://go.microsoft.com/fwlink/?LinkId=232738) doradztwa i unadvise metod obiektów wątku aplikacji menedżerów PDM (obiekty, które implementują [IDebugApplicationThread Interfejs](../../winscript/reference/idebugapplicationthread-interface.md)). Występują one w wątku, które pochodzą z.  
  
> [!IMPORTANT]
>  Interfejs jest implementowany przez program PDM w wersji 11.0 i nowszych. Znajduje się w zestawie activdbg100.h.  
  
## <a name="methods"></a>Metody  
 `IDebugActivationThreadEvents110` Interfejsu udostępnia następujące metody.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDebugApplicationThreadEvents110::OnBeginThreadRequest](../../winscript/reference/idebugapplicationthreadevents110-onbeginthreadrequest.md)|Wywołanie do wątku, przy użyciu menedżerów PDM wątku Przełączenie zostało uruchomione.|  
|[IDebugApplicationThreadEvents110::OnResumeFromBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onresumefrombreakpoint.md)|Wątek jest wznawiana po punkcie przerwania i zostanie uaktywniona jeszcze raz.|  
|[IDebugApplicationThreadEvents110::OnSuspendForBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onsuspendforbreakpoint.md)|Wątek jest zawieszanie dla punktu przerwania i może obsłużyć wywołania, które wymagają wątku, aby w pełni zawieszone.|  
|[IDebugApplicationThreadEvents110::OnThreadRequestComplete](../../winscript/reference/idebugapplicationthreadevents110-onthreadrequestcomplete.md)|Wywołanie do wątku, przy użyciu menedżerów PDM wątku Przełączenie zostało zakończone.|