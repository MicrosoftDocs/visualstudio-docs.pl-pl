---
title: 'IScriptScriptlet:: GetSimpleEventName | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptScriptlet. GetSimpleEventName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptScriptlet::GetSimpleEventName
ms.assetid: 012eb555-b26c-4248-bbcc-fc30e6f2b308
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e767c260dcdda2d92a7d90f7fd12af6918ac16d4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62786892"
---
# <a name="iscriptscriptlet-getsimpleeventname"></a>IScriptScriptlet:: GetSimpleEventName
Zwraca nazwę zdarzenia prostego, który jest skojarzony z scriptlet. Jest to nazwa jednowyrazowej, który nie zawiera żadnego odstępu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetSimpleEventName(  
   BSTR               *pbstr  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pbstr`  
 [out] Bufor, który zawiera nazwę zdarzenia prostego, który jest skojarzony z `IScriptScriptlet` obiektu.  
  
## <a name="return-value"></a>Wartość zwracana  
 `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [IScriptScriptlet, interfejs](../../winscript/reference/iscriptscriptlet-interface.md)