---
title: IDebugExtendedField::GetExtendedKind | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExtendedField::GetExtendedKind
- GetExtendedKind
ms.assetid: 20dc1c13-3cc0-4bb4-9c99-fa85587c86c3
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9b95992bdb9a35edbb828f05f4d4aad5e7d8631e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352700"
---
# <a name="idebugextendedfieldgetextendedkind"></a>IDebugExtendedField::GetExtendedKind
Pobiera rodzaj określone pole rozszerzonego.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetExtendedKind(
   FIELD_KIND_EX* pdwKind
);
```

```csharp
int GetExtendedKind(
   ref enum_FIELD_KIND_EX pdwKind
);
```

## <a name="parameters"></a>Parametry
`pdwKind`\
[out w] Wartość z [FIELD_KIND_EX](../../../extensibility/debugger/reference/field-kind-ex.md) wyliczenie, który definiuje typ pola.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz także
- [IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)