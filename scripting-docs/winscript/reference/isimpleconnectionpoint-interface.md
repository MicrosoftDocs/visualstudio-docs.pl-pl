---
title: Interfejs ISimpleConnectionPoint | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ISimpleConnectionPoint interface
ms.assetid: f632a82f-942d-4291-963e-e9fa2b162493
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0d18c8f9eef6ddb1a38473eb19984bd9cf7dbd96
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63001503"
---
# <a name="isimpleconnectionpoint-interface"></a>Interfejs ISimpleConnectionPoint
Zapewnia prostą metodę do opisu i wyliczania zdarzenia wywoływane w punkcie określonym połączeniu. Ten interfejs ułatwia także zaczepić `IDispatch` obiektu tych zdarzeń. Ten interfejs jest implementowany przez proces debugowania Menedżera (menedżerów PDM) i używane przez aparatów skryptów.  
  
 Ten interfejs jest dostępny z `IDebugHelper::CreateSimpleConnectionPoint`.  
  
 Oprócz metod odziedziczone `IUnknown`, `ISimpleConnectionPoint` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
  
|Metoda|Opis|  
|------------|-----------------|  
|[ISimpleConnectionPoint::Advise](../../winscript/reference/isimpleconnectionpoint-advise.md)|Ustanawia połączenie między obiektu punktu połączenia proste a zbiornikiem klienta.|  
|[ISimpleConnectionPoint::DescribeEvents](../../winscript/reference/isimpleconnectionpoint-describeevents.md)|Zwraca identyfikator DISPID i nazwę dla każdego zdarzenia w określonym zakresie zdarzeń.|  
|[ISimpleConnectionPoint::GetEventCount](../../winscript/reference/isimpleconnectionpoint-geteventcount.md)|Zwraca liczbę zdarzeń dostępne w tym interfejsie.|  
|[ISimpleConnectionPoint::Unadvise](../../winscript/reference/isimpleconnectionpoint-unadvise.md)|Przerywa połączenie doradztwa technicznego dotyczącego wcześniej ustanowione przez `ISimpleConnectionPoint::Advise`.|  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProperty, interfejs](../../winscript/reference/idebugproperty-interface.md)