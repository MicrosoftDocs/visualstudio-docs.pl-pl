---
title: IDebugComPlusSymbolProvider::GetLocalVariablelayout | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- GetLocalVariablelayout
- IDebugComPlusSymbolProvider::GetLocalVariablelayout
ms.assetid: b7328d85-e5e9-4d9f-bcd1-e7711fd33878
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f5ed664c3c9b018be6e29b5129c375d1e8f5eb41
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62922729"
---
# <a name="idebugcomplussymbolprovidergetlocalvariablelayout"></a>IDebugComPlusSymbolProvider::GetLocalVariablelayout
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Pobiera układ zmienne lokalne, aby uzyskać zestaw metod.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT GetLocalVariablelayout(  
   ULONG32   ulAppDomainID,  
   GUID      guidModule,  
   ULONG32   cMethods,  
   _mdToken  rgMethodTokens[],  
   IStream** pStreamLayout  
);  
```  
  
```csharp  
int GetLocalVariablelayout(  
   uint        ulAppDomainID,  
   Guid        guidModule,  
   uint        cMethods,  
   int[]       rgMethodTokens,  
   out IStream pStreamLayout  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ulAppDomainID`  
 [in] Identyfikator domeny aplikacji.  
  
 `guidModule`  
 [in] Unikatowy identyfikator modułu.  
  
 `cMethods`  
 [in] Liczba metoda tokenów w `rgMethodTokens` tablicy.  
  
 `rgMethodTokens`  
 [in] Tablica metody.  
  
 `pStreamLayout`  
 [out] Strumień tekst, który zawiera zmienną układu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak zaimplementować tę metodę, aby uzyskać **CDebugSymbolProvider** obiekt ujawniający [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) interfejsu.  
  
```cpp#  
HRESULT CDebugSymbolProvider::GetLocalVariablelayout(  
    ULONG32 ulAppDomainID,   
    GUID guidModule,   
    ULONG32 cMethods,   
    _mdToken rgMethodTokens[],   
    IStream** ppStreamLayout)  
{  
    HRESULT hr = S_OK;  
  
    METHOD_ENTRY(CDebugSymbolProvider::GetLocalVariablelayout);  
  
    CComPtr<ISymUnmanagedReader> symReader;  
    IfFailRet(GetSymUnmanagedReader(ulAppDomainID, guidModule, (IUnknown **) &symReader));  
    CComPtr<IStream> stream;  
    IfFailRet(CreateStreamOnHGlobal(NULL, true, &stream));  
  
    for (ULONG32 iMethod = 0; iMethod < cMethods; iMethod += 1)  
    {  
        CComPtr<ISymUnmanagedMethod> method;  
        IfFailRet(symReader->GetMethod(rgMethodTokens[iMethod], &method));  
        CComPtr<ISymUnmanagedScope> rootScope;  
        IfFailRet(method->GetRootScope(&rootScope));  
  
        //  
        // Add the method's variables to the stream  
        //  
        IfFailRet(AddScopeToStream(rootScope, 0, stream));  
  
        // do end of method marker  
        ULONG32 depth = 0xFFFFFFFF;  
        ULONG cb = 0;  
        IfFailRet(stream->Write(&depth, sizeof(depth), &cb));  
    }  
  
    LARGE_INTEGER pos;  
    pos.QuadPart = 0;  
    IfFailRet(stream->Seek(pos, STREAM_SEEK_SET, 0));  
    *ppStreamLayout = stream.Detach();  
  
    METHOD_EXIT(CDebugSymbolProvider::GetLocalVariablelayout, hr);  
    return hr;  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)
