---
title: 'IDebugFunctionObject:: oszacowanie | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::Evaluate
helpviewer_keywords:
- IDebugFunctionObject::Evaluate method
ms.assetid: 29349ea3-d5c1-4135-aa76-ced073ab9683
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 94285bc0ca36d4a55c3cd3a3483f6e20f6914271
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99920987"
---
# <a name="idebugfunctionobjectevaluate"></a>IDebugFunctionObject::Evaluate
Wywołuje funkcję i zwraca wynikową wartość jako obiekt.

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
podczas Tablica obiektów [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) reprezentujących parametry wejściowe. Każdy z tych parametrów został utworzony za pomocą jednej z `Create` metod w interfejsie [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) .

`dwParams`\
podczas Liczba parametrów w `ppParams` tablicy.

`dwTimeout`\
podczas Określa maksymalny czas oczekiwania (w milisekundach) przed powrotem z tej metody. Użyj `INFINITE` , aby czekać w nieskończoność.

`ppResult`\
określoną Zwraca [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) reprezentujący wartość funkcji jako obiekt.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda konfiguruje i wykonuje wywołanie funkcji reprezentowanej przez obiekt [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) .

## <a name="see-also"></a>Zobacz też
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
