---
title: IEnumCodePaths2::Reset | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCodePaths2::Reset
helpviewer_keywords:
- IEnumCodePaths2::Reset
ms.assetid: 490c0e19-ff4b-4673-bd06-cdee996ac226
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2392c25513b53137e5cdca332bc133ab998be999
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717792"
---
# <a name="ienumcodepaths2reset"></a>IEnumCodePaths2::Reset
Resetuje wyliczenie do pierwszego elementu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT Reset(
   void
);
```

```csharp
int Reset();
```

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Po wywołaniu tej metody, następne wywołanie [Next](../../../extensibility/debugger/reference/ienumcodepaths2-next.md) metoda zwraca pierwszy element wyliczenia.

## <a name="see-also"></a>Zobacz też
- [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)
