---
title: ISimpleConnectionPoint::DescribeEvents | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 1b5824f945ad25f177fc169b58157377bf53bcce
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62786422"
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