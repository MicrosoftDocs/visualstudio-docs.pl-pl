---
title: IDebugModule2::ReloadSymbols_Deprecated | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule2::ReloadSymbols
helpviewer_keywords:
- IDebugModule2::ReloadSymbols method
ms.assetid: 0f9f0133-7d58-4cd9-a6ca-1141e095749d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e776434e17d90cd2c61c926bbf0100a44ecc524b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726922"
---
# <a name="idebugmodule2reloadsymbols_deprecated"></a>IDebugModule2::ReloadSymbols_Deprecated
Przestarzałe. NIE UŻYWAĆ. Ponownie ładuje symbole dla tego modułu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT ReloadSymbols( 
   LPCOLESTR pszUrlToSymbols,
   BSTR*     pbstrDebugMessage
);
```

```csharp
int ReloadSymbols( 
   string     pszUrlToSymbols,
   out string pbstrDebugMessage
);
```

## <a name="parameters"></a>Parametry
`pszUrlToSymbols`\
[w] Ścieżka do magazynu symboli.

`pbstrDebugMessage`\
[na zewnątrz] Zwraca komunikat informacyjny, taki jak komunikat o stanie lub błędzie, który jest wyświetlany po prawej stronie nazwy modułu w oknie Moduły.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu. Aparat debugowania powinien `E_FAIL`zawsze zwracać .

## <a name="remarks"></a>Uwagi
 Ta metoda nie jest już obsługiwana. Zamiast tego [zaimplementuj metodę LoadSymbols.](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)

## <a name="see-also"></a>Zobacz też
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)
