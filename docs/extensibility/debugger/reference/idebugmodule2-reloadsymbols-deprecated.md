---
title: IDebugModule2::ReloadSymbols_Deprecated | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule2::ReloadSymbols
helpviewer_keywords:
- IDebugModule2::ReloadSymbols method
ms.assetid: 0f9f0133-7d58-4cd9-a6ca-1141e095749d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 635e305c0dd88d72017048da6353f813fcc46406
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66323965"
---
# <a name="idebugmodule2reloadsymbolsdeprecated"></a>IDebugModule2::ReloadSymbols_Deprecated
OBSOLETE. NIE NALEŻY UŻYWAĆ. Ponownie ładuje symbole dla tego modułu.

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
[in] Ścieżka do magazynu symboli.

`pbstrDebugMessage`\
[out] Zwraca komunikat informacyjny, takie jak stan albo komunikatu o błędzie, który jest wyświetlany po prawej stronie nazwy modułu w oknie moduły.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu. Aparat debugowania zawsze powinna zwrócić `E_FAIL`.

## <a name="remarks"></a>Uwagi
 Ta metoda nie jest już obsługiwana. Implementowanie [LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md) metody zamiast tego.

## <a name="see-also"></a>Zobacz także
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)