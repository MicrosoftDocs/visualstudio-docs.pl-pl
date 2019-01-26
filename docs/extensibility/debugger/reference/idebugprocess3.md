---
title: IDebugProcess3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProcess3
helpviewer_keywords:
- IDebugProcess3 interface
ms.assetid: 7bd6b952-cf34-4e66-b8f6-d472dac3748f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bca432c7999d4ec3e7ff4a5a8700eea698486798
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54962800"
---
# <a name="idebugprocess3"></a>IDebugProcess3
Ten interfejs reprezentuje uruchomionego procesu i jego programów. Ten interfejs istnieje jako zamiennika dla kilku metod w [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interfejsu. Zapewnia kontrolę nad wszystkie programy, w tym procesie.  
  
> [!NOTE]
>  [Kontynuuj](../../../extensibility/debugger/reference/idebugprogram2-continue.md), [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md), i [kroku](../../../extensibility/debugger/reference/idebugprogram2-step.md) metody są przestarzałe i nie powinna być używana. Użyj odpowiedniej metody na `IDebugProcess3` zamiast tego interfejsu.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugProcess3 : IDebugProcess2  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Ten interfejs jest implementowany przez dostawcę numery portów do zarządzania programami jako grupa. Gdy programy są zarządzane jako grupa, można kontrolować wykonywanie ich i ustalenia języka dla ewaluatora wyrażeń. Ten interfejs musi być implementowany przez dostawcy portu.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Ten interfejs jest wywoływana przede wszystkim przez Menedżer debugowania sesji (SDM) w celu interakcji z grupy programów identyfikowane w ramach tego procesu.  
  
 Wywołaj [QueryInterface](/cpp/atl/queryinterface) na [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) interfejsu w celu uzyskania tego interfejsu.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 Oprócz metod odziedziczone [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md), `IDebugProcess3` implementuje następujące metody.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md)|Kontynuuje wykonywanie lub przechodzenie krok po kroku przez proces.|  
|[Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md)|Rozpoczyna się wykonanie procesu.|  
|[Step](../../../extensibility/debugger/reference/idebugprocess3-step.md)|Kroki do przodu w jednej instrukcji lub instrukcji w procesie.|  
|[GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)|Pobiera przyczynę, że proces został uruchomiony dla debugowania.|  
|[SetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-sethostingprocesslanguage.md)|Określa język hostingu, tak, aby aparat debugowania mogą ładować Ewaluator wyrażeń odpowiednie.|  
|[GetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md)|Pobiera język aktualnie ustawione dla tego procesu.|  
|[DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)|Wyłącza Edytuj i Kontynuuj (ENC) dla tego procesu.<br /><br /> Dostawcy niestandardowego portu nie obsługuje tej metody (zawsze powinna zwrócić `E_NOTIMPL`).|  
|[GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)|Pobieranie stanu ENC dla tego procesu.<br /><br /> Dostawcy niestandardowego portu nie obsługuje tej metody (zawsze powinna zwrócić `E_NOTIMPL`).|  
|[GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md)|Pobiera tablicę unikatowych identyfikatorów dla silniki debugowania dostępnych.|  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Msdbg.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)