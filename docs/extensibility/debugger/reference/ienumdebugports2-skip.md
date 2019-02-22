---
title: IEnumDebugPorts2::Skip | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPorts2::Skip
helpviewer_keywords:
- IEnumDebugPorts2::Skip
ms.assetid: a837383f-7b39-4e06-b336-f1715b073dbe
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 56d941a826287f119fefdd11d305359dba02078d
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56681780"
---
# <a name="ienumdebugports2skip"></a>IEnumDebugPorts2::Skip
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

#### <a name="parameters"></a>Parametry
 `celt`

 [in] Liczba elementów do pominięcia.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`. Zwraca `S_FALSE` Jeśli `celt` jest większa niż liczba pozostałych elementów; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Jeśli `celt` określa wartość większa niż liczba pozostałych elementów wyliczenia jest ustawiona na końcu i `S_FALSE` jest zwracana.

## <a name="see-also"></a>Zobacz też
- [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)