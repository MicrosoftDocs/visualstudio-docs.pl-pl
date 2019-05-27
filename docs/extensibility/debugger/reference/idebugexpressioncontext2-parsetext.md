---
title: IDebugExpressionContext2::ParseText | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionContext2::ParseText
helpviewer_keywords:
- IDebugExpressionContext2::ParseText
ms.assetid: f58575db-f926-4ac8-83ff-7b3b86ab61e2
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f0f11c3b1770ca32b34f7a5480d5d56acc2b2478
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66201045"
---
# <a name="idebugexpressioncontext2parsetext"></a>IDebugExpressionContext2::ParseText
Analizuje wyrażenia w postaci tekstu do późniejszego obliczenia.

## <a name="syntax"></a>Składnia

```cpp
HRESULT ParseText(
    LPCOLESTR           pszCode,
    PARSEFLAGS          dwFlags,
    UINT                nRadix,
    IDebugExpression2** ppExpr,
    BSTR*               pbstrError,
    UINT*               pichError
);
```

```csharp
int ParseText(
    string                pszCode,
    enum_PARSEFLAGS       dwFlags,
    uint                  nRadix,
    out IDebugExpression2 ppExpr,
    out string            pbstrError,
    out uint              pichError
);
```

## <a name="parameters"></a>Parametry
`pszCode`\
[in] Wyrażenie które ma być analizowany.

`dwFlags`\
[in] Kombinacja flag z [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md) wyliczenie, które kontroluje analizy.

`nRadix`\
[in] Podstawy, który ma być używany podczas analizowania wszelkie dane liczbowe w `pszCode`.

`ppExpr`\
[out] Zwraca [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) obiekt, który reprezentuje przeanalizowany wyrażenie, który jest gotowy do powiązania i oceny.

`pbstrError`\
[out] Zwraca komunikat o błędzie, jeśli wyrażenie zawiera błąd.

`pichError`\
[out] Zwraca indeks znaków błędu w `pszCode` Jeśli wyrażenie zawiera błąd.

## <a name="return-value"></a>Wartość zwracana
Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
Gdy ta metoda jest wywoływana, aparat debugowania (DE) należy przeanalizować wyrażenia i zweryfikuje go pod kątem poprawności. `pbstrError` i `pichError` parametry mogą być wypełniane, jeśli wyrażenie jest nieprawidłowe.

Należy pamiętać, że wyrażenie nie jest oceniany, tylko przeanalizować. Nowsze wywołanie [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) lub [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) metody oblicza wyrażenie przeanalizowany.

## <a name="example"></a>Przykład
Poniższy przykład pokazuje, jak zaimplementować tę metodę dla prostego `CEnvBlock` obiekt ujawniający [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) interfejsu. W tym przykładzie uwzględnia wyrażenie które ma być analizowana jako nazwę zmiennej środowiskowej i pobiera wartość z tej zmiennej.

```cpp
HRESULT CEnvBlock::ParseText(
    LPCOLESTR           pszCode,
    PARSEFLAGS          dwFlags,
    UINT                nRadix,
    IDebugExpression2 **ppExpr,
    BSTR               *pbstrError,
    UINT               *pichError)
{
    HRESULT hr = E_OUTOFMEMORY;
    // Create an integer variable with a value equal to one plus
    // twice the length of the passed expression to be parsed.
    int iAnsiLen      = 2 * (wcslen(pszCode)) + 1;
    // Allocate a character string of the same length.
    char *pszAnsiCode = (char *) malloc(iAnsiLen);

    // Check for successful memory allocation.
    if (pszAnsiCode) {
        // Map the wide-character pszCode string to the new pszAnsiCode character string.
        WideCharToMultiByte(CP_ACP, 0, pszCode, -1, pszAnsiCode, iAnsiLen, NULL, NULL);
        // Check to see if the app can succesfully get the environment variable.
        if (GetEnv(pszAnsiCode)) {

            // Create and initialize a CExpression object.
            CComObject<CExpression> *pExpr;
            CComObject<CExpression>::CreateInstance(&pExpr);
            pExpr->Init(pszAnsiCode, this, NULL);

            // Assign the pointer to the new object to the passed argument
            // and AddRef the object.
            *ppExpr = pExpr;
            (*ppExpr)->AddRef();
            hr = S_OK;
        // If the program cannot succesfully get the environment variable.
        } else {
            // Set the errror message and return E_FAIL.
            *pbstrError = SysAllocString(L"No such environment variable.");
            hr = E_FAIL;
        }
        // Free the local character string.
        free(pszAnsiCode);
    }
    return hr;
}
```

## <a name="see-also"></a>Zobacz także
- [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)
- [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md)
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)
