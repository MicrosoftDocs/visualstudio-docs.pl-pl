---
title: IDebugModOpt::GetModOpts | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugModOpt::GetModOpts
- GetModOpts
ms.assetid: cb513fa9-d521-4a65-b968-f55f53a368df
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f5ebced053b80af8dce81d41e6614e89e4ffbf3a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66324009"
---
# <a name="idebugmodoptgetmodopts"></a>IDebugModOpt::GetModOpts
Pobiera listę Modyfikatory opcjonalne.

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
[in] Liczba elementów do zwrócenia.

`rgelt`\
[out] Zwraca tablicę, który zawiera opcje.

`pceltFetched`\
[out w] Liczba elementów zwróconych w `rgelt` tablicy.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz także
- [IDebugModOpt](../../../extensibility/debugger/reference/idebugmodopt.md)