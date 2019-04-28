---
title: IDebugExpressionEvaluator::Parse | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::Parse
helpviewer_keywords:
- IDebugExpressionEvaluator::Parse method
ms.assetid: e6e31b3a-63a7-4293-bcda-267eb78dffb6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5a93d909fbc8882c5864097a2a36c36749327a2d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62843137"
---
# <a name="idebugexpressionevaluatorparse"></a>IDebugExpressionEvaluator::Parse
Ta metoda konwertuje ciąg wyrażenia przeanalizowany wyrażenia.

## <a name="syntax"></a>Składnia

```cpp
HRESULT Parse( 
   LPCOLESTR                upstrExpression,
   PARSEFLAGS               dwFlags,
   UINT                     nRadix,
   BSTR*                    pbstrError,
   UINT*                    pichError,
   IDebugParsedExpression** ppParsedExpression
);
```

```csharp
int Parse(
   string                     upstrExpression,
   enum_PARSEFLAGS            dwFlags,
   uint                       nRadix,
   out string                 pbstrError,
   out uint                   pichError,
   out IDebugParsedExpression ppParsedExpression
);
```

#### <a name="parameters"></a>Parametry
 `upstrExpression`

 [in] Wyrażenie ciąg, który ma być analizowany.

 `dwFlags`

 [in] Kolekcja [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md) stałe, które określają, jak wyrażenie ma zostać przeanalizowany.

 `nRadix`

 [in] Podstawy ma być używany do interpretacji wszelkie dane liczbowe.

 `pbstrError`

 [out] Zwraca błąd jako tekst czytelny dla człowieka.

 `pichError`

 [out] Zwraca pozycję znaku, Start błędu, w ciągu wyrażenia.

 `ppParsedExpression`

 [out] Zwraca wyrażenie przeanalizowany w [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) obiektu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda tworzy wyrażenie przeanalizowany, a nie wartość rzeczywistą. Przeanalizowana wyrażenie jest gotowy do można obliczyć, oznacza to, przekonwertować na wartość.

## <a name="see-also"></a>Zobacz też
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
- [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)
- [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md)