---
title: IDebugHelper::CreatePropertyBrowserEx | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 01e63d1588fd1e25f3415f22450ed5145752d711
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62979204"
---
# <a name="idebughelpercreatepropertybrowserex"></a>IDebugHelper::CreatePropertyBrowserEx
Zwraca przeglądarkę właściwości opakowuje Typ VARIANT, która umożliwia niestandardowych konwersję typu VARIANT wartości lub VARTYPE na ciągi.  
  
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
 [in] Wariant głównego do przeglądania.  
  
 `bstrName`  
 [in] Nazwa do nadania katalogu głównego.  
  
 `pdat`  
 [in] Wątek, na którym należy żądać właściwości. Jeśli ten parametr ma wartość NULL, kierowania nie jest wykonywana.  
  
 `pdf`  
 [in] Obiekt, który zawiera niestandardowe formatowanie dla wariantów.  
  
 `ppdob`  
 [out] Przeglądarkę właściwości.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda zwraca przeglądarkę właściwości opakowuje Typ VARIANT, która umożliwia niestandardowych konwersję typu VARIANT wartości lub VARTYPE na ciągi.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugHelper::CreatePropertyBrowser](../../winscript/reference/idebughelper-createpropertybrowser.md)   
 [Interfejs IDebugHelper](../../winscript/reference/idebughelper-interface.md)   
 [IDebugProperty, interfejs](../../winscript/reference/idebugproperty-interface.md)