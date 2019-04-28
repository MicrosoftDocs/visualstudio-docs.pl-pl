---
title: IDebugApplicationThreadEvents110 Interface | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: b2cdde46484f95aa57404ebe6b6cb4c86ef458c9
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63440507"
---
# <a name="idebugapplicationthreadevents110-interface"></a>Interfejs IDebugApplicationThreadEvents110
Dodaje więcej wydarzeń wątku. Te zdarzenia są tylko lokalne. Oznacza to, możesz zasubskrybować je tylko w trwa proces debugowania, przy użyciu [IConnectionPoint](http://go.microsoft.com/fwlink/?LinkId=232738) doradztwa i unadvise metod obiektów wątku aplikacji menedżerów PDM (obiekty, które implementują [IDebugApplicationThread Interfejs](../../winscript/reference/idebugapplicationthread-interface.md)). Występują one w wątku, które pochodzą z.  
  
> [!IMPORTANT]
> Interfejs jest implementowany przez program PDM w wersji 11.0 i nowszych. Znajduje się w zestawie activdbg100.h.  
  
## <a name="methods"></a>Metody  
 `IDebugActivationThreadEvents110` Interfejsu udostępnia następujące metody.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDebugApplicationThreadEvents110::OnBeginThreadRequest](../../winscript/reference/idebugapplicationthreadevents110-onbeginthreadrequest.md)|Wywołanie do wątku, przy użyciu menedżerów PDM wątku Przełączenie zostało uruchomione.|  
|[IDebugApplicationThreadEvents110::OnResumeFromBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onresumefrombreakpoint.md)|Wątek jest wznawiana po punkcie przerwania i zostanie uaktywniona jeszcze raz.|  
|[IDebugApplicationThreadEvents110::OnSuspendForBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onsuspendforbreakpoint.md)|Wątek jest zawieszanie dla punktu przerwania i może obsłużyć wywołania, które wymagają wątku, aby w pełni zawieszone.|  
|[IDebugApplicationThreadEvents110::OnThreadRequestComplete](../../winscript/reference/idebugapplicationthreadevents110-onthreadrequestcomplete.md)|Wywołanie do wątku, przy użyciu menedżerów PDM wątku Przełączenie zostało zakończone.|