---
title: 'IRemoteDebugApplicationThread:: SetNextStatement | Microsoft Docs'
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
ms.openlocfilehash: 71e690d0e5b7567aabc88aabde907b67517f12aa
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575507"
---
# <a name="iremotedebugapplicationthreadsetnextstatement"></a>IRemoteDebugApplicationThread::SetNextStatement
Wymusza, aby wykonanie było kontynuowane jak najbliżej danego kontekstu kodu w kontekście danej ramki.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT SetNextStatement(  
   IDebugStackFrame*   pStackFrame,  
   IDebugCodeContext*  pCodeContext  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pStackFrame`  
 podczas Obiekt ramki stosu. Ten argument może mieć wartość NULL, co oznacza, że powinna zostać użyta bieżąca Ramka stosu.  
  
 `pCodeContext`  
 podczas Kontekst kodu. Ten argument może mieć wartość NULL, co oznacza, że powinien zostać użyty bieżący kontekst kodu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda wymusza wykonywanie operacji jak najbliżej kontekstu kodu określonego przez `pCodeContext` w kontekście ramki określonej przez `pStackFrame`. Jeden z tych argumentów może być `NULL`, reprezentujący bieżącą ramkę lub kontekst.  
  
## <a name="see-also"></a>Zobacz także  
 [IRemoteDebugApplicationThread, interfejs](../../winscript/reference/iremotedebugapplicationthread-interface.md)