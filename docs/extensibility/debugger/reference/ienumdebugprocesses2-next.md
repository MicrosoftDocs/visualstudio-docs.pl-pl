---
title: IEnumDebugProcesses2::Następny | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugProcesses2::Next
helpviewer_keywords:
- IEnumDebugProcesses2::Next
ms.assetid: abef89eb-198b-49cd-a4c9-17bce6cac0e1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cbfab7f13160129249afe7139ef3c402ba9801ee
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715826"
---
# <a name="ienumdebugprocesses2next"></a>IEnumDebugProcesses2::Next
Zwraca następny zestaw elementów z wyliczenia.

## <a name="syntax"></a>Składnia

```cpp
HRESULT Next(
   ULONG            celt,
   IDebugProcess2** rgelt,
   ULONG*           pceltFetched
);
```

```csharp
int Next(
   uint             celt,
   IDebugProcess2[] rgelt,
   ref uint         pceltFetched
);
```

## <a name="parameters"></a>Parametry
`celt`\
[w] Liczba elementów do pobrania. Określa również maksymalny rozmiar `rgelt` tablicy.

`rgelt`\
[w, na zewnątrz] Tablica elementów [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) do wypełnienia.

`pceltFetched`\
[na zewnątrz] Zwraca liczbę elementów faktycznie `rgelt`zwróconych w .

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca . Zwraca, `S_FALSE` jeśli mniej niż żądana liczba elementów może być zwrócona; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
