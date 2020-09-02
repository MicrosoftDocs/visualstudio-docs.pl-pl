---
title: 'IDebugProgramNode2:: Attach_V7 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::Attach
helpviewer_keywords:
- IDebugProgramNode2::Attach_V7
- IDebugProgramNode2::Attach
ms.assetid: b5ffc736-efc7-4ca8-964d-5536ff891b0e
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 08028f2b03f3ea36cc72172ca8f9de31740b49f3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64784989"
---
# <a name="idebugprogramnode2attach_v7"></a>IDebugProgramNode2::Attach_V7
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Przestarzałe. NIE NALEŻY UŻYWAĆ.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT Attach_V7 (   
   IDebugProgram2*       pMDMProgram,  
   IDebugEventCallback2* pCallback,  
   DWORD                 dwReason  
);  
```  
  
```csharp  
int Attach_V7 (   
   IDebugProgram2       pMDMProgram,  
   IDebugEventCallback2 pCallback,  
   uint                 dwReason  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pMDMProgram`  
 podczas Interfejs [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) , który reprezentuje program do dołączenia.  
  
 `pCallback`  
 podczas Interfejs [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) , który ma być używany do wysyłania zdarzeń debugowania do modelu SDM.  
  
 `dwReason`  
 podczas Wartość z wyliczenia [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) , która określa przyczynę dołączenia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja powinna zawsze zwrócić `E_NOTIMPL` .  
  
## <a name="remarks"></a>Uwagi  
  
> [!WARNING]
> Począwszy od programu [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] , ta metoda nie jest już używana i zawsze powinna zwracać `E_NOTIMPL` . Zapoznaj się z interfejsem [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md) , jeśli węzeł programu ma wskazywać, że nie można go dołączyć do programu, lub jeśli węzeł programu jest po prostu ustawiony na program `GUID` . W przeciwnym razie Zaimplementuj metodę [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) .  
  
## <a name="prior-to-visual-studio-2005"></a>Przed Visual Studio 2005  
 Ta metoda musi być implementowana tylko wtedy, gdy wszystkie uruchomienia w przestrzeni adresowej debugowanego programu. W przeciwnym razie ta metoda powinna zwrócić `S_FALSE` .  
  
 Gdy ta metoda jest wywoływana, element DE musi wysłać obiekt zdarzenia [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) , jeśli nie został jeszcze wysłany do tego wystąpienia interfejsu [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) , a także obiektów zdarzeń [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) i [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) . Obiekt zdarzenia [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) jest następnie wysyłany, jeśli `dwReason` parametr ma wartość `ATTACH_REASON_LAUNCH` .  
  
 DE musi wywołać metodę [GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) na obiekcie [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) dostarczonym przez obiekt zdarzenia [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) i musi przechowywać identyfikator GUID tego programu w danych wystąpienia dla `IDebugProgram2` obiektu zaimplementowanego przez de.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [Klej](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)   
 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)   
 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)   
 [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)   
 [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)
