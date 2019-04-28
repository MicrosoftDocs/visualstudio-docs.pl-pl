---
title: IDebugApplication110 Interface | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplication110 Interface
ms.assetid: ae943133-eb65-4ddc-a29f-9280a82dd8d6
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0991f27077cf3ac3eb5cbfdcbb409fd5903d9a66
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446374"
---
# <a name="idebugapplication110-interface"></a>Interfejs IDebugApplication110
`IDebugApplication110` Interfejs rozszerza funkcjonalność [interfejs IDebugApplication](../../winscript/reference/idebugapplication-interface.md). Wystąpienie tego interfejsu można uzyskać za pomocą wywołania QueryInterface na implementację [interfejs IDebugApplication](../../winscript/reference/idebugapplication-interface.md).  
  
> [!IMPORTANT]
> Interfejs jest implementowany przez program PDM w wersji 11.0 i nowszych. Znajduje się w zestawie activdbg100.h.  
  
## <a name="methods"></a>Metody  
 `IDebugApplication110` Interfejsu udostępnia następujące metody.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDebugApplication110::SynchronousCallInMainThread](../../winscript/reference/idebugapplication110-synchronouscallinmainthread.md)|Tworzy wywołanie synchroniczne w wątku głównym.|  
|[IDebugApplication110::AsynchronousCallInMainThread](../../winscript/reference/idebugapplication110-asynchronouscallinmainthread.md)|Sprawia, że wywołanie asynchroniczne w wątku głównym.|  
|[IDebugApplication110::CallableWaitForHandles](../../winscript/reference/idebugapplication110-callablewaitforhandles.md)|W tym czasie czeka dla każdego określonego dojścia ma być zasygnalizowany pozwalając wywołania międzywątkowe wysyłany do tego wątku. Ta metoda musi zostać wywołana z wątku debugera.|