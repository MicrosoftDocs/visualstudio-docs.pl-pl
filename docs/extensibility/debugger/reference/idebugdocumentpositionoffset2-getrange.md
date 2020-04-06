---
title: IDebugDocumentPositionOffset2::GetRange | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentPositionOffset2::GetRange
ms.assetid: 27da7130-0932-4f97-abde-05e6fb018606
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fd305b6506471a40de90fbd954e54461d2a139d0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731629"
---
# <a name="idebugdocumentpositionoffset2getrange"></a>IDebugDocumentPositionOffset2::GetRange
Pobiera zakres dla bieżącego położenia dokumentu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetRange(
   DWORD* pdwBegOffset,
   DWORD* pdwEndOffset
);
```

```csharp
public int GetRange(
   ref uint pdwBegOffset,
   ref uint pdwEndOffset
);
```

## <a name="parameters"></a>Parametry
`pdwBegOffset`\
[w, na zewnątrz] Przesunięcie dla pozycji początkowej zakresu. Ustaw ten parametr na wartość null, jeśli te informacje nie są potrzebne.

`pdwEndOffset`\
[w, na zewnątrz] Przesunięcie dla pozycji końcowej zakresu. Ustaw ten parametr na wartość null, jeśli te informacje nie są potrzebne.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Zakres określony w pozycji dokumentu dla punktu przerwania lokalizacji jest używany przez aparat debugowania (DE) do wyszukiwania z wyprzedzeniem instrukcji, która faktycznie przyczynia się do kodu. Rozważmy na przykład następujący kod:

```
Line 5: // comment
Line 6: x = 1;
```

 Wiersz 5 nie przyczynia się do kodu do programu jest debugowany. Jeśli debuger, który ustawia punkt przerwania w wierszu 5 chce DE do wyszukiwania do przodu pewną kwotę dla pierwszego wiersza, który przyczynia się do kodu, debuger określi zakres, który zawiera dodatkowe wiersze kandydata, gdzie punkt przerwania może być poprawnie umieszczony. DE będzie następnie przeszukiwać te wiersze, dopóki nie znajdzie wiersza, który może zaakceptować punkt przerwania.

## <a name="see-also"></a>Zobacz też
- [IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)
- [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)
