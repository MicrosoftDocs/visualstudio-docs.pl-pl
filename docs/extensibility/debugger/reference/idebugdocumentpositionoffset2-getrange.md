---
title: IDebugDocumentPositionOffset2::GetRange | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentPositionOffset2::GetRange
ms.assetid: 27da7130-0932-4f97-abde-05e6fb018606
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e8b309af47aed94c45eca418b390be041f66f609
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56686915"
---
# <a name="idebugdocumentpositionoffset2getrange"></a>IDebugDocumentPositionOffset2::GetRange
Pobiera zakres dla bieżącej pozycji dokumentu.

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

#### <a name="parameters"></a>Parametry
 `pdwBegOffset`

 [out w] Przesunięcia dla pozycja początkowa zakresu. Ustaw ten parametr ma wartość null, jeśli te informacje nie są potrzebne.

 `pdwEndOffset`

 [out w] Przesunięcia dla pozycja końcowa zakresu. Ustaw ten parametr ma wartość null, jeśli te informacje nie są potrzebne.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Zakres określony w pozycji dokument w lokalizacji punktu przerwania jest używany przez aparat debugowania (DE) do przodu wyszukiwania instrukcję, która faktycznie przyczynia się kod. Na przykład rozważmy następujący kod:

```
Line 5: // comment
Line 6: x = 1;
```

 Wiersz 5 przyczynia się żadnego kodu do debugowanego programu. Jeśli debuger, która ustawia punkt przerwania w wierszu 5 chce DE wyszukiwania do przodu pewien dla pierwszego wiersza, która wspiera kodu, debuger określić zakres, który zawiera wiersze dodatkowe Release candidate, gdzie punkt przerwania mogą zostać prawidłowo umieszczone. DE będzie następnie wyszukuj do przodu, za pomocą tych wierszy aż do znalezienia go wiersza, który mógłby odebrać punktu przerwania.

## <a name="see-also"></a>Zobacz też
- [IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)
- [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)