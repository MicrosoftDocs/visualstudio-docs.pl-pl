---
title: IDispatchEx::D eleteMemberByName | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.DeleteMemberByName
apilocation:
- scrobj.dll
helpviewer_keywords:
- DeleteMemberByName method
ms.assetid: a01b4e6a-d989-4b29-bb3f-04554f8c39f7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cf62972b192d73bd130d15066d79ea70fe24beb8
ms.sourcegitcommit: d281d2a04a5bc302650eebf369946d8f101e59dd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/12/2020
ms.locfileid: "88144600"
---
# <a name="idispatchexdeletememberbyname"></a>IDispatchEx::DeleteMemberByName
Usuwa element członkowski według nazwy.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT DeleteMemberByName(  
   BSTR bstrName,  
   DWORD grfdex  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `bstrName`  
 Nazwa elementu członkowskiego, który ma zostać usunięty.  
  
 `grfdex`  
 Określa, czy w nazwie elementu członkowskiego jest uwzględniana wielkość liter. To ustawienie może zwracać jedną z następujących wartości:  
  
|Wartość|Znaczenie|  
|-----------|-------------|  
|fdexNameCaseSensitive|Żądania wyszukania nazwy są wykonywane w sposób uwzględniający wielkość liter. Może być ignorowany przez obiekt, który nie obsługuje wyszukiwania z rozróżnianiem wielkości liter.|  
|fdexNameCaseInsensitive|Żądania wyszukania nazwy są wykonywane w sposób niezależny od wielkości liter. Może być ignorowany przez obiekt, który nie obsługuje wyszukiwania bez uwzględniania wielkości liter.|  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca jedną z następujących wartości:  
  
|Wartość|Znaczenie|
|-|-|  
|`S_OK`|Powodzenie.|  
|`S_FALSE`|Element członkowski istnieje, ale nie można go usunąć.|  
  
## <a name="remarks"></a>Uwagi  
 W przypadku usunięcia elementu członkowskiego DISPID musi pozostać prawidłowy dla `GetNextDispID` .  
  
 Jeśli element członkowski o danej nazwie zostanie usunięty, a później członek o tej samej nazwie zostanie odtworzony, identyfikator DISPID powinien być taki sam. (Czy elementy członkowskie, które różnią się tylko wielkością liter są "takie same", są zależne od obiektu).  
  
## <a name="example"></a>Przykład  
  
```cpp
BSTR bstrName;  
IDispatchEx *pdex;  
  
// Assign to pdex and bstrName  
pdex->DeleteMemberByName(bstrName, fdexNameCaseSensitive);  
```  
  
## <a name="see-also"></a>Zobacz także  
 [IDispatchEx, interfejs](../../winscript/reference/idispatchex-interface.md)