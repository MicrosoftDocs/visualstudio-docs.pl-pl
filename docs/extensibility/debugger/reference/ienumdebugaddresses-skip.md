---
description: Ta metoda pomija określoną liczbę elementów w wyliczeniu adresów.
title: 'IEnumDebugAddresses:: Skip | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugAddresses::Skip
helpviewer_keywords:
- IEnumDebugAddresses::Skip method
ms.assetid: ed9a8e71-30ef-414b-9da5-c9a2a251b84e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 082cba541b1074e75e44384cd8ac9e4879cc29c3
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105083157"
---
# <a name="ienumdebugaddressesskip"></a>IEnumDebugAddresses::Skip
Ta metoda pomija określoną liczbę elementów.

## <a name="syntax"></a>Składnia

```cpp
HRESULT Skip(
   [in] ULONG celt
);
```

```csharp
int Skip(
   uint celt
);
```

## <a name="parameters"></a>Parametry
`celt`\
podczas Liczba elementów do pominięcia.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` . Zwraca `S_FALSE` wartość `celt` , jeśli jest większa niż liczba pozostałych elementów; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Jeśli `celt` wartość jest większa niż liczba pozostałych elementów, Wyliczenie zostanie ustawione na koniec i `S_FALSE` zostanie zwrócone.

## <a name="see-also"></a>Zobacz też
- [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)
