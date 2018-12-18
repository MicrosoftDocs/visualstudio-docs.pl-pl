---
title: IDebugComPlusSymbolProvider::GetSymAttribute | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugComPlusSymbolProvider::GetSymAttribute
- GetSymAttribute
ms.assetid: 6cbaac92-a60b-4165-a7f5-c34407770f3c
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2d6645f7bbda6daa8f51bc63244027cf484bb8ec
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51743602"
---
# <a name="idebugcomplussymbolprovidergetsymattribute"></a>IDebugComPlusSymbolProvider::GetSymAttribute
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Pobiera symbole debugowania z atrybutem nadrzędnym podanego dla określonego modułu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT GetSymAttribute (  
   ULONG32  ulAppDomainID,  
   GUID     guidModule,  
   _mdToken tokParent,  
   LPOLESTR pstrName,  
   ULONG32  cBuffer,  
   ULONG32* pcBuffer,  
   BYTE*    buffer  
);  
```  
  
```csharp  
int GetSymAttribute (  
   uint      ulAppDomainID,  
   Guid      guidModule,  
   int       tokParent,  
   string    pstrName,  
   uint      cBuffer,  
   out uint  pcBuffer,  
   out int[] buffer  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ulAppDomainID`  
 [in] Identyfikator domeny aplikacji.  
  
 `guidModule`  
 [in] Unikatowy identyfikator modułu.  
  
 `tokParent`  
 [in] Token dla atrybutu nadrzędnego.  
  
 `pstrName`  
 [in] Nazwa modułu.  
  
 `cBuffer`  
 [in] Liczba bajtów potrzebnych dla danych wyjściowych `buffer`.  
  
 `pcBuffer`  
 [out] Długość danych wyjściowych `buffer`.  
  
 `buffer`  
 [out] Tablica, która zawiera symbole.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak zaimplementować tę metodę, aby uzyskać **CDebugSymbolProvider** obiekt ujawniający [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) interfejsu.  
  
```cpp#  
HRESULT CDebugSymbolProvider::GetSymAttribute(  
    ULONG32 ulAppDomainID,  
    GUID guidModule,  
    _mdToken tokParent,  
    __in_z LPOLESTR pstrName,  
    ULONG32 cBuffer,  
    ULONG32 *pcBuffer,  
    BYTE buffer[])  
{  
    HRESULT hr = S_OK;  
    CComPtr<CModule> pModule;  
    Module_ID idModule(ulAppDomainID, guidModule);  
  
    METHOD_ENTRY( CDebugSymbolProvider::GetSymAttribute );  
  
    IfFailGo( GetModule( idModule, &pModule) );  
  
    IfFailGo( pModule->GetSymAttribute( tokParent, pstrName, cBuffer, pcBuffer, buffer ) );  
  
Error:  
  
    METHOD_EXIT(CDebugSymbolProvider::GetSymAttribute, hr);  
  
    return hr;  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)

