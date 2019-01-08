---
title: IDispatchEx::DeleteMemberByName | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 1866b5135d2c98ccacb34c2c776c69dd7d25db3f
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54096437"
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