---
title: IDebugMemoryBytes2::WriteAt | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryBytes2::WriteAt
helpviewer_keywords:
- IDebugMemoryBytes2::WriteAt method
- WriteAt method
ms.assetid: 61cc3704-47fa-4d9b-aa62-bb4585ac8fb1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5eefaee08d64952681e91711cdf8347186123e57
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66347137"
---
# <a name="idebugmemorybytes2writeat"></a>IDebugMemoryBytes2::WriteAt
Zapisuje określoną liczbę bajtów pamięci, zaczynając od określonego adresu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT WriteAt( 
   IDebugMemoryContext2* pStartContext,
   DWORD                 dwCount,
   BYTE*                 rgbMemory
);
```

```csharp
int WriteAt(
   IDebugMemoryContext2 pStartContext,
   uint                 dwCount,
   byte[]               rgbMemory
);
```

## <a name="parameters"></a>Parametry
`pStartContext`\
[in] [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) obiekt, który określa, gdzie rozpoczyna zapis bajtów.

`dwCount`\
[in] Liczba bajtów do zapisania.

`rgbMemory`\
[in] Bajty do zapisania. Ta tablica zakłada, że co najmniej `dwCount` bajtów.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` Jeśli nie wszystkie wartości bajtowe mogłyby być zapisywane lub zwraca kod błędu (zwykle `E_FAIL`).

## <a name="remarks"></a>Uwagi
 Jeśli adres początkowy nie jest w obrębie okna pamięci, reprezentowane przez ten [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) obiektu występuje nie zapisywania i kod błędu `E_FAIL` zwróceniem — nawet wtedy, gdy kwota do zapisania nakłada się do obszaru pamięci.

## <a name="see-also"></a>Zobacz także
- [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)