---
title: 'IDebugHelper:: CreatePropertyBrowser | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugHelper.CreatePropertyBrowser
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugHelper::CreatePropertyBrowser
ms.assetid: 2fa819cf-c7f7-4bd7-b018-ea33b804ba8f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 99aa03470b49d02ee9f0ac1548bd1f8e27d0ab34
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72562503"
---
# <a name="idebughelpercreatepropertybrowser"></a>IDebugHelper::CreatePropertyBrowser
Zwraca przeglądarkę właściwości, która otacza ZMIENNĄ.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT CreatePropertyBrowser(  
   VARIANT*                  pvar,  
   LPCOLESTR                 bstrName,  
   IDebugApplicationThread*  pdat,  
   IDebugProperty**          ppdob  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pvar`  
 podczas Wariant główny do przeglądania.  
  
 `bstrName`  
 podczas Nazwa, aby nadać katalogowi głównemu.  
  
 `pdat`  
 podczas Wątek, w którym należy zażądać właściwości. Jeśli ten parametr ma wartość NULL, kierowanie nie jest wykonywane.  
  
 `ppdob`  
 określoną Przeglądarka właściwości.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda zwraca przeglądarkę właściwości, która otacza ZMIENNĄ.  
  
## <a name="see-also"></a>Zobacz także  
 [IDebugHelper:: CreatePropertyBrowserEx](../../winscript/reference/idebughelper-createpropertybrowserex.md)    
 [IDebugHelper   interfejsu](../../winscript/reference/idebughelper-interface.md)  
 [IDebugProperty, interfejs](../../winscript/reference/idebugproperty-interface.md)