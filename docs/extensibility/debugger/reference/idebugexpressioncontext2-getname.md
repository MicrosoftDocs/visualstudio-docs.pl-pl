---
title: IDebugExpressionContext2::GetName | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionContext2::GetName
helpviewer_keywords:
- IDebugExpressionContext2::GetName
ms.assetid: c2b70d22-17af-4986-a7e3-930910367216
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 20004fd424bbb394c4c6d0a80df94d408e86285c
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56706525"
---
# <a name="idebugexpressioncontext2getname"></a>IDebugExpressionContext2::GetName
Pobiera nazwę kontekst oceny.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetName( 
   BSTR* pbstrName
);
```

```csharp
int GetName( 
   out string pbstrName
);
```

#### <a name="parameters"></a>Parametry
 `pbstrName`

 [out] Zwraca nazwę kontekst oceny.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Nazwa jest opis tego kontekstu oceny. Zwykle jest coś, co może być analizowane przez ewaluatora wyrażeń, odwołujący się do tego kontekstu dokładną ocenę. Na przykład w języku C++ nazwa jest w następujący sposób:

```
"{ function-name, source-file-name, module-file-name }"
```

## <a name="see-also"></a>Zobacz też
- [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)