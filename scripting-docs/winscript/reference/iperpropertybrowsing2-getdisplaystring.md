---
title: IPerPropertyBrowsing2::GetDisplayString | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IPerPropertyBrowsing2.GetDisplayString
apilocation:
- scrobj.dll
helpviewer_keywords:
- IPerPropertyBrowsing2::GetDisplayString
ms.assetid: 8f75c6a9-86a9-4e2d-8cb4-74e7b1c0a524
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f6f63db8d9c032b8e880f05d4d21e50fd56c74e2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62944871"
---
# <a name="iperpropertybrowsing2getdisplaystring"></a>IPerPropertyBrowsing2::GetDisplayString
Pobiera ciąg, aby wyświetlić typy, które nie są widoczne natury zwracanym tekście jest nazwą właściwości opisujące i mogą być wyświetlane w interfejsie użytkownika wywołującego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetDisplayString(  
   DISPID  dispid,  
   BSTR*  pBstr  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dispid`  
 [in] Wyślij identyfikator właściwości, których nazwa wyświetlana jest wymagane.  
  
 `pBstr`  
 [out] Wskaźnik do `BSTR` zawierający nazwę wyświetlaną dla właściwości identyfikowane przez `dispID`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca prawidłową `HRESULT`, zazwyczaj `S_OK`.  
  
## <a name="remarks"></a>Uwagi  
 Zwracany ciąg nie jest dozwoloną wartością właściwości. Jest po prostu wyświetlanie ciągów właściwości.  
  
## <a name="see-also"></a>Zobacz też  
 [IPerPropertyBrowsing2, interfejs 1](../../winscript/reference/iperpropertybrowsing2-interface-1.md)