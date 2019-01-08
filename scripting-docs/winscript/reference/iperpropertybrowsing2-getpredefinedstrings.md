---
title: IPerPropertyBrowsing2::GetPredefinedStrings | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 3bec9643a89d40a7b1e37d019d4211bd7167ee65
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088611"
---
# <a name="iperpropertybrowsing2getpredefinedstrings"></a>IPerPropertyBrowsing2::GetPredefinedStrings
Umożliwia obiektowi wywołującemu wypełnić pole listy zliczono tablicę wskaźników ciągu, które reprezentują potencjalnych wartości dla tej właściwości.  
  
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
 [in] Wyślij identyfikator właściwości, dla którego obiekt wywołujący żąda listy parametrów.  
  
 `pCaStrings`  
 [out] Wskaźnik do struktury przydzielonej przez obiekt wywołujący, zliczono tablicy, która zawiera liczba elementów i adres przydzielony Metoda tablicy wskaźników ciągu. Jeśli metoda nie powiedzie się, nie pamięć została przydzielona, i zawartość struktury są niezdefiniowane.  
  
 `pCaCookies`  
 [out] Wskaźnik do przydzielonej przez obiekt wywołujący, liczone strukturę tablicy, która zawiera liczba elementów i adres przydzielony metoda Tablica słów podwójnych. Jeśli metoda nie powiedzie się, nie pamięć została przydzielona, i zawartość struktury są niezdefiniowane.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca prawidłową `HRESULT`, zazwyczaj `S_OK`.  
  
## <a name="see-also"></a>Zobacz też  
 [IPerPropertyBrowsing2, interfejs 1](../../winscript/reference/iperpropertybrowsing2-interface-1.md)