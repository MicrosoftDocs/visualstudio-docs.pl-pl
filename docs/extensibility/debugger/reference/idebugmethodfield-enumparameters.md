---
title: IDebugMethodField::EnumParameters | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugMethodField::EnumParameters
helpviewer_keywords:
- IDebugMethodField::EnumParameters method
ms.assetid: d77b1197-deb6-4144-8d1b-8b09949ccfac
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 674f2cc7160ace49f4fc8b5333fc3b951a7ccc8b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53823182"
---
# <a name="idebugmethodfieldenumparameters"></a>IDebugMethodField::EnumParameters
Tworzy moduł wyliczający dla parametrów metody.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT EnumParameters(   
   IEnumDebugFields** ppParams  
);  
```  
  
```csharp  
int EnumParameters(  
   out IEnumDebugFields ppParams  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppParams`  
 [out] Zwraca [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) obiekt reprezentujący listę parametrów do metody; w przeciwnym razie zwraca wartość null, jeśli nie ma żadnych parametrów.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca wartość S_OK lub zwraca wartość S_FALSE, jeśli nie ma żadnych parametrów. W przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Każdy element jest [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) obiekt reprezentujący różne typy parametrów. Wywołaj [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) metody dla każdego obiektu, aby określić dokładnie rodzaj parametru obiekt reprezentuje.  
  
 Parametr obejmuje zarówno nazwy zmiennych, jak i jej typu. Pierwszy parametr metody klasy zwykle jest wskaźnik "this".  
  
 Jeśli tylko typy parametrów jest potrzebny, wywołaj [EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) metody.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)