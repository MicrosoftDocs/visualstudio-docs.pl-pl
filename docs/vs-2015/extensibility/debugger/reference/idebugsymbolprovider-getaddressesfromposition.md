---
title: IDebugSymbolProvider::GetAddressesFromPosition | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugSymbolProvider::GetAddressesFromPosition
helpviewer_keywords:
- IDebugSymbolProvider::GetAddressesFromPosition method
ms.assetid: 1b0f02cb-8ace-4614-88f3-0e10239012b3
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 11654670e1a4b2755f1d3111c991dca542e96099
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51743259"
---
# <a name="idebugsymbolprovidergetaddressesfromposition"></a>IDebugSymbolProvider::GetAddressesFromPosition
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ta metoda mapuje położenie dokumentu na tablicę adresów debugowania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT GetAddressesFromPosition(   
   IDebugDocumentPosition2* pDocPos,  
   BOOL                     fStatmentOnly,  
   IEnumDebugAddresses**    ppEnumBegAddresses,  
   IEnumDebugAddresses**    ppEnumEndAddresses  
);  
```  
  
```csharp  
int GetAddressesFromPosition(   
   IDebugDocumentPosition2  pDocPos,  
   bool                     fStatmentOnly,  
   out IEnumDebugAddresses  ppEnumBegAddresses,  
   out IEnumDebugAddresses  ppEnumEndAddresses  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pDocPos`  
 [in] Położenie dokumentu.  
  
 `fStatmentOnly`  
 [in] W przypadku opcji TRUE ogranicza adresy debugowania do pojedynczej instrukcji.  
  
 `ppEnumBegAddresses`  
 [out] Zwraca moduł wyliczający dla wyjścia adresów debugowania skojarzone z tym instrukcja lub wiersza.  
  
 `ppEnumEndAddresses`  
 [out] Zwraca [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md) modułu wyliczającego dla końcowy adresów debugowania skojarzone z tym instrukcja lub wiersza.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Położenie dokumentu zazwyczaj wskazuje zakres wierszy źródłowych. Ta metoda zapewnia początkowy i końcowy adres debugowania powiązanych z tymi wierszami. W niektórych językach umożliwiają instrukcji, które rozciągają się wiele wierszy lub wiersze, które zawiera więcej niż jedną instrukcję. Ta metoda zapewnia flagi, aby ograniczyć adresy debugowania do pojedynczej instrukcji.  
  
 Istnieje możliwość dla pojedynczej instrukcji wielu adresów debugowania, tak jak w przypadku szablonów.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)   
 [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)

