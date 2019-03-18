---
title: IPerPropertyBrowsing2, interfejs 1 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 156cf9a1e104b8a2d7ffe4e48bd39642ef1abbd0
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58159585"
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