---
title: Interfejs ISimpleConnectionPoint | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 4a756fa3f933f4adff56c41a86aee19a0a2a93aa
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54346413"
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