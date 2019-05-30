---
title: IEnumDebugReferenceInfo2::Skip | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugReferenceInfo2::Skip
helpviewer_keywords:
- IEnumDebugReferenceInfo2::Skip
ms.assetid: 12f07ed8-92bd-47b5-9113-f73fec5bdde6
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fa8f4e7c9ff04ff20ca58a14465399c62a71bbb1
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66350864"
---
# <a name="ienumdebugreferenceinfo2skip"></a>IEnumDebugReferenceInfo2::Skip
Pomija w ciągu określonej liczby elementów.

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
[in] Liczba elementów do pominięcia.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`. Zwraca `S_FALSE` Jeśli `celt` jest większa niż liczba pozostałych elementów; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Jeśli `celt` określa wartość większa niż liczba pozostałych elementów wyliczenia jest ustawiona na końcu i `S_FALSE` jest zwracana.

## <a name="see-also"></a>Zobacz także
- [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)