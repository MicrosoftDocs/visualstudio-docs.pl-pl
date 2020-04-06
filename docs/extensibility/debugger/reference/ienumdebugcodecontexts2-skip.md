---
title: IEnumDebugCodeContexts2::Pomiń | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugCodeContexts2::Skip
helpviewer_keywords:
- IEnumDebugCodeContexts2::Skip
ms.assetid: 3451a3eb-bf5b-4ec5-acc9-aa5a24363801
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6a1f63f5e3a6a84d6752707de5c81b4549085662
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717315"
---
# <a name="ienumdebugcodecontexts2skip"></a>IEnumDebugCodeContexts2::Skip
Przeskakuje przez określoną liczbę elementów.

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

## <a name="parameters"></a>Parametry
`celt`\
[w] Liczba elementów do pominięcia.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca . `S_FALSE` Zwraca, `celt` jeśli jest większa niż liczba pozostałych elementów; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Jeśli `celt` określa wartość większą niż liczba pozostałych elementów, wyliczenie jest `S_FALSE` ustawiona na końcu i jest zwracana.

## <a name="see-also"></a>Zobacz też
- [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)
