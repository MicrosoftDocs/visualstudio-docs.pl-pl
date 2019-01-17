---
title: IPerPropertyBrowsing2, interfejs 1 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IPerPropertyBrowsing2
apilocation:
- scrobj.dll
helpviewer_keywords:
- IPerPropertyBrowsing2 interface
ms.assetid: 1e50b3f7-cc1c-495a-93c7-3ee03aea0b8a
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bded7159b72fc8c1ae8408611ce858105e6734da
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54344040"
---
# <a name="iperpropertybrowsing2-interface-1"></a>IPerPropertyBrowsing2, interfejs 1
Uzyskuje dostęp do informacji na stronach właściwości oferowana przez obiekt.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
  
|Metoda|Opis|  
|------------|-----------------|  
|`GetDisplayString`|Zwraca ciąg tekst opisujący określonej właściwości.|  
|`MapPropertyToPage`|Zwraca identyfikator CLSID strony właściwości, który umożliwia manipulowanie określonej właściwości.|  
|`GetPredefinedStrings`|Zwraca zliczono tablicę ciągów (`LPOLESTR` wskaźniki) lista Opisy dopuszczalnych wartości, które może zaakceptować określoną właściwość.|  
|`SetPredefinedValue`|Ustawia wartość właściwości wstępnie zdefiniowaną wartość identyfikowane za pomocą tokenu `dwCookie.`|  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: dbgprop.h