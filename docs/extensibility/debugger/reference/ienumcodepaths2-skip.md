---
title: IEnumCodePaths2::Pomiń | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCodePaths2::Skip
helpviewer_keywords:
- IEnumCodePaths2::Skip
ms.assetid: 356472d8-68b2-4b7e-b5f0-1f16d4ee80af
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c552e57c43b5abc1a41ecd468747b4ce32241a6f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717745"
---
# <a name="ienumcodepaths2skip"></a>IEnumCodePaths2::Skip
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
- [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)
