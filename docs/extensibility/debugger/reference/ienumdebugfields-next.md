---
title: IEnumDebugFields::Next | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFields::Next
helpviewer_keywords:
- IEnumDebugFields::Next method
ms.assetid: 22c177a2-af81-4234-812b-f9b47be245a2
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a39725f316e63b8c6768471164b69feb47c05728
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62867241"
---
# <a name="ienumdebugfieldsnext"></a>IEnumDebugFields::Next
Ta metoda zwraca następny zestaw elementów z wyliczenia.

## <a name="syntax"></a>Składnia

```cpp
HRESULT Next(
   ULONG         celt,
   IDebugField** rgelt,
   ULONG*        pceltFetched
);
```

```csharp
int Next(
   uint          celt,
   IDebugField[] rgelt,
   ref uint      pceltFetched
);
```

#### <a name="parameters"></a>Parametry
 `celt`

 [in] Liczba elementów do pobrania. Również określa maksymalny rozmiar `rgelt` tablicy.

 `rgelt`

 [out w] Tablica [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) elementami do wypełnienia.

 `pceltFetched`

 [out] Zwraca liczbę elementów, w rzeczywistości są zwracane w `rgelt`.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`. Zwraca `S_FALSE` Jeśli mniej niż żądana liczba elementów, które mogą być zwracane; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)