---
title: 'IDebugAsyncOperationCallBack:: OnComplete | Microsoft Docs'
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
ms.openlocfilehash: a15ae57d64d2b1e7be867c20e9683e4aaa415974
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573231"
---
# <a name="idebugasyncoperationcallbackoncomplete"></a>IDebugAsyncOperationCallBack::onComplete
Sygnalizuje, że wynik jest dostępny z asynchronicznej operacji debugowania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT onComplete();  
```  
  
#### <a name="parameters"></a>Parametry  
 Ta metoda nie przyjmuje żadnych parametrów.  
  
## <a name="return-value"></a>Wartość zwrócona  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Value|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda sygnalizuje, że wynik jest dostępny z obiektu `IDebugAsyncOperation`. Zdarzenie jest wyzwalane w wątku debugera.  
  
## <a name="see-also"></a>Zobacz także  
 [IDebugAsyncOperationCallBack  interfejsu](../../winscript/reference/idebugasyncoperationcallback-interface.md)  
 [IDebugAsyncOperation, interfejs](../../winscript/reference/idebugasyncoperation-interface.md)