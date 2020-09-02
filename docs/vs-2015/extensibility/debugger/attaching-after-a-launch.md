---
title: Dołączanie po uruchomieniu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 5a3600a1-dc20-4e55-b2a4-809736a6ae65
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 693cf6d746f51862415f2f30e46d48a998047f14
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64835344"
---
# <a name="attaching-after-a-launch"></a>Dołączanie po uruchomieniu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Po uruchomieniu programu sesja debugowania jest gotowa do dołączenia aparatu debugowania (DE) do wspomnianego programu.  
  
## <a name="design-decisions"></a>Decyzje dotyczące projektu  
 Ze względu na to, że komunikacja jest łatwiejsza w obrębie udostępnionej przestrzeni adresowej, należy zdecydować, czy ma to na celu ułatwienie komunikacji między sesją debugowania a częścią lub między programami DE i. Wybierz jeden z następujących:  
  
- Jeśli ma to na celu ułatwienie komunikacji między sesją debugowania a DE, wówczas sesja debugowania współtworzy i poprosi o dołączenie do programu. Spowoduje to pozostawienie sesji debugowania i nawiąże w jednej przestrzeni adresowej, a środowisko uruchomieniowe i program razem w innym.  
  
- Jeśli ma to na celu ułatwienie komunikacji między programami a a programem, środowisko czasu wykonywania współtworzy. Spowoduje to pozostawienie modelu SDM w jednej przestrzeni adresowej, a także środowiska uruchomieniowego i programu w innym miejscu. Jest to typowa część DE, która jest zaimplementowana przy użyciu interpretera do uruchamiania języków skryptowych.  
  
    > [!NOTE]
    > Jak dołączanie do programu jest zależne od implementacji. Komunikacja między programami a a programem jest również zależna od implementacji.  
  
## <a name="implementation"></a>Implementacja  
 Program programowo, gdy Menedżer debugowania sesji najpierw odbiera obiekt [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) , który reprezentuje program do uruchomienia, wywołuje metodę [Attach](../../extensibility/debugger/reference/idebugprogram2-attach.md) , przekazując do niej obiekt [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) , który jest później używany do przekazywania zdarzeń debugowania z powrotem do modelu SDM. `IDebugProgram2::Attach`Metoda następnie wywołuje metodę [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) . Aby uzyskać więcej informacji o tym, jak model SDM odbiera `IDebugProgram2` interfejs, zobacz [Powiadamianie portu](../../extensibility/debugger/notifying-the-port.md).  
  
 Jeśli nie ma potrzeby uruchamiania w tej samej przestrzeni adresowej co debugowany program, zazwyczaj z powodu braku części interpretera, która uruchamia skrypt, `IDebugProgramNodeAttach2::OnAttach` Metoda zwraca `S_FALSE` , wskazując, że zakończył proces dołączania.  
  
 Jeśli z drugiej strony, kończy działanie w przestrzeni adresowej modelu SDM, `IDebugProgramNodeAttach2::OnAttach` Metoda zwróci `S_OK` lub interfejs [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) nie jest zaimplementowany we wszystkich obiektach [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) skojarzonych z debugowanym programem. W takim przypadku Metoda [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) jest ostatecznie wywoływana w celu ukończenia operacji Attach.  
  
 W tym drugim przypadku należy wywołać metodę [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) na `IDebugProgram2` obiekcie, który został przesłany do `IDebugEngine2::Attach` metody, zapisać `GUID` w obiekcie programu lokalnego i zwrócić go, `GUID` gdy `IDebugProgram2::GetProgramId` Metoda zostanie wywołana w tym obiekcie. Służy `GUID` do unikatowego identyfikowania programu w różnych składnikach debugowania.  
  
 Należy zauważyć, że w przypadku `IDebugProgramNodeAttach2::OnAttach` powrotu metody `S_FALSE` , `GUID` do użycia dla programu jest przenoszona do tej metody i jest to `IDebugProgramNodeAttach2::OnAttach` Metoda, która ustawia `GUID` obiekt w obiekcie programu lokalnego.  
  
 DE jest teraz dołączony do programu i jest gotowy do wysłania wszelkich zdarzeń uruchomienia.  
  
## <a name="see-also"></a>Zobacz też  
 [Dołączanie bezpośrednio do programu](../../extensibility/debugger/attaching-directly-to-a-program.md)   
 [Powiadamianie portu](../../extensibility/debugger/notifying-the-port.md)   
 [Zadania debugowania](../../extensibility/debugger/debugging-tasks.md)   
 [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [Klej](../../extensibility/debugger/reference/idebugprogram2-attach.md)   
 [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [Dołącz](../../extensibility/debugger/reference/idebugengine2-attach.md)
