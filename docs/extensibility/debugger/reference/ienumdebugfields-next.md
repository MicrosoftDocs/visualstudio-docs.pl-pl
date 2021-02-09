---
title: 'IEnumDebugFields:: Next | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFields::Next
helpviewer_keywords:
- IEnumDebugFields::Next method
ms.assetid: 22c177a2-af81-4234-812b-f9b47be245a2
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 19d996f1a040cd07742f23f467e3f25bee1f04d4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99900036"
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

## <a name="parameters"></a>Parametry
`celt`\
podczas Liczba elementów do pobrania. Określa również maksymalny rozmiar `rgelt` tablicy.

`rgelt`\
[in. out] Tablica elementów [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) do wypełnienia.

`pceltFetched`\
określoną Zwraca liczbę elementów faktycznie zwracanych w elemencie `rgelt` .

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` . Zwraca wartość `S_FALSE` , jeśli nie można zwrócić wymaganej liczby elementów; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
