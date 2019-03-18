---
title: IDispatchEx::GetNextDispID | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.GetNextDispID
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetNextDispID method
ms.assetid: 8263d441-85ee-47f4-bdba-fbf2ad07e85f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 51a47a7d777d4abc54e8acc2ad0b1d4ef4b7a20b
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58159429"
---
# <a name="idispatchexgetnextdispid"></a>IDispatchEx::GetNextDispID
Wylicza elementy członkowskie obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetNextDispID(  
   DWORD grfdex,  
   DISPID id,  
   DISPID *pid  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `grfdex`  
 Określa zbiór elementów, które mają być wyliczane. Może to być kombinacją następujących wartości:  
  
|Wartość|Znaczenie|  
|-----------|-------------|  
|fdexEnumDefault|Żądania, że obiekt wylicza domyślne elementy. Obiekt może wyliczyć dowolny zbiór elementów.|  
|fdexEnumAll|Żądania obiektu wylicza wszystkie elementy. Obiekt może wyliczyć dowolny zbiór elementów.|  
  
 `id`  
 Identyfikuje bieżącego elementu członkowskiego. GetNextDispID pobiera element w wyliczeniu po niej. Używa GetDispID lub poprzednie wywołanie GetNextDispID w celu uzyskania tego identyfikatora. Używa wartości DISPID_STARTENUM, aby uzyskać pierwszy identyfikator pierwszego elementu.  
  
 `pid`  
 Adres zmiennej DISPID, która odbiera identyfikator następnej pozycji w wyliczeniu.  
  
 Jeśli członek zostanie usunięty przez `DeleteMemberByName` lub `DeleteMemberByDispID`, `DISPID` powinna być prawidłowa dla `GetNextDispID`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca jedną z następujących wartości:  
  
|||  
|-|-|  
|`S_OK`|Powodzenie.|  
|`S_FALSE`|Wyliczenie jest wykonywane.|  
  
## <a name="example"></a>Przykład  
  
```cpp
HRESULT hr;  
   BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;  
  
   // Assign to pdex  
   hr = pdex->GetNextDispID(fdexEnumAll, DISPID_STARTENUM, &dispid);  
   while (hr == NOERROR)  
   {  
      hr = pdex->GetMemberName(dispid, &bstrName);  
      if (!wcscmp(bstrName, OLESTR("Bar")))  
      {  
         SysFreeString(bstrName);  
         return TRUE;  
      }  
      SysFreeString(bstrName);  
      hr = pdex->GetNextDispID(fdexEnumAll, dispid, &dispid);  
   }  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDispatchEx](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](#lrfidispatchexgetnextdispid)   
 [IDispatchEx::DeleteMemberByName](../../winscript/reference/idispatchex-deletememberbyname.md)   
 [IDispatchEx::DeleteMemberByDispID](../../winscript/reference/idispatchex-deletememberbydispid.md)