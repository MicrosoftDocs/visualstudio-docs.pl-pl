---
title: Interfejs ISimpleConnectionPoint | Microsoft Docs
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
ms.openlocfilehash: 549d7f38b01937f992b240cb6f1d651bc848236c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571790"
---
# <a name="isimpleconnectionpoint-interface"></a>Interfejs ISimpleConnectionPoint
Zapewnia prosty sposób opisywania i wyliczania zdarzeń wyzwalanych w określonym punkcie połączenia. Ten interfejs ułatwia również podłączenie `IDispatch` obiektu do tych zdarzeń. Ten interfejs jest implementowany przez Menedżera debugowania procesów (PDM) i zużywany przez aparaty skryptów.  
  
 Ten interfejs jest dostępny w `IDebugHelper::CreateSimpleConnectionPoint`.  
  
 Oprócz metod dziedziczonych z `IUnknown` interfejs `ISimpleConnectionPoint` udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych  
  
|Metoda|Opis|  
|------------|-----------------|  
|[ISimpleConnectionPoint::Advise](../../winscript/reference/isimpleconnectionpoint-advise.md)|Ustanawia połączenie między obiektem prostego punktu połączenia i ujściam klienta.|  
|[ISimpleConnectionPoint::DescribeEvents](../../winscript/reference/isimpleconnectionpoint-describeevents.md)|Zwraca identyfikator DISPID i nazwę każdego zdarzenia w określonym zakresie zdarzeń.|  
|[ISimpleConnectionPoint::GetEventCount](../../winscript/reference/isimpleconnectionpoint-geteventcount.md)|Zwraca liczbę zdarzeń uwidocznionych w tym interfejsie.|  
|[ISimpleConnectionPoint::Unadvise](../../winscript/reference/isimpleconnectionpoint-unadvise.md)|Kończy połączenie doradcze utworzone wcześniej za `ISimpleConnectionPoint::Advise`.|  
  
## <a name="see-also"></a>Zobacz także  
 [IDebugProperty, interfejs](../../winscript/reference/idebugproperty-interface.md)