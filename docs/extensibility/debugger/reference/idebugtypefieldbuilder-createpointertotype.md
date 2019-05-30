---
title: IDebugTypeFieldBuilder::CreatePointerToType | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- CreatePointerToType
- IDebugTypeFieldBuilder::CreatePointerToType
ms.assetid: 73966e8a-b643-43e0-9b4e-0aa4b402ebbe
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b8947090c56376b03da83cfd81296604b6bd642a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66319904"
---
# <a name="idebugtypefieldbuildercreatepointertotype"></a>IDebugTypeFieldBuilder::CreatePointerToType
Tworzy wskaźnik do określonego typu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT CreatePointerToType(
   IDebugField*  pTypeField,
   IDebugField** pPtrToTypeField
);
```

```csharp
int CreatePointerToType(
   IDebugField     pTypeField,
   out IDebugField pPtrToTypeField
);
```

## <a name="parameters"></a>Parametry
`pTypeField`\
[in] Wpisz, aby wskazać. Jest reprezentowany przez [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interfejsu.

`pPtrToTypeField`\
[out] Zwraca wskaźnik, reprezentowane przez nowy **IDebugField** obiektu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz także
- [IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md)