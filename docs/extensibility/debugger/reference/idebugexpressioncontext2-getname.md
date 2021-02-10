---
title: 'IDebugExpressionContext2:: GetName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionContext2::GetName
helpviewer_keywords:
- IDebugExpressionContext2::GetName
ms.assetid: c2b70d22-17af-4986-a7e3-930910367216
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8529e83de0f5de3d5d202885cf37b29d21fa3e59
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949535"
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
