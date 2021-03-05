---
description: Pobiera listę opcjonalnych modyfikatorów.
title: 'IDebugModOpt:: GetModOpts | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugModOpt::GetModOpts
- GetModOpts
ms.assetid: cb513fa9-d521-4a65-b968-f55f53a368df
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 971d04662042afed1afe8e1861d0080b513ca74d
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149941"
---
# <a name="idebugmodoptgetmodopts"></a>IDebugModOpt::GetModOpts
Pobiera listę opcjonalnych modyfikatorów.

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
podczas Liczba elementów, które mają zostać zwrócone.

`rgelt`\
określoną Zwraca tablicę zawierającą opcje.

`pceltFetched`\
[in. out] Liczba elementów zwracanych w `rgelt` tablicy.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDebugModOpt](../../../extensibility/debugger/reference/idebugmodopt.md)
