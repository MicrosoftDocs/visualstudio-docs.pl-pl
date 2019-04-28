---
title: IApplicationDebuggerUI::BringDocumentContextToTop | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IApplicationDebuggerUI.BringDocumentContextToTop
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebuggerUI::BringDocumentContextToTop
ms.assetid: 7844217d-658b-42af-8d10-2714f4eded20
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 596f9357a8553bf6c39140a6948d8ae3085c3210
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62991132"
---
# <a name="iapplicationdebuggeruibringdocumentcontexttotop"></a>IApplicationDebuggerUI::BringDocumentContextToTop
Wywołuje okno zawierające kontekście danego dokumentu do góry w interfejsie użytkownika debugera i przewija okna do kontekstu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT BringDocumentContextToTop(  
   IDebugDocumentContext*  pddc  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pddc`  
 [in] Kontekst dokumentu można przenieść do góry w interfejsie użytkownika debugera.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
|`E_INVALIDARG`|Kontekst określonej przez `pddc` nie jest znany.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda powoduje wyświetlenie okna zawierająca kontekst danego dokumentu do góry w interfejsie użytkownika debugera i przewija okna do kontekstu.  
  
## <a name="see-also"></a>Zobacz też  
 [IApplicationDebuggerUI, interfejs](../../winscript/reference/iapplicationdebuggerui-interface.md)