---
title: Interfejs IDebugApplicationThreadEvents110 | Microsoft Docs
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
ms.openlocfilehash: 5dd666d825c40155675714f5945209f22198993c
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2019
ms.locfileid: "72984394"
---
# <a name="idebugapplicationthreadevents110-interface"></a>Interfejs IDebugApplicationThreadEvents110
Dodaje więcej zdarzeń wątku. Te zdarzenia są tylko lokalne. Oznacza to, że można subskrybować je tylko w debugowanym procesie przy użyciu metod [IConnectionPoint](/windows/win32/api/ocidl/nn-ocidl-iconnectionpoint) Advise i Unadvise dla obiektów wątku aplikacji PDM (obiektów, które implementują [interfejs IDebugApplicationThread](../../winscript/reference/idebugapplicationthread-interface.md)). Są one wykonywane w wątku, z którego pochodzą.  
  
> [!IMPORTANT]
> Interfejs jest implementowany przez program PDM w wersji 11.0 i nowszych. Znajduje się w zestawie activdbg100.h.  
  
## <a name="methods"></a>Metody  
 Interfejs `IDebugActivationThreadEvents110` udostępnia następujące metody.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDebugApplicationThreadEvents110::OnBeginThreadRequest](../../winscript/reference/idebugapplicationthreadevents110-onbeginthreadrequest.md)|Rozpoczęto wywołanie wątku przy użyciu funkcji przełączania wątku PDM.|  
|[IDebugApplicationThreadEvents110::OnResumeFromBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onresumefrombreakpoint.md)|Wątek jest wznawiany z punktu przerwania i zostanie on uaktywniony ponownie.|  
|[IDebugApplicationThreadEvents110::OnSuspendForBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onsuspendforbreakpoint.md)|Wątek jest wstrzymywany dla punktu przerwania i może obsługiwać wywołania, które wymagają całkowitego zawieszenia wątku.|  
|[IDebugApplicationThreadEvents110::OnThreadRequestComplete](../../winscript/reference/idebugapplicationthreadevents110-onthreadrequestcomplete.md)|Wywołanie wątku przy użyciu przełączenia wątku PDM zostało zakończone.|