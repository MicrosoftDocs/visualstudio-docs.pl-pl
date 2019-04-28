---
title: IDispatchEx::DeleteMemberByName | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: dc7c8db4ab28e0bd0fcb48f352cb07595f72fd17
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63000889"
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
 Nazwa członka do usunięcia.  
  
 `grfdex`  
 Określa, czy nazwa elementu członkowskiego z uwzględnieniem wielkości liter. Może to być jeden z następujących wartości:  
  
|Wartość|Znaczenie|  
|-----------|-------------|  
|fdexNameCaseSensitive|Żądania, które odbywać wyszukiwanie nazw uwzględnianiem wielkości liter. Można zignorować przez obiekt, który nie obsługuje wyszukiwania z uwzględnieniem wielkości liter.|  
|fdexNameCaseInsensitive|Żądania, które wyszukiwanie nazw odbywać się bez uwzględniania wielkości liter. Można zignorować przez obiekt, który nie obsługuje wyszukiwanie bez uwzględniania wielkości liter.|  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca jedną z następujących wartości:  
  
|||  
|-|-|  
|`S_OK`|Powodzenie.|  
|`S_FALSE`|Element członkowski istnieje, ale nie można jej usunąć.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli element członkowski zostanie usunięty, identyfikator DISPID musi są ważne `GetNextDispID`.  
  
 Jeśli element członkowski o określonej nazwie zostanie usunięty, a później zostaje odtworzone element członkowski o takiej samej nazwie, DISPID powinna być taka sama. (Czy elementy członkowskie, które różnią się tylko wielkością liter są "takie same" jest zależny od obiektu).  
  
## <a name="example"></a>Przykład  
  
```cpp
BSTR bstrName;  
IDispatchEx *pdex;  
  
// Assign to pdex and bstrName  
pdex->DeleteMemberByName(bstrName, fdexNameCaseSensitive);  
```  
  
## <a name="see-also"></a>Zobacz też  
 [IDispatchEx, interfejs](../../winscript/reference/idispatchex-interface.md)