---
title: IDebugFunctionObject::Evaluate | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::Evaluate
helpviewer_keywords:
- IDebugFunctionObject::Evaluate method
ms.assetid: 29349ea3-d5c1-4135-aa76-ced073ab9683
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d56d80a10967f2ed0da82ad79905914874e73df1
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66200763"
---
# <a name="idebugfunctionobjectevaluate"></a>IDebugFunctionObject::Evaluate
Wywołuje funkcję i zwraca wartość wynikowa jako obiekt.

## <a name="syntax"></a>Składnia

```cpp
HRESULT Evaluate( 
   IDebugObject** ppParams,
   DWORD          dwParams,
   DWORD          dwTimeout,
   IDebugObject** ppResult
);
```

```csharp
int Evaluate(
   IDebugObject[]   ppParams,
   IntPtr           dwParams,
   uint             dwTimeout,
   out IDebugObject ppResult
);
```

## <a name="parameters"></a>Parametry
`ppParams`\
[in] Tablica [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) obiekty reprezentujące parametrów wejściowych. Każdy z tych parametrów został utworzony przy użyciu jednego z `Create` metody [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) interfejsu.

`dwParams`\
[in] Liczba parametrów w `ppParams` tablicy.

`dwTimeout`\
[in] Określa maksymalny czas (w milisekundach) oczekiwania przed zwróceniem z tej metody. Użyj `INFINITE` czekanie w nieskończoność.

`ppResult`\
[out] Zwraca [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) reprezentujący wartość funkcji jako obiekt.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda konfiguruje i wykonuje wywołanie funkcji, reprezentowane przez [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) obiektu.

## <a name="see-also"></a>Zobacz także
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)