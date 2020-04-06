---
title: IDebugDocumentContext2::GetStatementRange | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::GetStatementRange
helpviewer_keywords:
- IDebugDocumentContext2::GetStatementRange
ms.assetid: bc94851a-0ec4-47ea-99c7-0a585e54e726
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 50e521d98f10477d56dfece30e20fd000b87b632
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731770"
---
# <a name="idebugdocumentcontext2getstatementrange"></a>IDebugDocumentContext2::GetStatementRange
Pobiera zakres instrukcji pliku kontekstu dokumentu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetStatementRange(
    TEXT_POSITION* pBegPosition,
    TEXT_POSITION* pEndPosition
);
```

```csharp
int GetStatementRange(
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
Zakres instrukcji to zakres wierszy, które przyczyniły się do kodu, do którego odnosi się ten kontekst dokumentu.

Aby uzyskać zakres kodu źródłowego (w tym komentarze) w tym kontekście dokumentu, należy wywołać [GetSourceRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md) metody.

## <a name="example"></a>Przykład
W poniższym przykładzie pokazano, jak `CDebugContext` zaimplementować tę metodę dla prostego obiektu, który udostępnia interfejs [IDebugDocumentContext2.](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) W tym przykładzie wypełnia się pozycję końcową tylko wtedy, gdy pozycja początkowa nie jest wartością null.

```cpp
HRESULT CDebugContext::GetStatementRange(TEXT_POSITION* pBegPosition,
                                         TEXT_POSITION* pEndPosition)
{
    HRESULT hr;

    // Check for a valid beginning position argument pointer.
    if (pBegPosition)
    {
        // Copy the member TEXT_POSITION into the local pBegPosition.
        memcpy(pBegPosition, &m_pos, sizeof (TEXT_POSITION));

        // Check for a valid ending position argument pointer.
        if (pEndPosition)
        {
            // Copy the member TEXT_POSITION into the local pEndPosition.
            memcpy(pEndPosition, &m_pos, sizeof (TEXT_POSITION));
        }
        hr = S_OK;
    }
    else
    {
        hr = E_INVALIDARG;
    }

    return hr;
}
```

## <a name="see-also"></a>Zobacz też
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [GetSourceRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
