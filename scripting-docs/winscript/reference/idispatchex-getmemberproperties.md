---
title: IDispatchEx::GetMemberProperties | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.GetMemberProperties
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetMemberProperties method
ms.assetid: 20d43209-12e2-472a-9bf3-81eced137b71
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 51e01ef3fa6d5e0611875f6402b79e53f8c83cac
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088195"
---
# <a name="idispatchexgetmemberproperties"></a>IDispatchEx::GetMemberProperties
Pobiera właściwości elementu członkowskiego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetMemberProperties(  
   DISPID id,  
   DWORD grfdexFetch,  
   DWORD *pgrfdex  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `id`  
 Określa element członkowski. Używa `GetDispID` lub `GetNextDispID` można uzyskać identyfikatora wysyłania.  
  
 `grfdexFetch`  
 Określa właściwości, które można pobrać. Może to być kombinacją wartości na liście `pgrfdex` i/lub kombinacją następujących wartości:  
  
|Wartość|Znaczenie|  
|-----------|-------------|  
|grfdexPropCanAll|Łączy fdexPropCanGet, fdexPropCanPut, fdexPropCanPutRef, fdexPropCanCall fdexPropCanConstruct i fdexPropCanSourceEvents.|  
|grfdexPropCannotAll|Łączy fdexPropCannotGet, fdexPropCannotPut, fdexPropCannotPutRef, fdexPropCannotCall fdexPropCannotConstruct i fdexPropCannotSourceEvents.|  
|grfdexPropExtraAll|Łączy fdexPropNoSideEffects i fdexPropDynamicType.|  
|grfdexPropAll|Łączy w sobie grfdexPropCanAll grfdexPropCannotAll i grfdexPropExtraAll.|  
  
 `pgrfdex`  
 Adres `DWORD` odbierająca żądanej właściwości. Może to być kombinacją następujących wartości:  
  
|Wartość|Znaczenie|  
|-----------|-------------|  
|fdexPropCanGet|Element członkowski można uzyskać za pomocą DISPATCH_PROPERTYGET.|  
|fdexPropCannotGet|Element członkowski nie można uzyskać za pomocą DISPATCH_PROPERTYGET.|  
|fdexPropCanPut|Element członkowski można ustawić za pomocą DISPATCH_PROPERTYPUT.|  
|fdexPropCannotPut|Element członkowski nie można ustawić za pomocą DISPATCH_PROPERTYPUT.|  
|fdexPropCanPutRef|Element członkowski można ustawić za pomocą DISPATCH_PROPERTYPUTREF.|  
|fdexPropCannotPutRef|Element członkowski nie można ustawić za pomocą DISPATCH_PROPERTYPUTREF.|  
|fdexPropNoSideEffects|Element członkowski nie ma żadnych efektów ubocznych. Na przykład, debuger może bezpiecznie get/set/wywołanie tego elementu członkowskiego, bez zmiany stanu skryptu debugowane.|  
|fdexPropDynamicType|Element członkowski jest elementem dynamicznym i zmieniać w okresie istnienia obiektu.|  
|fdexPropCanCall|Element członkowski może zostać wywołana jako metody przy użyciu DISPATCH_METHOD.|  
|fdexPropCannotCall|Element członkowski nie można wywołać jako metodę, przy użyciu DISPATCH_METHOD.|  
|fdexPropCanConstruct|Element członkowski może zostać wywołana jako Konstruktor przy użyciu DISPATCH_CONSTRUCT.|  
|fdexPropCannotConstruct|Nie można wywołać elementu członkowskiego jako Konstruktor przy użyciu DISPATCH_CONSTRUCT.|  
|fdexPropCanSourceEvents|Element członkowski może wyzwalać zdarzeń.|  
|fdexPropCannotSourceEvents|Element członkowski nie może wyzwalać zdarzeń.|  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca jedną z następujących wartości:  
  
|||  
|-|-|  
|`S_OK`|Powodzenie.|  
|`DISP_E_UNKNOWNNAME`|Nazwa nie jest znane.|  
  
## <a name="example"></a>Przykład  
  
```cpp
BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;   
   DWORD dwProps;  
  
   // Assign to pdex and bstrName  
   if (SUCCEEDED(pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid)) &&  
      SUCCEEDED(pdex->GetMemberProperties(dispid, grfdexPropAll, &dwProps)) &&  
         (dwProps & fdexPropCanPut))  
   {  
      // Assign to member  
   }  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDispatchEx](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)