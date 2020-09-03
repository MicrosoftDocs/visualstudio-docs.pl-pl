---
title: IDebugExpressionEvaluator3::P arse2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator3::Parse2
ms.assetid: 78099628-d600-4f76-b7c8-ee07c864af1e
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3c8629fb996dd020882ce81ae9975ccd799d863c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148973"
---
# <a name="idebugexpressionevaluator3parse2"></a>IDebugExpressionEvaluator3::Parse2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Konwertuje ciąg wyrażenia na wyrażenie analizowane przez dostawcę symboli i adres obliczanej ramki.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
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
  
#### <a name="parameters"></a>Parametry  
 `upstrExpression`  
 podczas Ciąg wyrażenia, który ma zostać przeanalizowany.  
  
 `dwFlags`  
 podczas Kolekcja stałych [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md) , które określają, w jaki sposób wyrażenie ma być analizowane.  
  
 `nRadix`  
 podczas Podstawy do interpretowania wszelkich informacji numerycznych.  
  
 `pSymbolProvider`  
 podczas Interfejs dostawcy symboli.  
  
 `pAddress`  
 podczas Adres obliczanej ramki.  
  
 `pbstrError`  
 określoną Zwraca błąd jako tekst czytelny dla człowieka.  
  
 `pichError`  
 określoną Zwraca pozycję znaku początku błędu w ciągu wyrażenia.  
  
 `ppParsedExpression`  
 określoną Zwraca przeanalizowane wyrażenie w obiekcie [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) .  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda generuje wyrażenie analizowane, a nie wartość rzeczywistą. Wyrażenie analizowane jest gotowe do obliczenia, czyli jest konwertowane na wartość.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak zaimplementować tę metodę dla obiektu **CEE** , który uwidacznia Interfejs [IDebugExpressionEvaluator3](../../../extensibility/debugger/reference/idebugexpressionevaluator3.md) .  
  
```cpp#  
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
        out_pbstrError      ,   // BSTR*  
        inout_pichError,        // UINT*  
        pSymbolProvider,  
        out_ppParsedExpression  // Output  
    };  
  
    return (*m_LanguageSpecificUseCases.pfParseExpression)(DomainVal);  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugExpressionEvaluator3](../../../extensibility/debugger/reference/idebugexpressionevaluator3.md)
