---
title: IDebugDocumentHost::OnCreateDocumentContext | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: c0f8ce73e05fa8dd163564184361254fd58163ee
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54096342"
---
# <a name="idebugdocumenthostoncreatedocumentcontext"></a>IDebugDocumentHost::OnCreateDocumentContext
Powiadamia hosta, że nowy kontekst dokumentu jest tworzona i Zezwalaj hostowi na opcjonalnie zwracać kontrolowanie nieznane w nowym kontekście.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT OnCreateDocumentContext(  
   IUnknown**  ppunkOuter  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppunkOuter`  
 [out] Obiekt, który kontroluje nowy kontekst.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
|`E_NOTIMPL`|Host nie udostępnia obiekt kontroli.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda umożliwia hosta do dodawania nowych funkcji do dokumentów dostarczonych przez pomocnika kontekstów. Ta metoda może zwrócić **E_NOTIMPL** lub zewnętrzny obiekt z wartością null, w którym obiekt wywołujący jest odpowiedzialny za tworzenie kontekstu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugDocumentHost, interfejs](../../winscript/reference/idebugdocumenthost-interface.md)