---
title: IDispatchEx::GetDispID | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: c466ec767be53d100b970314bf0d81d5dd9dfb20
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097542"
---
# <a name="idispatchexgetdispid"></a>IDispatchEx::GetDispID
Mapuje nazwę na jeden element członkowski jego odpowiedni identyfikator DISPID, które następnie mogą być używane w kolejnych wywołaniach `IDispatchEx::InvokeEx`.  
  
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
 Przekazana nazwa mają być mapowane.  
  
 `grfdex`  
 Określa opcje do uzyskania identyfikatora elementu członkowskiego. Może to być kombinacją następujących wartości:  
  
|Wartość|Znaczenie|  
|-----------|-------------|  
|fdexNameCaseSensitive|Żądania, które odbywać wyszukiwanie nazw uwzględnianiem wielkości liter. Można zignorować przez obiekt, który nie obsługuje wyszukiwania z uwzględnieniem wielkości liter.|  
|fdexNameEnsure|Żądania, że utworzony elementu członkowskiego, jeśli jeszcze nie istnieje. Należy utworzyć nowy element członkowski o wartości `VT_EMPTY`.|  
|fdexNameImplicit|Wskazuje, że obiekt wywołujący wyszukuje obiekty składową o określonej nazwie kiedy podstawowego obiektu nie jest jawnie określona.|  
|fdexNameCaseInsensitive|Żądania, które wyszukiwanie nazw odbywać się bez uwzględniania wielkości liter. Może być ignorowane przez obiekt, który nie obsługuje wyszukiwanie bez uwzględniania wielkości liter.|  
  
 `pid`  
 Wskaźnik do przydzielonej przez obiekt wywołujący lokalizacji, aby otrzymać identyfikator DISPID wynik. Jeśli wystąpi błąd, `pid` zawiera DISPID_UNKNOWN.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca jedną z następujących wartości:  
  
|||  
|-|-|  
|`S_OK`|Powodzenie.|  
|`E_OUTOFMEMORY`|Za mało pamięci.|  
|`DISP_E_UNKNOWNNAME`|Nazwa nie jest znane.|  
  
## <a name="remarks"></a>Uwagi  
 `GetDispID` można użyć zamiast `GetIDsOfNames` uzyskać identyfikator DISPID dla danego elementu członkowskiego.  
  
 Ponieważ `IDispatchEx` zezwala na dodawanie i usuwanie elementów członkowskich, zbiór dispid nie pozostaje niezmienna przez okres istnienia obiektu.  
  
 Nieużywane `riid` parametru w `IDispatch::GetIDsOfNames` został usunięty.  
  
## <a name="example"></a>Przykład  
  
```cpp
BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;   
  
   // Assign to pdex and bstrName  
   pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid);  
   // Use dispid  
```  
  
## <a name="see-also"></a>Zobacz też  
 [IDispatchEx, interfejs](../../winscript/reference/idispatchex-interface.md)