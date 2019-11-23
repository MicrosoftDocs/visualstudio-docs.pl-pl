---
title: 'IRemoteDebugApplication:: ResumeFromBreakPoint | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplication.ResumeFromBreakPoint
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplication::ResumeFromBreakPoint
ms.assetid: a613cc2b-1d69-4713-a235-64372c253b4a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7fead9c14efbe73bd006a5ff3e1cfb10ad40404b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577460"
---
# <a name="iremotedebugapplicationresumefrombreakpoint"></a>IRemoteDebugApplication::ResumeFromBreakPoint
Kontynuuje aplikację, która jest obecnie w punkcie przerwania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT ResumeFromBreakPoint(  
   IRemoteDebugApplicationThread*  prptFocus,  
   BREAKRESUMEACTION               bra,  
   ERRORRESUMEACTION               era  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `prptFocus`  
 podczas W przypadku trybów taktowania wątek, w którym ma wpływ tryb taktowania.  
  
 `bra`  
 podczas Akcja, która ma zostać podjęta po wznowieniu działania aplikacji.  
  
 `era`  
 podczas Akcja, która ma zostać podjęta w przypadku, gdy aplikacja została zatrzymana z powodu błędu.  
  
## <a name="return-value"></a>Wartość zwrócona  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Value|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda kontynuuje aplikację, która jest obecnie w punkcie przerwania.  
  
## <a name="see-also"></a>Zobacz także  
 [IRemoteDebugApplication  interfejsu](../../winscript/reference/iremotedebugapplication-interface.md)  
   [Wyliczenie BREAKRESUMEACTION](../../winscript/reference/breakresumeaction-enumeration.md)  
 [ERRORRESUMEACTION, wyliczenie](../../winscript/reference/errorresumeaction-enumeration.md)