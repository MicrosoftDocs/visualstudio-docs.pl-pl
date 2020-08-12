---
title: IDispatchEx::D eleteMemberByDispID | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.DeleteMemberByDispID
apilocation:
- scrobj.dll
helpviewer_keywords:
- DeleteMemberByDispID method
ms.assetid: f61231e5-ba93-4ac3-bde8-d363548356b3
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0c3dbb040e39fd15b77e42b2eaa9fb2cdda0b1b2
ms.sourcegitcommit: d281d2a04a5bc302650eebf369946d8f101e59dd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/12/2020
ms.locfileid: "88144639"
---
# <a name="idispatchexdeletememberbydispid"></a>IDispatchEx::DeleteMemberByDispID
Usuwa element członkowski przez identyfikator DISPID.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT DeleteMemberByDispID(  
    DISPID id  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `id`  
 Identyfikator elementu członkowskiego. Używa `GetDispID` lub `GetNextDispID` do uzyskania identyfikatora wysyłania.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca jedną z następujących wartości:  
  
|Wartość|Znaczenie|
|-|-|  
|`S_OK`|Powodzenie.|  
|`S_FALSE`|Element członkowski istnieje, ale nie można go usunąć.|  
  
## <a name="remarks"></a>Uwagi  
 W przypadku usunięcia elementu członkowskiego DISPID musi pozostać prawidłowy dla `GetNextDispID` .  
  
 Jeśli element członkowski o danej nazwie zostanie usunięty, a później członek o tej samej nazwie zostanie odtworzony, identyfikator DISPID powinien być taki sam. (Czy nazwy elementów członkowskich, które różnią się tylko wielkością liter są "takie same" są zależne od obiektu).  
  
## <a name="example"></a>Przykład  
  
```cpp
BSTR bstrName;  
DISPID dispid;  
IDispatchEx *pdex;   
  
// Assign to pdex and bstrName  
if (SUCCEEDED(pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid)))  
    pdex->DeleteMemberByDispID(dispid);  
```  
  
## <a name="see-also"></a>Zobacz także  
 [IDispatchEx, interfejs](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx:: getdispid](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)