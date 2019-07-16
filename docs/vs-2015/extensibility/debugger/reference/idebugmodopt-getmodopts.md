---
title: IDebugModOpt::GetModOpts | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugModOpt::GetModOpts
- GetModOpts
ms.assetid: cb513fa9-d521-4a65-b968-f55f53a368df
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 319e059116e46d532a7c199ab863538d2154999a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68162531"
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

#### <a name="parameters"></a>Parametry
 `celt`

 [in] Liczba elementów do zwrócenia.

 `rgelt`

 [out] Zwraca tablicę, który zawiera opcje.

 `pceltFetched`

 [out w] Liczba elementów zwróconych w `rgelt` tablicy.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDebugModOpt](../../../extensibility/debugger/reference/idebugmodopt.md)