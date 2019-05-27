---
title: IDebugFunctionPosition2::GetFunctionName | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionPosition2::GetFunctionName
helpviewer_keywords:
- IDebugFunctionPosition2::GetFunctionName
ms.assetid: eb7a348e-a7f5-4f25-be68-80482d5482a8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7b93860bd59c37e2fab383a4e74b13c8ff17841e
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66200668"
---
# <a name="idebugfunctionposition2getfunctionname"></a>IDebugFunctionPosition2::GetFunctionName
Pobiera nazwę funkcji, na który wskazuje tej pozycji.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetFunctionName( 
   BSTR* pbstrFunctionName
);
```

```csharp
int GetFunctionName(
   out string pbstrFunctionName
);
```

## <a name="parameters"></a>Parametry
`pbstrFunctionName`\
[out] Zwraca nazwę funkcji.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz także
- [IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)