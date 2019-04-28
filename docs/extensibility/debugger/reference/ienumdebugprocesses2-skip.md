---
title: IEnumDebugProcesses2::Skip | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugProcesses2::Skip
helpviewer_keywords:
- IEnumDebugProcesses2::Skip
ms.assetid: b9e9d888-189b-44c4-a65f-e91612458898
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: eebbdd7d8b9bf4726da298d98e821875e71c3acf
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62866094"
---
# <a name="ienumdebugprocesses2skip"></a>IEnumDebugProcesses2::Skip
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
- [IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)