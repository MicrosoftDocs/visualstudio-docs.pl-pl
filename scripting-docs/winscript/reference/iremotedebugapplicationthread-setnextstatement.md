---
title: IRemoteDebugApplicationThread::SetNextStatement | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationThread.SetNextStatement
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplicationThread::SetNextStatement
ms.assetid: 356766da-f7b7-4e8d-b4f3-2ab8da0609b8
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0c4b19322a15e92adcf2609c479af6b21e2078bd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62788144"
---
# <a name="iremotedebugapplicationthreadsetnextstatement"></a>IRemoteDebugApplicationThread::SetNextStatement
Wymusza wykonanie kontynuować możliwie blisko kontekst kodu podanego w kontekście danej ramki.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT SetNextStatement(  
   IDebugStackFrame*   pStackFrame,  
   IDebugCodeContext*  pCodeContext  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pStackFrame`  
 [in] Obiekt w ramce stosu. Ten argument może być NULL, co oznacza, że należy używać bieżącej ramki stosu.  
  
 `pCodeContext`  
 [in] Kontekst kodu. Ten argument może być NULL, co oznacza, że bieżący kontekst kodu powinny być używane.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda wymusza możliwie blisko kontekst kodu określonego przez kontynuowanie wykonywania `pCodeContext`, w kontekście ramki określonego przez `pStackFrame`. Jedną z tych argumentów może być `NULL`, reprezentujący bieżące ramce lub kontekstu.  
  
## <a name="see-also"></a>Zobacz też  
 [IRemoteDebugApplicationThread, interfejs](../../winscript/reference/iremotedebugapplicationthread-interface.md)