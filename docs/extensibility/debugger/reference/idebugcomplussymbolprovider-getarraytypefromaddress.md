---
title: IDebugComPlusSymbolProvider::GetArrayTypeFromAddress | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GetArrayTypeFromAddress
- IDebugComPlusSymbolProvider::GetArrayTypeFromAddress
ms.assetid: cc0c53f1-8c0f-49fa-8dbe-bc155e9ce0ef
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6131b3a52ab7ee092f69bcb4970c28500337c021
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54941538"
---
# <a name="idebugcomplussymbolprovidergetarraytypefromaddress"></a>IDebugComPlusSymbolProvider::GetArrayTypeFromAddress
Pobiera typ informacji o określonej tablicy, na podstawie jego adresu debugowania.  
  
## <a name="syntax"></a>Składnia  
  
```  
[C++]  
HRESULT GetArrayTypeFromAddress(  
   IDebugAddress* pAddress,  
   BYTE*          pSig,  
   DWORD          dwSigLength,  
   IDebugField**  ppField  
);  
```  
  
```  
[C#]  
int GetArrayTypeFromAddress(  
   IDebugAddress   pAddress,  
   int[]           pSig,  
   uint            dwSigLength,  
   out IDebugField ppField  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pAddress`  
 [in] Adres debugowania reprezentowany przez [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interfejsu.  
  
 `pSig`  
 [in] Tablica do sprawdzenia.  
  
 `dwSigLength`  
 [in] Długość w bajtach `pSig` tablicy.  
  
 `ppField`  
 [out] Zwraca typ tablicy, reprezentowane przez [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) interfejsu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak zaimplementować tę metodę, aby uzyskać **CDebugSymbolProvider** obiekt ujawniający [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) interfejsu.  
  
```cpp  
HRESULT CDebugSymbolProvider::GetArrayTypeFromAddress(  
    IDebugAddress *pAddress,  
    BYTE *pSig,  
    DWORD dwSigLength,  
    IDebugField **ppField)  
{  
    HRESULT hr = E_FAIL;  
    CDEBUG_ADDRESS da;  
    CDebugGenericParamScope* pGenScope = NULL;  
  
    METHOD_ENTRY( CDebugDynamicFieldSymbol::GetArrayTypeFromAddress );  
  
    ASSERT(IsValidObjectPtr(this, CDebugSymbolProvider));  
    ASSERT(IsValidWritePtr(ppField, IDebugField*));  
  
    IfFailGo( pAddress->GetAddress(&da) );  
  
    if ( S_OK == hr )  
    {  
        IfNullGo( pGenScope = new CDebugGenericParamScope(da.GetModule(), da.tokClass, da.GetMethod()), E_OUTOFMEMORY );  
  
        IfFailGo( this->CreateType((const COR_SIGNATURE*)(pSig), dwSigLength, da.GetModule(), mdMethodDefNil, pGenScope, ppField) );  
    }  
  
Error:  
  
    METHOD_EXIT( CDebugDynamicFieldSymbol::GetArrayTypeFromAddress, hr );  
    RELEASE( pGenScope );  
    return hr;  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)