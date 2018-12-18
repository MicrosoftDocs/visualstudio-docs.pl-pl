---
title: IDebugSymbolProvider::GetAddressesFromContext | Dokumentacja firmy Microsoft
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
- IDebugSymbolProvider::GetAddressesFromContext
helpviewer_keywords:
- IDebugSymbolProvider::GetAddressesFromContext method
ms.assetid: a3124883-a255-4543-a5ec-e1c7a97beb69
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1f7a38559e4cb67e5d714a9f4d82ad635e87bfb5
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51725491"
---
# <a name="idebugsymbolprovidergetaddressesfromcontext"></a>IDebugSymbolProvider::GetAddressesFromContext
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ta metoda mapuje kontekstu dokumentu na tablicę adresów debugowania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT GetAddressesFromContext(   
   IDebugDocumentContext2* pDocContext,  
   BOOL                    fStatmentOnly,  
   IEnumDebugAddresses**   ppEnumBegAddresses,  
   IEnumDebugAddresses**   ppEnumEndAddresses  
);  
```  
  
```csharp  
int GetAddressesFromContext(  
   IDebugDocumentContext2  pDocContext,  
   bool                    fStatmentOnly,  
   out IEnumDebugAddresses ppEnumBegAddresses,  
   out IEnumDebugAddresses ppEnumEndAddresses  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pDocContext`  
 [in] Kontekst dokumentu.  
  
 `fStatmentOnly`  
 [in] W przypadku opcji TRUE ogranicza adresy debugowania do pojedynczej instrukcji.  
  
 `ppEnumBegAddresses`  
 [out] Zwraca moduł wyliczający dla wyjścia adresów debugowania skojarzone z tym instrukcja lub wiersza.  
  
 `ppEnumEndAddresses`  
 [out] Zwraca [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md) modułu wyliczającego dla końcowy adresów debugowania skojarzone z tym instrukcja lub wiersza.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Kontekst dokumentu zazwyczaj wskazuje zakres wierszy źródłowych. Ta metoda zapewnia początkowy i końcowy adres debugowania powiązanych z tymi wierszami. W niektórych językach umożliwiają instrukcji, które rozciągają się wiele wierszy lub wiersze, które zawiera więcej niż jedną instrukcję. Ta metoda zapewnia flagi, aby ograniczyć adresy debugowania do pojedynczej instrukcji.  
  
 Istnieje możliwość dla pojedynczej instrukcji wielu adresów debugowania, tak jak w przypadku szablonów.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)   
 [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)

