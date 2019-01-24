---
title: IDebugDisassemblyStream2::GetDocument | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::GetDocument
helpviewer_keywords:
- IDebugDisassemblyStream2::GetDocument
ms.assetid: 3d039a44-ebaa-4413-ac18-7cfd92c408bd
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d71db41646fece07b79389c35cdfaa7402c31438
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54777769"
---
# <a name="idebugdisassemblystream2getdocument"></a>IDebugDisassemblyStream2::GetDocument
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Pobiera dokument źródłowy skojarzony z tym strumienia wejściowego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT GetDocument(   
   BSTR              bstrDocumentUrl,  
   IDebugDocument2** ppDocument  
);  
```  
  
```csharp  
int GetDocument(   
   string              bstrDocumentUrl,  
   out IDebugDocument2 ppDocument  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `bstrDocumentUrl`  
 [in] Adres URL dokumentu.  
  
 `ppDocument`  
 [out] Zwraca [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) obiekt reprezentujący dokument.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest implementowana przez aparaty debugowania, mających dokumenty tekstowe, które nie są przechowywane w rzeczywisty plik.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
