---
title: 'IPerPropertyBrowsing2:: GetPredefinedStrings | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IPerPropertyBrowsing2.GetPredefinedStrings
apilocation:
- scrobj.dll
helpviewer_keywords:
- IPerPropertyBrowsing2::GetPredefinedStrings
ms.assetid: d2fa30f7-a566-4dbd-8b47-ffdc00419771
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 55ade724dd9ee5d59feb9d04c5b525ca839a9cec
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576774"
---
# <a name="iperpropertybrowsing2getpredefinedstrings"></a>IPerPropertyBrowsing2::GetPredefinedStrings
Umożliwia obiektowi wywołującemu Wypełnienie pola listy z zliczoną tablicą wskaźników ciągu reprezentujących potencjalne wartości tej właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetPredefinedStrings(  
   DISPID  dispid,  
   CALPOLESTR*  pCaStrings,  
   CADWORD*  pCaCookies  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dispid`  
 podczas Identyfikator wysyłania właściwości, dla której obiekt wywołujący żąda listy ciągów.  
  
 `pCaStrings`  
 określoną Wskaźnik do rozliczanej struktury obiektu wywołującego, która zawiera liczbę elementów i adres tablicy wskaźników ciągu. Jeśli metoda nie powiedzie się, nie przydzielono żadnej pamięci i zawartość struktury jest niezdefiniowana.  
  
 `pCaCookies`  
 określoną Wskaźnik do rozliczanej struktury obiektu wywołującego, która zawiera liczbę elementów i adres tablicy typu DWORD przydzieloną metodę. Jeśli metoda nie powiedzie się, nie przydzielono żadnej pamięci i zawartość struktury jest niezdefiniowana.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca prawidłowy `HRESULT`, zazwyczaj `S_OK`.  
  
## <a name="see-also"></a>Zobacz także  
 [IPerPropertyBrowsing2, interfejs 1](../../winscript/reference/iperpropertybrowsing2-interface-1.md)