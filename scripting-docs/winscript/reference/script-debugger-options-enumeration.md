---
title: SCRIPT_DEBUGGER_OPTIONS, Wyliczenie | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SCRIPT_DEBUGGER_OPTIONS Enumeration
ms.assetid: aef41ec0-6f65-48e8-a69e-44b4e4fb929f
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c69d419732786442cda275bf85c74ab2b9d3e870
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574566"
---
# <a name="script_debugger_options-enumeration"></a>Wyliczenie SCRIPT_DEBUGGER_OPTIONS
Wskazuje zestaw opcji i/lub możliwości, które mają zastosowanie do dołączonego debugera. Używane w [IDebugApplicationNode100:: GetExcludedDocuments](../../winscript/reference/idebugapplicationnode100-getexcludeddocuments.md) i [IDebugApplicationNode100:: SetFilterForEventSink](../../winscript/reference/idebugapplicationnode100-setfilterforeventsink.md)  
  
> [!IMPORTANT]
> Te stałe są implementowane przez PDM v 10.0 i nowsze. Znajduje się w zestawie activdbg100.h.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
typedef SCRIPT_DEBUGGER_OPTIONS  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Wartość|Opis|  
|------------|-----------|-----------------|  
|SDO_NONE|0x00000000|Nie ustawiono żadnych opcji.|  
|SDO_ENABLE_FIRST_CHANCE_EXCEPTIONS|0x00000001|Wskazuje, że środowisko uruchomieniowe skryptu ma zgłaszać zdarzenia BREAKREASON_ERROR, gdy wyjątek jest zgłaszany. Ta opcja może być ustawiana przez debuger lub ustawiana przez kod użytkownika za pośrednictwem `Debug.enableFirstChanceExceptions(<true&#124;false>)`.|  
|SDO_ENABLE_WEB_WORKER_SUPPORT|0x00000002|Wskazuje, że dołączony debuger obsługuje internetowe procesy robocze.|  
  
## <a name="see-also"></a>Zobacz także  
 [Stałe, wyliczenia i struktury debugera aktywnego skryptu](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)