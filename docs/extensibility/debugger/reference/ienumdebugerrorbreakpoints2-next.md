---
title: IEnumDebugErrorBreakpoints2::Następny | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugErrorBreakpoints2::Next
helpviewer_keywords:
- IEnumDebugErrorBreakpoints2::Next
ms.assetid: 6a3dee11-5267-4d77-9e28-6a38413ba70b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9e98a11fbae630c085a699a400efcec83bbcaeea
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717006"
---
# <a name="ienumdebugerrorbreakpoints2next"></a>IEnumDebugErrorBreakpoints2::Next
Zwraca następny zestaw elementów z wyliczenia.

## <a name="syntax"></a>Składnia

```cpp
HRESULT Next(
   ULONG                    celt,
   IDebugErrorBreakpoint2** rgelt,
   ULONG*                   pceltFetched
);
```

```csharp
int Next(
   uint                     celt,
   IDebugErrorBreakpoint2[] rgelt,
   ref uint                 pceltFetched
);
```

## <a name="parameters"></a>Parametry
`celt`\
[w] Liczba elementów do pobrania. Określa również maksymalny rozmiar `rgelt` tablicy.

`rgelt`\
[w, na zewnątrz] Tablica [elementów IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) do wypełnienia.

`pceltFetched`\
[na zewnątrz] Zwraca liczbę elementów faktycznie `rgelt`zwróconych w .

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca . Zwraca, `S_FALSE` jeśli mniej niż żądana liczba elementów może być zwrócona; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)
- [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
