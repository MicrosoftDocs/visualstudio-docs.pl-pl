---
title: 'IDebugDocumentHost:: OnCreateDocumentContext | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHost.OnCreateDocumentContext
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentHost::OnCreateDocumentContext
ms.assetid: 080c8604-cfd7-484e-a337-15040870e683
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3fdfa64f66288cba47dec7c498db15238e55f954
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72569111"
---
# <a name="idebugdocumenthostoncreatedocumentcontext"></a>IDebugDocumentHost::OnCreateDocumentContext
Powiadamia hosta o tworzeniu nowego kontekstu dokumentu i umożliwia hostowi opcjonalne zwrócenie kontroli nieznanej dla nowego kontekstu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT OnCreateDocumentContext(  
   IUnknown**  ppunkOuter  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppunkOuter`  
 określoną Obiekt, który steruje nowym kontekstem.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
|`E_NOTIMPL`|Host nie udostępnia obiektu sterującego.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda umożliwia hostowi Dodawanie nowych funkcji do kontekstów dokumentu dostarczonych przez pomocnika. Ta metoda może zwrócić **E_NOTIMPL** lub pusty obiekt zewnętrzny, w takim przypadku wywołujący jest odpowiedzialny za tworzenie kontekstu.  
  
## <a name="see-also"></a>Zobacz także  
 [IDebugDocumentHost, interfejs](../../winscript/reference/idebugdocumenthost-interface.md)