---
title: ICanHandleException::CanHandleException | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 784463f9e465aac005f5454be28a0043069dcb69
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54090002"
---
# <a name="icanhandleexceptioncanhandleexception"></a>ICanHandleException::CanHandleException
Określa, jeśli obiekt wywołujący aparat skryptu może obsłużyć określony wyjątek.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT CanHandleException(  
   EXCEPINFO*  pExcepInfo,  
   VARIANT*    pvar  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pExcepInfo`  
 [in] Wskaźnik do `EXCEPINFO` struktury zawierające informacje, które będą zgłaszane, jeśli zostanie znaleziony żaden moduł obsługi wyjątku.  
  
 `pvar`  
 [in] Wartość skojarzoną z wyjątku, takie jak wartości generowane przez `throw` instrukcji. Ten parametr może być `NULL`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Obiekt wywołujący może obsłużyć wyjątek|  
|`E_FAIL`|Obiekt wywołujący nie może obsłużyć wyjątek.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli wywołanie `IDispatchEx::InvokeEx`, lub podobnej metody, powoduje wyjątek, aparat skryptu wyszukuje obiekt wywołujący w łańcuchu obiekt wywołujący skryptu, który obsługuje `ICanHandleException` interfejs i wskazuje, że może obsługiwać wyjątek. Jeśli wywołujący nie może obsłużyć wyjątek, aparat skryptu zostanie zatrzymany.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs ICanHandleException](../../winscript/reference/icanhandleexception-interface.md)   
 [IDispatchEx::InvokeEx](../../winscript/reference/idispatchex-invokeex.md)