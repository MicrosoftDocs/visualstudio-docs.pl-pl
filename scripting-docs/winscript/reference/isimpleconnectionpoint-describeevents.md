---
title: ISimpleConnectionPoint::DescribeEvents | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISimpleConnectionPoint.DescribeEvents
apilocation:
- pdm.dll
helpviewer_keywords:
- ISimpleConnectionPoint::DescribeEvents
ms.assetid: 659ea05f-d41e-424a-bb38-df7672b2d135
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 43a20a2d9580c80bc6aea5d22c6a0713f4843634
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088507"
---
# <a name="isimpleconnectionpointdescribeevents"></a>ISimpleConnectionPoint::DescribeEvents
Zwraca identyfikator DISPID i nazwę dla każdego zdarzenia w określonym zakresie zdarzeń.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT DescribeEvents(  
   ULONG    iEvent,  
   ULONG    cEvents,  
   DISPID*  prgid,  
   BSTR*    prgbstr,  
   ULONG*   pcEventsFetched  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `iEvent`  
 [in] Indeks pierwszego zdarzenia do pobrania.  
  
 `cEvents`  
 [in] Liczba zdarzeń do pobrania.  
  
 `prgid`  
 [out] Tablica wartości identyfikator DISPID zdarzenia.  
  
 `prgbstr`  
 [out] Tablica nazw zdarzeń.  
  
 `pcEventsFetched`  
 [out] Rzeczywista liczba zdarzeń pobrana.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
|`S_FALSE`|Zażądano więcej zdarzeń, nie były dostępne. Niedostępne zdarzenia są reprezentowane z DISPID_NULL i BSTR o wartości null.|  
|`E_INVALIDARG`|Może być pobierane żadne elementy.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda zwraca identyfikator DISPID i nazwę dla każdego zdarzenia w określonym zakresie zdarzeń.  
  
## <a name="see-also"></a>Zobacz też  
 [ISimpleConnectionPoint, interfejs](../../winscript/reference/isimpleconnectionpoint-interface.md)