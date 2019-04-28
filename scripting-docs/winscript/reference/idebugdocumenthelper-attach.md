---
title: IDebugDocumentHelper::Attach | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.Attach
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::Attach
ms.assetid: 834f23a9-716d-44df-b23c-d1bf6da60e79
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8f4fbd1686d27e594b748ca97c82c645de1b93de
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62783138"
---
# <a name="idebugdocumenthelperattach"></a>IDebugDocumentHelper::Attach
Dodaje ten dokument w drzewie dokumentu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT Attach(  
   IDebugDocumentHelper*  pddhParent  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pddhParent`  
 [in] W drzewie dokumentu, gdzie ma zostać dodana w tym dokumencie. Może mieć wartości NULL.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Metoda ta umożliwia dodanie tego dokumentu do dokumentu drzewa, za pomocą `pddhParent` jako element nadrzędny. Jeśli `pddhParent` jest `NULL`, w tym dokumencie będzie dokumentów najwyższego poziomu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugDocumentHelper::Detach](../../winscript/reference/idebugdocumenthelper-detach.md)   
 [IDebugDocumentHelper, interfejs](../../winscript/reference/idebugdocumenthelper-interface.md)