---
title: IEnumDebugPorts2::Next | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPorts2::Next
helpviewer_keywords:
- IEnumDebugPorts2::Next
ms.assetid: 3f43d18c-6bd1-4ddd-95ef-9550abd2ad09
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2245bc6032ebb8df400f595079039b49cee08075
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66339328"
---
# <a name="ienumdebugports2next"></a>IEnumDebugPorts2::Next
Zwraca następny zestaw elementów z wyliczenia.

## <a name="syntax"></a>Składnia

```cpp
HRESULT Next(
   ULONG         celt,
   IDebugPort2** rgelt,
   ULONG*        pceltFetched
);
```

```csharp
int Next(
   uint          celt,
   IDebugPort2[] rgelt,
   ref uint      pceltFetched
);
```

## <a name="parameters"></a>Parametry
`celt`\
[in] Liczba elementów do pobrania. Również określa maksymalny rozmiar `rgelt` tablicy.

`rgelt`\
[out w] Tablica [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) elementami do wypełnienia.

`pceltFetched`\
[out] Zwraca liczbę elementów, w rzeczywistości są zwracane w `rgelt`.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`. Zwraca `S_FALSE` Jeśli mniej niż żądana liczba elementów, które mogą być zwracane; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz także
- [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)