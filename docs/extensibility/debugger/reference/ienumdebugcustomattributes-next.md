---
title: IEnumDebugCustomAttributes::Dalej | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCustomAttributes::Next
helpviewer_keywords:
- IEnumDebugCustomAttributes::Next
ms.assetid: e36f856b-2619-42d1-b73e-4f2390fc22bd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 08228fe4a630eac37c38f4eb247dc91678d8e2e2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717232"
---
# <a name="ienumdebugcustomattributesnext"></a>IEnumDebugCustomAttributes::Next
Pobiera określoną liczbę atrybutów niestandardowych w sekwencji wyliczenia.

## <a name="syntax"></a>Składnia

```cpp
HRESULT Next ( 
   ULONG      celt,
   CODE_PATH* rgelt,
   ULONG*     pceltFetched
);
```

```csharp
int Next(
   uint                        celt,
   out IDebugCustomAttribute[] rgelt,
   ref uint                    pceltFetched
);
```

## <a name="parameters"></a>Parametry
`celt`\
[w] Liczba elementów do pobrania. Określa również maksymalny rozmiar `rgelt` tablicy.

`rgelt`\
[na zewnątrz] Tablica [obiektów IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md) do wypełnienia.

`pceltFetched`\
[na zewnątrz] Zwraca liczbę elementów faktycznie `rgelt`zwróconych w .

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca . Zwraca, `S_FALSE` jeśli mniej niż żądana liczba elementów może być zwrócona; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
