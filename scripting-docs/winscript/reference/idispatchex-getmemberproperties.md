---
title: 'IDispatchEx:: GetMemberProperties | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 488f8790ec25532fb611f18e8b24e7e7dba2e2f4
ms.sourcegitcommit: d281d2a04a5bc302650eebf369946d8f101e59dd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/12/2020
ms.locfileid: "88144553"
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
 Określa element członkowski. Używa `GetDispID` lub `GetNextDispID` do uzyskania identyfikatora wysyłania.  
  
 `grfdexFetch`  
 Określa, które właściwości mają być pobierane. Może to być kombinacja wartości wymienionych poniżej `pgrfdex` i/lub kombinacji następujących wartości:  
  
|Wartość|Znaczenie|  
|-----------|-------------|  
|grfdexPropCanAll|Łączy fdexPropCanGet, fdexPropCanPut, fdexPropCanPutRef, fdexPropCanCall, fdexPropCanConstruct i fdexPropCanSourceEvents.|  
|grfdexPropCannotAll|Łączy fdexPropCannotGet, fdexPropCannotPut, fdexPropCannotPutRef, fdexPropCannotCall, fdexPropCannotConstruct i fdexPropCannotSourceEvents.|  
|grfdexPropExtraAll|Łączy fdexPropNoSideEffects i fdexPropDynamicType.|  
|grfdexPropAll|Łączy grfdexPropCanAll, grfdexPropCannotAll i grfdexPropExtraAll.|  
  
 `pgrfdex`  
 Adres `DWORD` , który odbiera żądane właściwości. Może to być kombinacja następujących wartości:  
  
|Wartość|Znaczenie|  
|-----------|-------------|  
|fdexPropCanGet|Element członkowski można uzyskać przy użyciu DISPATCH_PROPERTYGET.|  
|fdexPropCannotGet|Nie można uzyskać elementu członkowskiego przy użyciu DISPATCH_PROPERTYGET.|  
|fdexPropCanPut|Element członkowski można ustawić przy użyciu DISPATCH_PROPERTYPUT.|  
|fdexPropCannotPut|Nie można ustawić elementu członkowskiego przy użyciu DISPATCH_PROPERTYPUT.|  
|fdexPropCanPutRef|Element członkowski można ustawić przy użyciu DISPATCH_PROPERTYPUTREF.|  
|fdexPropCannotPutRef|Nie można ustawić elementu członkowskiego przy użyciu DISPATCH_PROPERTYPUTREF.|  
|fdexPropNoSideEffects|Element członkowski nie ma żadnych efektów ubocznych. Na przykład debuger może bezpiecznie pobrać/ustawić/wywołać tego elementu członkowskiego bez zmiany stanu debugowanego skryptu.|  
|fdexPropDynamicType|Element członkowski jest dynamiczny i może ulec zmianie w okresie istnienia obiektu.|  
|fdexPropCanCall|Element członkowski może być wywoływany jako metoda przy użyciu DISPATCH_METHOD.|  
|fdexPropCannotCall|Nie można wywołać elementu członkowskiego jako metody przy użyciu DISPATCH_METHOD.|  
|fdexPropCanConstruct|Element członkowski może być wywoływany jako Konstruktor przy użyciu DISPATCH_CONSTRUCT.|  
|fdexPropCannotConstruct|Nie można wywołać elementu członkowskiego jako konstruktora przy użyciu DISPATCH_CONSTRUCT.|  
|fdexPropCanSourceEvents|Element członkowski może uruchamiać zdarzenia.|  
|fdexPropCannotSourceEvents|Składowa nie może wyzwalać zdarzeń.|  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca jedną z następujących wartości:  
  
|Wartość|Znaczenie|
|-|-|  
|`S_OK`|Powodzenie.|  
|`DISP_E_UNKNOWNNAME`|Nazwa jest nieznana.|  
  
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
  
## <a name="see-also"></a>Zobacz także  
 [IDispatchEx, interfejs](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx:: getdispid](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)