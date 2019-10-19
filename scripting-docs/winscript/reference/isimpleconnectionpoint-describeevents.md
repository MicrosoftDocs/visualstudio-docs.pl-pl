---
title: ISimpleConnectionPoint::D escribeEvents | Microsoft Docs
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
ms.openlocfilehash: b5000689d588fe3f63ec5408893187bba8d13d63
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571823"
---
# <a name="isimpleconnectionpointdescribeevents"></a>ISimpleConnectionPoint::DescribeEvents
Zwraca identyfikator DISPID i nazwę każdego zdarzenia w określonym zakresie zdarzeń.  
  
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
 podczas Indeks pierwszego zdarzenia do pobrania.  
  
 `cEvents`  
 podczas Liczba zdarzeń do pobrania.  
  
 `prgid`  
 określoną Tablica wartości DISPID zdarzenia.  
  
 `prgbstr`  
 określoną Tablica nazw zdarzeń.  
  
 `pcEventsFetched`  
 określoną Rzeczywista liczba pobranych zdarzeń.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
|`S_FALSE`|Zażądano więcej zdarzeń niż było dostępne. Niedostępne zdarzenia są reprezentowane za pomocą DISPID_NULL i typu BSTR o wartości null.|  
|`E_INVALIDARG`|Nie można pobrać żadnych elementów.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda zwraca identyfikator DISPID i nazwę każdego zdarzenia w określonym zakresie zdarzeń.  
  
## <a name="see-also"></a>Zobacz także  
 [ISimpleConnectionPoint, interfejs](../../winscript/reference/isimpleconnectionpoint-interface.md)