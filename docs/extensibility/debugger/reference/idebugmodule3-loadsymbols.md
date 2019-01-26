---
title: IDebugModule3::LoadSymbols | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugModule3::LoadSymbols
helpviewer_keywords:
- IDebugModule3::LoadSymbols
ms.assetid: 7548c8c1-cbc6-48aa-a845-19058d4a85bb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a14406d0aeb58cead006ef9f1d5485a053d4a72c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55021065"
---
# <a name="idebugmodule3loadsymbols"></a>IDebugModule3::LoadSymbols
Ładuje symbole dla bieżącego modułu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT LoadSymbols(  
   void  
);  
```  
  
```csharp  
int LoadSymbols();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli metoda się powiedzie, zwraca `S_OK`. Jeśli nie powiedzie się, zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda ładuje symbole z bieżącą ścieżkę wyszukiwania (może być zmienione przez wywołanie metody [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md) metody).  
  
 Ta metoda jest preferowana nad [ReloadSymbols_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md) metody.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)   
 [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)