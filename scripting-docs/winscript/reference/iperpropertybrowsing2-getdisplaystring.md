---
title: 'IPerPropertyBrowsing2:: GetDisplayString | Microsoft Docs'
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
ms.openlocfilehash: bc702ad15d1aba04bf991c04b585728afde4fb41
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571449"
---
# <a name="iperpropertybrowsing2getdisplaystring"></a>IPerPropertyBrowsing2::GetDisplayString
Pobiera ciąg do typów wyświetlanych, które nie są w sposób niewidoczny, zwracany tekst jest nazwą opisującą Właściwość i może być wyświetlany w interfejsie użytkownika obiektu wywołującego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetDisplayString(  
   DISPID  dispid,  
   BSTR*  pBstr  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dispid`  
 podczas Identyfikator wysyłania właściwości, której żądano nazwa wyświetlana.  
  
 `pBstr`  
 określoną Wskaźnik do `BSTR` zawierający nazwę wyświetlaną dla właściwości identyfikowanej przez `dispID`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca prawidłowy `HRESULT`, zazwyczaj `S_OK`.  
  
## <a name="remarks"></a>Uwagi  
 Zwrócony ciąg nie jest dozwoloną wartością właściwości. Jest to tylko ciąg wyświetlania właściwości.  
  
## <a name="see-also"></a>Zobacz także  
 [IPerPropertyBrowsing2, interfejs 1](../../winscript/reference/iperpropertybrowsing2-interface-1.md)