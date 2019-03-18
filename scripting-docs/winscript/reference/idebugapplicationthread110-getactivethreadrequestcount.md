---
title: IDebugApplicationThread110::GetActiveThreadRequestCount | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: d9bda0cc59560d90ebc0a382d858c881e7372c15
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58145073"
---
# <a name="idebugapplicationthread110getactivethreadrequestcount"></a>IDebugApplicationThread110::GetActiveThreadRequestCount
Zwraca liczbę żądań wątku z wątku menedżerów PDM przełączanie mechanizmów, które są obecnie przetwarzane. Ta liczba jest zwykle 0 lub 1. Jednak liczba może być wyższy Jeśli jedno wywołanie wątek uruchamia przetwarzanie, ale wyzwala synchroniczne wywołanie z wątku, lub w przeciwnym razie wstrzymuje działanie wątku i zezwala na przychodzące wywołania on przetworzony ponownie (na przykład, wyzwalając [ Interfejs IRemoteDebugApplicationEvents](../../winscript/reference/iremotedebugapplicationevents-interface.md) zdarzenie, które jest wystawiony w wątku debugera).  
  
> [!IMPORTANT]
>  [Interfejs IDebugApplicationThread110](../../winscript/reference/idebugapplicationthread110-interface.md) jest implementowany przez program PDM w wersji 11.0 i nowszych. Znajduje się w zestawie activdbg100.h.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetActiveThreadRequestCount([out, annotation("_Out_")] UINT * puiThreadRequests);  
```  
  
#### <a name="parameters"></a>Parametry  
 `puiThreadRequests`  
 [out] Liczba żądań wątku.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugApplicationThread110, interfejs](../../winscript/reference/idebugapplicationthread110-interface.md)