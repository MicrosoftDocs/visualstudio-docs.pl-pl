---
title: IDebugModOpt::GetModOpts | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugModOpt::GetModOpts
- GetModOpts
ms.assetid: cb513fa9-d521-4a65-b968-f55f53a368df
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5ab870db3ae3517b60bebd4815e4530f6035b327
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727051"
---
# <a name="idebugmodoptgetmodopts"></a>IDebugModOpt::GetModOpts
Pobiera listę modyfikatorów opcjonalnych.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetModOpts(
   ULONG  celt,
   BSTR*  rgelt,
   ULONG* pceltFetched
);
```

```csharp
int GetModOpts(
   uint         celt,
   out string[] rgelt,
   ref uint     pceltFetched
);
```

## <a name="parameters"></a>Parametry
`celt`\
[w] Liczba elementów, które mają zostać zwrócone.

`rgelt`\
[na zewnątrz] Zwraca tablicę zawierającą opcje.

`pceltFetched`\
[w, na zewnątrz] Liczba elementów zwróconych w tablicy. `rgelt`

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDebugModOpt](../../../extensibility/debugger/reference/idebugmodopt.md)
