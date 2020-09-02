---
title: Dołączanie do programu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 9a3f5b83-60b5-4ef0-91fe-a432105bd066
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ab9301f31976b084c3c8565329dca248503e40ae
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64795913"
---
# <a name="attaching-to-the-program"></a>Dołączanie do programu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Po zarejestrowaniu programów z odpowiednim portem należy dołączyć debuger do programu, który chcesz debugować.  
  
## <a name="choosing-how-to-attach"></a>Wybieranie sposobu dołączania  
 Istnieją trzy sposoby, w których Menedżer debugowania sesji (SDM) próbuje dołączyć do debugowanego programu.  
  
1. W przypadku programów uruchamianych przez aparat debugowania za pomocą metody [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) (na przykład typowej interpretacji języków) model SDM uzyskuje Interfejs [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) z obiektu [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) skojarzonego z dołączonym programem. Jeśli model SDM może uzyskać `IDebugProgramNodeAttach2` interfejs, model SDM następnie wywoła metodę [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) . `IDebugProgramNodeAttach2::OnAttach`Metoda wraca `S_OK` do wskazuje, że nie dołączyła do programu i że inne próby można dołączyć do programu.  
  
2. Jeśli model SDM może uzyskać Interfejs [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md) z dołączanego programu do, model SDM wywołuje metodę [Attach](../../extensibility/debugger/reference/idebugprogramex2-attach.md) . To podejście jest typowe dla programów, które zostały uruchomione zdalnie przez dostawcę portu.  
  
3. Jeśli nie można dołączyć programu za pomocą `IDebugProgramNodeAttach2::OnAttach` lub `IDebugProgramEx2::Attach` metod, model SDM załaduje aparat debugowania (jeśli nie został jeszcze załadowany) przez wywołanie `CoCreateInstance` funkcji, a następnie wywołanie metody [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) . To podejście jest typowe w przypadku programów uruchomionych lokalnie przez dostawcę portów.  
  
    Istnieje również możliwość, aby dostawca portu niestandardowego wywoływał `IDebugEngine2::Attach` metodę w implementacji niestandardowego dostawcy portów `IDebugProgramEx2::Attach` . Zwykle w tym przypadku dostawca portu niestandardowego uruchamia aparat debugowania na maszynie zdalnej.  
  
   Załącznik jest osiągany, gdy Menedżer debugowania sesji (SDM) wywołuje metodę [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) .  
  
   W przypadku uruchomienia w tym samym procesie co aplikacja do debugowania należy zaimplementować następujące metody [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md):  
  
- [Gethostname](../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md),  
  
- [GetHostPid](../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)  
  
- [GetProgramName](../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)  
  
  Po `IDebugEngine2::Attach` wywołaniu metody wykonaj następujące kroki w implementacji `IDebugEngine2::Attach` metody:  
  
1. Wyślij obiekt zdarzenia [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) do modelu SDM. Aby uzyskać więcej informacji, zobacz [wysyłanie zdarzeń](../../extensibility/debugger/sending-events.md).  
  
2. Wywołaj metodę [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) na obiekcie [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) , który został przesłany do `IDebugEngine2::Attach` metody.  
  
     Zwraca wartość `GUID` , która jest używana do identyfikacji programu. Wartość `GUID` musi być przechowywana w obiekcie, który reprezentuje program lokalny, i musi być zwracana, gdy `IDebugProgram2::GetProgramId` Metoda jest wywoływana w `IDebugProgram2` interfejsie.  
  
    > [!NOTE]
    > W przypadku zaimplementowania `IDebugProgramNodeAttach2` interfejsu program `GUID` jest przesyłany do `IDebugProgramNodeAttach2::OnAttach` metody. `GUID`Jest on używany dla programu `GUID` zwracanego przez `IDebugProgram2::GetProgramId` metodę.  
  
3. Wyślij obiekt zdarzenia [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) , aby powiadomić model SDM, że `IDebugProgram2` obiekt lokalny został utworzony, aby reprezentować program do de. Aby uzyskać szczegółowe informacje, zobacz [wysyłanie zdarzeń](../../extensibility/debugger/sending-events.md).  
  
    > [!NOTE]
    > Nie jest to ten sam `IDebugProgram2` obiekt, który został przekazano do `IDebugEngine2::Attach` metody. Poprzednio zakończony `IDebugProgram2` obiekt jest rozpoznawany tylko przez port i jest oddzielnym obiektem.  
  
## <a name="see-also"></a>Zobacz też  
 [Załącznik z systemem](../../extensibility/debugger/launch-based-attachment.md)   
 [Wysyłanie zdarzeń](../../extensibility/debugger/sending-events.md)   
 [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)   
 [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)   
 [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)   
 [Klej](../../extensibility/debugger/reference/idebugprogramex2-attach.md)   
 [Dołącz](../../extensibility/debugger/reference/idebugengine2-attach.md)
