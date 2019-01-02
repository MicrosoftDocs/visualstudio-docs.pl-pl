---
title: IDebugEngine3::LoadSymbols | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugEngine3::LoadSymbols
helpviewer_keywords:
- IDebugEngine3::LoadSymbols
ms.assetid: c846a440-1d91-4d48-b8f1-82e902ae152b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b74b4303d85364e5d6afa2eb0618c32770ac3a23
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53865157"
---
# <a name="idebugengine3loadsymbols"></a>IDebugEngine3::LoadSymbols
Symbole obciążenia (w razie potrzeby) dla wszystkich modułów, które jest debugowane tego aparatu debugowania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT LoadSymbols();  
```  
  
```csharp  
int LoadSymbols();  
```  
  
#### <a name="parameters"></a>Parametry  
 Brak.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Spowoduje to załadowanie symboli debugowania dla wszystkich modułów, które odwołuje się ten aparat debugowania. Symbole są ładowane tylko wtedy, gdy ich nie zostały jeszcze załadowane. Symbole są przeszukiwane w ścieżkach, ustaw przez wywołanie [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md).  
  
## <a name="see-also"></a>Zobacz też  
 [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)   
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)