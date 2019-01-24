---
title: IDebugEngine2 | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngine2
helpviewer_keywords:
- IDebugEngine2 interface
ms.assetid: 1f0e9ac0-6dfb-461a-976c-888d82144cdb
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0c011a530bbd4323546257a40334a4b8a0f57bdb
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54790725"
---
# <a name="idebugengine2"></a>IDebugEngine2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ten interfejs reprezentuje aparat debugowania (DE). Służy do zarządzania różnymi aspektami sesji debugowania od utworzenia punktów przerwania do ustawiania i czyszczenia wyjątków.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugEngine2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Ten interfejs jest implementowany przez niestandardowe DE Zarządzanie debugowania programów. Ten interfejs musi być implementowany przez DE.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Ten interfejs jest wywoływane przez Menedżer debugowania sesji (SDM) do zarządzania sesji debugowania, w tym Zarządzanie wyjątkami, tworzenie punktów przerwania i reagowanie na zdarzenia synchroniczne wysyłane przez DE.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 W poniższej tabeli przedstawiono metody `IDebugEngine2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)|Tworzy moduł wyliczający dla wszystkich programów, które jest debugowane DE.|  
|[Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)|DE dołącza do programu.|  
|[CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)|Tworzy oczekujący punkt przerwania w DE.|  
|[SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)|Określa, jak DE powinna obsługiwać dany wyjątek.|  
|[RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)|Usuwa określony wyjątek, więc nie jest już obsługiwane przez aparat debugowania.|  
|[RemoveAllSetExceptions](../../../extensibility/debugger/reference/idebugengine2-removeallsetexceptions.md)|Usuwa listy wyjątków, ustawionych przez środowisko IDE dla określonej architektury środowiska wykonawczego lub języka.|  
|[GetEngineID](../../../extensibility/debugger/reference/idebugengine2-getengineid.md)|Pobiera identyfikator GUID DE.|  
|[DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)|Informuje, Zdarzenie niszczenia DE nietypowo zakończony program określony i, Niemcy, należy wyczyścić wszystkie odwołania do programu i wysyłania programu.|  
|[ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)|Metoda wywoływana przez SDM, aby wskazać, że w przypadku zdarzenia synchroniczne debugowania do SDM, z wcześniej wysłanych przez DE został odbierane i przetwarzane.|  
|[SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)|Ustawia ustawienia regionalne DE.|  
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugengine2-setregistryroot.md)|Ustawia katalog główny rejestru aktualnie używany przez DE.|  
|[SetMetric](../../../extensibility/debugger/reference/idebugengine2-setmetric.md)|Ustawia metrykę.|  
|[CauseBreak](../../../extensibility/debugger/reference/idebugengine2-causebreak.md)|Żądania, że wszystkie programy, które jest debugowane to DE zatrzymać wykonywanie po następnym jednego z ich wątków próbuje uruchomić.|  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Msdbg.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Zdarzenia](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [GetEngine](../../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md)
