---
title: IEnumDebugPortSuppliers2::Pomiń | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPortSuppliers2::Skip
helpviewer_keywords:
- IEnumDebugPortSuppliers2::Skip
ms.assetid: bd95d7e9-274f-485d-8bf6-865306ae1b81
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 06bdf3d190fb738c2685455a0d1b2b321fd9dd0b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715946"
---
# <a name="ienumdebugportsuppliers2skip"></a>IEnumDebugPortSuppliers2::Skip
Przeskakuje przez określoną liczbę elementów.

## <a name="syntax"></a>Składnia

```cpp
HRESULT Skip(
   ULONG celt
);
```

```csharp
int Skip(
   uint celt
);
```

## <a name="parameters"></a>Parametry
`celt`\
[w] Liczba elementów do pominięcia.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca . `S_FALSE` Zwraca, `celt` jeśli jest większa niż liczba pozostałych elementów; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Jeśli `celt` określa wartość większą niż liczba pozostałych elementów, wyliczenie jest `S_FALSE` ustawiona na końcu i jest zwracana.

## <a name="see-also"></a>Zobacz też
- [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)
