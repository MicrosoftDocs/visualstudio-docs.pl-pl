---
title: IEnumDebugBoundBreakpoints2::Next | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugBoundBreakpoints2::Next
helpviewer_keywords:
- IEnumDebugBoundBreakpoints2::Next
ms.assetid: cb3a249f-2282-4bdc-b6d8-a4ee4bfb8365
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 92de3edb5e0720654714555f6073c19561450c3c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66314174"
---
# <a name="ienumdebugboundbreakpoints2next"></a>IEnumDebugBoundBreakpoints2::Next
Zwraca następny zestaw elementów z wyliczenia.

## <a name="syntax"></a>Składnia

```cpp
HRESULT Next(
   ULONG                    celt,
   IDebugBoundBreakpoint2** rgelt,
   ULONG*                   pceltFetched
);
```

```csharp
int Next(
   uint                     celt,
   IDebugBoundBreakpoint2[] rgelt,
   ref uint                 pceltFetched
);
```

## <a name="parameters"></a>Parametry
`celt`\
[in] Liczba elementów do pobrania. Również określa maksymalny rozmiar `rgelt` tablicy.

`rgelt`\
[out w] Tablica [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md) elementami do wypełnienia.

`pceltFetched`\
[out] Zwraca liczbę elementów, w rzeczywistości są zwracane w `rgelt`.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`. Zwraca `S_FALSE` Jeśli mniej niż żądana liczba elementów, które mogą być zwracane; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz także
- [IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)
- [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)