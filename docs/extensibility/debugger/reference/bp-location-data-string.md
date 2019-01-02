---
title: BP_LOCATION_DATA_STRING | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- BP_LOCATION_DATA_STRING
helpviewer_keywords:
- BP_LOCATION_DATA_STRING structure
ms.assetid: 445d6f3f-95b0-47ac-85e2-51b778240687
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6a9f822dfe13d6adf4ea79481ca5bca2cacf2463
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53946944"
---
# <a name="bplocationdatastring"></a>BP_LOCATION_DATA_STRING
Używana do ustawiania punktów przerwania danych, które są oparte na ciąg, który użytkownik może wprowadzić ze zintegrowanego środowiska programistycznego (IDE).  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef struct _BP_LOCATION_DATA_STRING {   
   IDebugThread2* pThread;  
   BSTR           bstrContext;  
   BSTR           bstrDataExpr;  
   DWORD          dwNumElements;  
} BP_LOCATION_DATA_STRING;  
```  
  
## <a name="members"></a>Elementy członkowskie  
 `pThread`  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) obiekt, który reprezentuje wątek, w którym występuje punkt przerwania.  
  
 `bstrContext`  
 Kontekst punktu przerwania w kodzie, zazwyczaj nazwę metody lub funkcji wyświetlanego w stosie wywołań.  
  
 `bstrDataExpr`  
 Ciąg danych, które użytkownik wprowadza ustawić punkt przerwania.  
  
 `dwNumElements`  
 Liczba elementów w ciągu danych, w której występuje punkt przerwania.  
  
## <a name="remarks"></a>Uwagi  
 Ta struktura jest elementem członkowskim [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) struktur w ramach złożenia.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Struktur i Unii](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)