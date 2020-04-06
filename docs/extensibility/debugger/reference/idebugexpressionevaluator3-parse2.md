---
title: IDebugExpressionEvaluator3::Parse2 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator3::Parse2
ms.assetid: 78099628-d600-4f76-b7c8-ee07c864af1e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5254d30ed1a656bfd357fca822efa554d895807e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729128"
---
# <a name="idebugexpressionevaluator3parse2"></a>IDebugExpressionEvaluator3::Parse2
Konwertuje ciąg wyrażenia na wyrażenie analizowane, biorąc pod uwagę dostawcę symbolu i adres ramki oceniającej.

## <a name="syntax"></a>Składnia

```cpp
HRESULT Parse2 (
    LPCOLESTR                upstrExpression,
    PARSEFLAGS               dwFlags,
    UINT                     nRadix,
    IDebugSymbolProvider*    pSymbolProvider,
    IDebugAddress*           pAddress,
    BSTR*                    pbstrError,
    UINT*                    pichError,
    IDebugParsedExpression** ppParsedExpression
);
```

```csharp
HRESULT Parse2 (
    string                     upstrExpression,
    enum_PARSEFLAGS            dwFlags,
    uint                       nRadix,
    IDebugSymbolProvider       pSymbolProvider,
    IDebugAddress              pAddress,
    out string                 pbstrError,
    out uint                   pichError,
    out IDebugParsedExpression ppParsedExpression
);
```

## <a name="parameters"></a>Parametry
`upstrExpression`\
[w] Ciąg wyrażenia, który ma być analizowany.

`dwFlags`\
[w] Kolekcja [parseflags](../../../extensibility/debugger/reference/parseflags.md) stałych, które określają, jak wyrażenie ma być analizowane.

`nRadix`\
[w] Radix do interpretacji wszelkich informacji liczbowych.

`pSymbolProvider`\
[w] Interfejs dostawcy symbolu.

`pAddress`\
[w] Adres ramki oceniającej.

`pbstrError`\
[na zewnątrz] Zwraca błąd jako tekst czytelny dla człowieka.

`pichError`\
[na zewnątrz] Zwraca położenie znaku początku błędu w ciągu wyrażenia.

`ppParsedExpression`\
[na zewnątrz] Zwraca analizowane wyrażenie w [obiekcie IDebugParsedExpression.](../../../extensibility/debugger/reference/idebugparsedexpression.md)

## <a name="return-value"></a>Wartość zwracana
Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
Ta metoda tworzy wyrażenie analizowane, a nie wartość rzeczywistą. Analizowane wyrażenie jest gotowe do oceny, czyli przekonwertowane na wartość.

## <a name="example"></a>Przykład
W poniższym przykładzie pokazano, jak zaimplementować tę metodę dla obiektu **CEE,** który udostępnia interfejs [IDebugExpressionEvaluator3.](../../../extensibility/debugger/reference/idebugexpressionevaluator3.md)

```cpp
HRESULT CEE::Parse2 ( LPCOLESTR in_szExprText,
  PARSEFLAGS in_FLAGS,
  UINT in_RADIX,
  IDebugSymbolProvider *pSymbolProvider,
  IDebugAddress *pAddress,
  BSTR* out_pbstrError,
  UINT* inout_pichError,
  IDebugParsedExpression** out_ppParsedExpression )
{
    // precondition
    REQUIRE( NULL != in_szExprText );
    //REQUIRE( NULL != out_pbstrError );
    REQUIRE( NULL != inout_pichError );
    REQUIRE( NULL != out_ppParsedExpression );

    if (NULL == in_szExprText)
        return E_INVALIDARG;

    if (NULL == inout_pichError)
        return E_POINTER;

    if (NULL == out_ppParsedExpression)
        return E_POINTER;

    if (out_pbstrError)
        *out_pbstrError = NULL;

    *out_ppParsedExpression = NULL;

    INVARIANT( this );

    if (!this->ClassInvariant())
        return E_UNEXPECTED;

    // function body
    EEDomain::fParseExpression DomainVal =
    {
        this,                   // CEE*
        in_szExprText,          // LPCOLESTR
        in_FLAGS,               // EVALFLAGS
        in_RADIX,               // RADIX
        out_pbstrError,         // BSTR*
        inout_pichError,        // UINT*
        pSymbolProvider,
        out_ppParsedExpression  // Output
    };

    return (*m_LanguageSpecificUseCases.pfParseExpression)(DomainVal);
}
```

## <a name="see-also"></a>Zobacz też
- [IDebugExpressionEvaluator3](../../../extensibility/debugger/reference/idebugexpressionevaluator3.md)
