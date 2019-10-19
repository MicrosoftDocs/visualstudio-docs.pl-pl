---
title: 'IDispatchEx:: getdispid | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.GetDispID
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetDispID method
ms.assetid: a288d63d-b08a-4540-9d9d-0bcd182eff9a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 57f0faf6004e2219600f0dbd63749a7e65ca438c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576604"
---
# <a name="idispatchexgetdispid"></a>IDispatchEx::GetDispID
Mapuje pojedynczą nazwę elementu członkowskiego do odpowiadającego mu identyfikatora DISPID, który można następnie użyć podczas kolejnych wywołań do `IDispatchEx::InvokeEx`.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetDispID(  
   BSTR bstrName,  
   DWORD grfdex,  
   DISPID *pid  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `bstrName`  
 Nazwa została przeniesiona do zamapowania.  
  
 `grfdex`  
 Określa opcje uzyskiwania identyfikatora elementu członkowskiego. Może to być kombinacja następujących wartości:  
  
|Wartość|Znaczenie|  
|-----------|-------------|  
|fdexNameCaseSensitive|Żądania wyszukania nazwy są wykonywane w sposób uwzględniający wielkość liter. Może być ignorowany przez obiekt, który nie obsługuje wyszukiwania z uwzględnieniem wielkości liter.|  
|fdexNameEnsure|Żąda utworzenia elementu członkowskiego, jeśli jeszcze nie istnieje. Nowy element członkowski powinien zostać utworzony przy użyciu wartości `VT_EMPTY`.|  
|fdexNameImplicit|Wskazuje, że obiekt wywołujący wyszukuje obiekty dla elementu członkowskiego o określonej nazwie, jeśli obiekt podstawowy nie został jawnie określony.|  
|fdexNameCaseInsensitive|Żądania wyszukania nazwy są wykonywane w sposób niezależny od wielkości liter. Może być ignorowany przez obiekt, który nie obsługuje wyszukiwania bez uwzględniania wielkości liter.|  
  
 `pid`  
 Wskaźnik do lokalizacji przydzielenia przez obiekt wywołujący, aby otrzymać wynik DISPID. Jeśli wystąpi błąd, `pid` zawiera DISPID_UNKNOWN.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca jedną z następujących wartości:  
  
|||  
|-|-|  
|`S_OK`|Prawnego.|  
|`E_OUTOFMEMORY`|Za mało pamięci.|  
|`DISP_E_UNKNOWNNAME`|Nazwa jest nieznana.|  
  
## <a name="remarks"></a>Uwagi  
 `GetDispID` można użyć zamiast `GetIDsOfNames`, aby uzyskać identyfikator DISPID dla danego elementu członkowskiego.  
  
 Ponieważ `IDispatchEx` zezwala na dodawanie i usuwanie elementów członkowskich, zestaw identyfikatorów SPID nie pozostaje stały dla okresu istnienia obiektu.  
  
 Nieużywany parametr `riid` w `IDispatch::GetIDsOfNames` został usunięty.  
  
## <a name="example"></a>Przykład  
  
```cpp
BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;   
  
   // Assign to pdex and bstrName  
   pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid);  
   // Use dispid  
```  
  
## <a name="see-also"></a>Zobacz także  
 [IDispatchEx, interfejs](../../winscript/reference/idispatchex-interface.md)