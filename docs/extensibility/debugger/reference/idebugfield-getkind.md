---
title: IDebugField::GetKind | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetKind
helpviewer_keywords:
- IDebugField::GetKind method
ms.assetid: e7c9c60a-8e55-4ecc-aa63-0c814a1e92cc
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d99c7d1bed9f5afe844539c9a9ccab11f43a8002
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66333172"
---
# <a name="idebugfieldgetkind"></a>IDebugField::GetKind
Ta metoda pobiera typ pola.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetKind( 
   FIELD_KIND* pdwKind
);
```

```csharp
int GetKind(
   out enum_FIELD_KIND pdwKind
);
```

## <a name="parameters"></a>Parametry
`pdwKind`\
[out] Zwraca typ pola pod postacią połączenia [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) stałe.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz także
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md)