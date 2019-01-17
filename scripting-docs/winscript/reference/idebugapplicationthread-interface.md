---
title: Interfejs IDebugApplicationThread | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThread interface
ms.assetid: f869c328-4409-4b74-a6c3-9e63fc58c63d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 262174d0daecd2c37bafbecee13532ba62e9967f
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54347791"
---
# <a name="idebugapplicationthread-interface"></a>Interfejs IDebugApplicationThread
Umożliwia aparatów języka i hosty zapewnienie synchronizacji wątków i zachować informacje o stanie debugowania właściwe dla wątków. Ten interfejs rozszerza `IRemoteDebugApplicationThread` interfejsu, aby zapewnić zdalną dostęp do wątku.  
  
 Oprócz metod odziedziczone `IRemoteDebugApplicationThread`, `IDebugApplicationThread` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDebugApplicationThread::SynchronousCallIntoThread](../../winscript/reference/idebugapplicationthread-synchronouscallintothread.md)|Udostępnia mechanizm do obiektu wywołującego uruchomić kod w wątku aplikacji.|  
|[IDebugApplicationThread::QueryIsCurrentThread](../../winscript/reference/idebugapplicationthread-queryiscurrentthread.md)|Określa, czy ten wątek jest aktualnie uruchomionemu wątkowi.|  
|[IDebugApplicationThread::QueryIsDebuggerThread](../../winscript/reference/idebugapplicationthread-queryisdebuggerthread.md)|Określa, czy ten wątek jest debugera wątku.|  
|[IDebugApplicationThread::SetDescription](../../winscript/reference/idebugapplicationthread-setdescription.md)|Określa opis tego wątku.|  
|[IDebugApplicationThread::SetStateString](../../winscript/reference/idebugapplicationthread-setstatestring.md)|Określa opis stan wątku.|