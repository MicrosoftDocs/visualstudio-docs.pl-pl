---
title: 'IDebugHelper:: CreatePropertyBrowserEx | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugHelper.CreatePropertyBrowserEx
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugHelper::CreatePropertyBrowserEx
ms.assetid: 87ad322f-09da-4ce8-bb68-0b0bbeec645b
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4d64d9dad54e029dc4c76e8b7e6c7a3f0299b0cb
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576498"
---
# <a name="idebughelpercreatepropertybrowserex"></a>IDebugHelper::CreatePropertyBrowserEx
Zwraca przeglądarkę właściwości, która otacza wariant i pozwala na konwersję niestandardową wartości wariantów lub typów VARTYPE na ciągi.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT CreatePropertyBrowserEx(  
   VARIANT*                  pvar,  
   LPCOLESTR                 bstrName,  
   IDebugApplicationThread*  pdat,  
   IDebugFormatter*          pdf,  
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
  
 `pdf`  
 podczas Obiekt, który zapewnia niestandardowe formatowanie dla wariantów.  
  
 `ppdob`  
 określoną Przeglądarka właściwości.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda zwraca przeglądarkę właściwości, która otacza wariant i pozwala na konwersję niestandardową wartości wariantów lub typów VARTYPE na ciągi.  
  
## <a name="see-also"></a>Zobacz także  
 [IDebugHelper:: CreatePropertyBrowser](../../winscript/reference/idebughelper-createpropertybrowser.md)    
 [IDebugHelper   interfejsu](../../winscript/reference/idebughelper-interface.md)  
 [IDebugProperty, interfejs](../../winscript/reference/idebugproperty-interface.md)