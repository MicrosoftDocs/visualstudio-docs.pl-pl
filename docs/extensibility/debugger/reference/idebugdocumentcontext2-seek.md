---
title: IDebugDocumentContext2::Seek | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugDocumentContext2::Seek
helpviewer_keywords:
- IDebugDocumentContext2::Seek
ms.assetid: 71501356-8a82-4d36-b354-6625bdd2baa0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: db5c44d79882d887e8a852f3add491317dbf96fa
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53895528"
---
# <a name="idebugdocumentcontext2seek"></a>IDebugDocumentContext2::Seek
Przenosi kontekstu dokumentu o podanej liczbie wierszy lub instrukcji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Seek(   
   int                      nCount,  
   IDebugDocumentContext2** ppDocContext  
);  
```  
  
```cpp  
int Seek(   
   int                        nCount,  
   out IDebugDocumentContext2 ppDocContext  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `nCount`  
 [in] Liczba instrukcji lub wiersze, aby przenieść w górę, w zależności od kontekstu dokumentu.  
  
 `ppDocContext`  
 [out] Zwraca nowy [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) obiektu za pomocą nowej pozycji.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)