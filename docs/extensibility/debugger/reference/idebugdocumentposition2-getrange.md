---
title: IDebugDocumentPosition2::GetRange | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentPosition2::GetRange
helpviewer_keywords:
- IDebugDocumentPosition2::GetRange
ms.assetid: 91a06ee7-253a-4215-be22-04bf57305aa8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a923691afdfe145931ab31d0e9bbc6142e7c8d1c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731664"
---
# <a name="idebugdocumentposition2getrange"></a>IDebugDocumentPosition2::GetRange
Pobiera zakres dla tej pozycji dokumentu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetRange( 
   TEXT_POSITION* pBegPosition,
   TEXT_POSITION* pEndPosition
);
```

```csharp
int GetRange( 
   TEXT_POSITION[] pBegPosition,
   TEXT_POSITION[] pEndPosition
);
```

## <a name="parameters"></a>Parametry
`pBegPosition`\
[w, na zewnątrz] Struktura [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) wypełniona pozycją początkową. Ustaw ten argument na wartość null, jeśli te informacje nie są potrzebne.

`pEndPosition`\
[w, na zewnątrz] Struktura [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) wypełniona pozycją końcową. Ustaw ten argument na wartość null, jeśli te informacje nie są potrzebne.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Zakres określony w pozycji dokumentu dla punktu przerwania lokalizacji jest używany przez aparat debugowania (DE) do wyszukiwania z wyprzedzeniem instrukcji, która faktycznie przyczynia się do kodu. Rozważmy na przykład następujący kod:

```
Line 5: // comment
Line 6: x = 1;
```

 Wiersz 5 nie przyczynia się do kodu do programu jest debugowany. Jeśli debuger, który ustawia punkt przerwania w wierszu 5 chce DE do wyszukiwania do przodu pewną kwotę dla pierwszego wiersza, który przyczynia się do kodu, debuger określi zakres, który zawiera dodatkowe wiersze kandydata, gdzie punkt przerwania może być prawidłowo umieszczony. DE będzie następnie przeszukiwać te wiersze, dopóki nie znajdzie wiersza, który może zaakceptować punkt przerwania.

## <a name="see-also"></a>Zobacz też
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
