---
title: IDispatchEx::DeleteMemberByDispID | Microsoft Docs
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
ms.openlocfilehash: 36eeeb4c28286bb5712be3908b47a5145e460597
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63000942"
---
# <a name="idispatchexdeletememberbydispid"></a>IDispatchEx::DeleteMemberByDispID
Usuwa członka przez identyfikator DISPID.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT DeleteMemberByDispID(  
    DISPID id  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `id`  
 Identyfikator elementu członkowskiego. Używa `GetDispID` lub `GetNextDispID` można uzyskać identyfikatora wysyłania.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca jedną z następujących wartości:  
  
|||  
|-|-|  
|`S_OK`|Powodzenie.|  
|`S_FALSE`|Element członkowski istnieje, ale nie można jej usunąć.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli element członkowski zostanie usunięty, identyfikator DISPID musi są ważne `GetNextDispID`.  
  
 Jeśli element członkowski o określonej nazwie zostanie usunięty, a później zostaje odtworzone element członkowski o takiej samej nazwie, DISPID powinna być taka sama. (Czy nazwy elementów członkowskich, które różnią się tylko wielkością liter są "takie same" jest zależny od obiektu).  
  
## <a name="example"></a>Przykład  
  
```cpp
BSTR bstrName;  
DISPID dispid;  
IDispatchEx *pdex;   
  
// Assign to pdex and bstrName  
if (SUCCEEDED(pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid)))  
    pdex->DeleteMemberByDispID(dispid);  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDispatchEx](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)