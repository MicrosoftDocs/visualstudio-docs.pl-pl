---
title: IDebugAsyncOperationCallBack::onComplete | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugAsyncOperationCallBack.onComplete
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugAsyncOperationCallBack::onComplete
ms.assetid: d4023f5a-41f9-4948-b0dc-3317d61bb783
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f9e5532a55901d8e29addfee58594645440991f6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62821876"
---
# <a name="idebugasyncoperationcallbackoncomplete"></a>IDebugAsyncOperationCallBack::onComplete
Sygnały, że wynik jest dostępna z operacją asynchroniczną debugowania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT onComplete();  
```  
  
#### <a name="parameters"></a>Parametry  
 Ta metoda nie przyjmuje żadnych parametrów.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda sygnalizuje, że wynik jest dostępna z `IDebugAsyncOperation` obiektu. Generowane zdarzenia debuger wątku.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugAsyncOperationCallBack Interface](../../winscript/reference/idebugasyncoperationcallback-interface.md)   
 [IDebugAsyncOperation, interfejs](../../winscript/reference/idebugasyncoperation-interface.md)