---
title: IDebugDocumentContext2::GetSourceRange | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::GetSourceRange
helpviewer_keywords:
- IDebugDocumentContext2::GetSourceRange
ms.assetid: 5903c75e-5390-4d13-9314-1ee276255313
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 782cf230c38af77da09b49f69c093e2e95bf7199
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731800"
---
# <a name="idebugdocumentcontext2getsourcerange"></a>IDebugDocumentContext2::GetSourceRange
Pobiera zakres kodu źródłowego tego kontekstu dokumentu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetSourceRange( 
   TEXT_POSITION* pBegPosition,
   TEXT_POSITION* pEndPosition
);
```

```csharp
int GetSourceRange( 
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
 Zakres źródłowy jest cały zakres kodu źródłowego, od bieżącej instrukcji z powrotem do tuż po poprzedniej instrukcji, które przyczyniły się do kodu. Zakres źródłowy jest zwykle używany do mieszania instrukcji źródłowych, w tym komentarzy, z kodem w oknie demontażu.

 Aby uzyskać zakres tylko dla instrukcji kodu zawartych w tym kontekście dokumentu, wywołać [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md) metody.

## <a name="see-also"></a>Zobacz też
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
