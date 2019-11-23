---
title: 'ICanHandleException:: unhandleexception | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ICanHandleException.CanHandleException
apilocation:
- scrobj.dll
helpviewer_keywords:
- ICanHandleException::CanHandleException
ms.assetid: 0fc703bf-9518-487e-af20-00e073b640f1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c536d35dcb9f0faca8b033ecd39aec520a2e260a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575720"
---
# <a name="icanhandleexceptioncanhandleexception"></a>ICanHandleException::CanHandleException
Określa, czy obiekt wywołujący aparatu skryptu może obsłużyć określony wyjątek.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT CanHandleException(  
   EXCEPINFO*  pExcepInfo,  
   VARIANT*    pvar  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pExcepInfo`  
 podczas Wskaźnik do struktury `EXCEPINFO` zawierającej informacje, które zostaną zgłoszone w przypadku braku obsługi wyjątków.  
  
 `pvar`  
 podczas Wartość skojarzona z wyjątkiem, taka jak wartość zwrócona przez instrukcję `throw`. Ten parametr może być `NULL`.  
  
## <a name="return-value"></a>Wartość zwrócona  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Value|Opis|  
|-----------|-----------------|  
|`S_OK`|Obiekt wywołujący może obsłużyć wyjątek|  
|`E_FAIL`|Obiekt wywołujący nie może obsłużyć wyjątku.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli wywołanie `IDispatchEx::InvokeEx`lub podobnej metody, powoduje wyjątek, aparat skryptów sprawdza obiekt wywołujący w łańcuchu wywołującym skryptu, który obsługuje interfejs `ICanHandleException` i wskazuje, że może obsłużyć wyjątek. Jeśli obiekt wywołujący nie może obsłużyć wyjątku, aparat skryptu zostanie zatrzymany.  
  
## <a name="see-also"></a>Zobacz także  
 [ICanHandleException  interfejsu](../../winscript/reference/icanhandleexception-interface.md)  
 [IDispatchEx::InvokeEx](../../winscript/reference/idispatchex-invokeex.md)