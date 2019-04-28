---
title: IApplicationDebuggerUI::BringDocumentToTop | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IApplicationDebuggerUI.BringDocumentToTop
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebuggerUI::BringDocumentToTop
ms.assetid: ef5fe1e7-4381-4409-a0d7-58f993abe84e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a8a88b44f609113670259492eb82491b16004d29
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62991123"
---
# <a name="iapplicationdebuggeruibringdocumenttotop"></a>IApplicationDebuggerUI::BringDocumentToTop
Przesuwa okno zawiera dokument określonego debugowania do góry w debugerze interfejsu użytkownika.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT BringDocumentToTop(  
   IDebugDocumentText*  pddt  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pddt`  
 [in] Debuguj dokument, aby przenieść do góry w interfejsie użytkownika debugera.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
|`E_INVALIDARG`|Dokument nie jest znany.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda powoduje wyświetlenie okna zawiera dokument określonego debugowania do góry w debugerze interfejsu użytkownika.  
  
## <a name="see-also"></a>Zobacz też  
 [IApplicationDebuggerUI, interfejs](../../winscript/reference/iapplicationdebuggerui-interface.md)