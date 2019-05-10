---
title: IDebugReturnValueEvent2::GetReturnValue | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReturnValueEvent2::GetReturnValue
helpviewer_keywords:
- IDebugReturnValueEvent2::GetReturnValue
ms.assetid: 86c50d5a-6df6-4798-818a-c587a8741f90
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: db7199a4e589d4839e2a9171350063d2bb4f9f68
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/09/2019
ms.locfileid: "65457449"
---
# <a name="idebugreturnvalueevent2getreturnvalue"></a>IDebugReturnValueEvent2::GetReturnValue
Pobiera wartość zwracana na przechodzenie krok po kroku z lub funkcji.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetReturnValue ( 
   IDebugProperty2** ppReturnValue
);
```

```csharp
int GetReturnValue ( 
   out IDebugProperty2 ppReturnValue
);
```

## <a name="parameters"></a>Parametry
 `ppReturnValue`\

 [out] Zwraca [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) obiekt, który reprezentuje wartość, które mają zostać pobrane.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz także
- [IDebugReturnValueEvent2](../../../extensibility/debugger/reference/idebugreturnvalueevent2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)