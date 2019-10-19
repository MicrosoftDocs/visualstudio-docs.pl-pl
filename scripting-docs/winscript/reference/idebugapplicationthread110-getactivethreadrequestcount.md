---
title: 'IDebugApplicationThread110:: GetActiveThreadRequestCount | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThread110::GetActiveThreadRequestCount
ms.assetid: 025d2072-1d7f-4448-8aa3-38a014313570
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e7f038c1d0958701a14899825a2adb0a11cf604d
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574479"
---
# <a name="idebugapplicationthread110getactivethreadrequestcount"></a>IDebugApplicationThread110::GetActiveThreadRequestCount
Zwraca liczbę żądań wątku z mechanizmów przełączania wątku PDM, które są obecnie przetwarzane. Ta liczba jest zwykle równa 0 lub 1. Jednakże liczba może być wyższa, jeśli jedno wywołanie wątku rozpocznie przetwarzanie, ale wyzwala wywołanie synchroniczne z wątku lub w inny sposób wstrzymuje wątek i zezwala na ponowne przetwarzanie wywołań przychodzących (na przykład przez wyzwolenie elementu [IRemoteDebugApplicationEvents Zdarzenie interfejsu](../../winscript/reference/iremotedebugapplicationevents-interface.md) , które jest wydawane w wątku debugera).  
  
> [!IMPORTANT]
> [Interfejs IDebugApplicationThread110](../../winscript/reference/idebugapplicationthread110-interface.md) jest implementowany przez PDM v 11.0 i nowsze. Znajduje się w zestawie activdbg100.h.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetActiveThreadRequestCount([out, annotation("_Out_")] UINT * puiThreadRequests);  
```  
  
#### <a name="parameters"></a>Parametry  
 `puiThreadRequests`  
 określoną Liczba żądań wątków.  
  
## <a name="see-also"></a>Zobacz także  
 [IDebugApplicationThread110, interfejs](../../winscript/reference/idebugapplicationthread110-interface.md)