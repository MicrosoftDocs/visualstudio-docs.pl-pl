---
title: IPerPropertyBrowsing2::MapPropertyToPage | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IPerPropertyBrowsing2.MapPropertyToPage
apilocation:
- scrobj.dll
helpviewer_keywords:
- IPerPropertyBrowsing2::MapPropertyToPage
ms.assetid: e6418a8e-500b-42e1-9b5a-52e6f7567f99
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 77270bbe963f281a43a085cb7d15724b7b2ec14e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62944831"
---
# <a name="iperpropertybrowsing2mappropertytopage"></a>IPerPropertyBrowsing2::MapPropertyToPage
Zwraca identyfikator CLSID strony właściwości, które można edytować tej właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT MapPropertyToPage(  
   DISPID  dispid,  
   CLSID*  pClsidPropPage  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dispid`  
 [in] Wyślij identyfikator właściwości zainteresowania.  
  
 `pClsidPropPage`  
 [out] Wskaźnik do CLSID identyfikowanie na stronie właściwości skojarzony z właściwością. Jeśli ta metoda nie powiedzie się, *`pClsidPropPage` jest ustawiona na CLSID_NULL.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca prawidłową `HRESULT`, zazwyczaj `S_OK`.  
  
## <a name="see-also"></a>Zobacz też  
 [IPerPropertyBrowsing2, interfejs 1](../../winscript/reference/iperpropertybrowsing2-interface-1.md)