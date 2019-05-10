---
title: IEnumDebugPortSuppliers2::Skip | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPortSuppliers2::Skip
helpviewer_keywords:
- IEnumDebugPortSuppliers2::Skip
ms.assetid: bd95d7e9-274f-485d-8bf6-865306ae1b81
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a9f172466e0c77580a2f68515baed1efded9e23d
ms.sourcegitcommit: 6196d0b7fdcb08ba6d28a8151ad36b8d1139f2cc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65225795"
---
# <a name="ienumdebugportsuppliers2skip"></a>IEnumDebugPortSuppliers2::Skip
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
- [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)