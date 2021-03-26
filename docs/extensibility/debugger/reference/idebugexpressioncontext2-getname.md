---
description: Pobiera nazwę kontekstu oceny.
title: 'IDebugExpressionContext2:: GetName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionContext2::GetName
helpviewer_keywords:
- IDebugExpressionContext2::GetName
ms.assetid: c2b70d22-17af-4986-a7e3-930910367216
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c3aa27ba70e0b407e72a42d2904467ee85fc027b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105092322"
---
# <a name="idebugexpressioncontext2getname"></a>IDebugExpressionContext2::GetName
Pobiera nazwę kontekstu oceny.

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

## <a name="parameters"></a>Parametry
`pbstrName`\
określoną Zwraca nazwę kontekstu oceny.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Nazwa to opis tego kontekstu szacowania. Zwykle jest to element, który może być analizowany przez ewaluatora wyrażeń, który odwołuje się do tego dokładnego kontekstu oceny. Na przykład w języku C++ nazwa jest następująca:

```
"{ function-name, source-file-name, module-file-name }"
```

## <a name="see-also"></a>Zobacz też
- [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)
