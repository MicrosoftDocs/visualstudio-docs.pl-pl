---
title: IDebugExtendedField::IsClosedType | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IsClosedType
- IDebugExtendedField::IsClosedType
ms.assetid: 9136fc57-74ff-4fe4-a6e2-b137cb9d5b08
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0ea8e501d338de24a49b04a61b46652c062a027a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352688"
---
# <a name="idebugextendedfieldisclosedtype"></a>IDebugExtendedField::IsClosedType
Określa, czy pole reprezentuje zamkniętego typu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT IsClosedType(
   void
);
```

```csharp
int IsClosedType();
```

## <a name="return-value"></a>Wartość zwracana
 Jeśli to pole jest zamkniętego typu, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE`.

## <a name="see-also"></a>Zobacz także
- [IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)