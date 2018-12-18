---
title: Dołączanie po uruchomieniu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 5a3600a1-dc20-4e55-b2a4-809736a6ae65
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 416c05a7592d9f036a76a5d96537b4be917a0651
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51774708"
---
# <a name="attaching-after-a-launch"></a>Dołączanie po uruchomieniu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Po uruchomieniu programu sesji debugowania jest gotowy do dołączania aparat debugowania (DE) do wspomnianej programu.  
  
## <a name="design-decisions"></a>Decyzje dotyczące projektu  
 Ponieważ komunikacja jest łatwiejsze w przestrzeni adresowej udostępnionego, należy zdecydować, czy warto więcej ułatwiają komunikację między sesji debugowania i "de" lub między DE i program. Wybierz jedną z następujących:  
  
-   Jeśli warto więcej ułatwiają komunikację między sesji debugowania i "de", sesja debugowania wspólnie tworzy DE i pyta, Niemcy, aby dołączyć do programu. Spowoduje to pozostawienie sesji debugowania i "de" ze sobą w jedną przestrzeń adresową i środowiska wykonawczego i programie razem w innym.  
  
-   Jeśli więcej sensu ułatwiających komunikację między DE i program, następnie środowiska wykonawczego wspólnie tworzy DE. Spowoduje to pozostawienie SDM w jedną przestrzeń adresową, a DE, środowiska wykonawczego i program w innym. To jest typowe dla DE, który jest implementowany przy użyciu tłumacza do uruchamiania przy użyciu skryptu języków.  
  
    > [!NOTE]
    >  Jak DE dołącza do programu zależy od implementacji. Komunikacja między DE i program jest również zależna od implementacji.  
  
## <a name="implementation"></a>Implementacja  
 Programistycznie, gdy Menedżer debugowania sesji (SDM) otrzymuje najpierw [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) wywołuje obiekt, który reprezentuje program do uruchomienia, [Attach](../../extensibility/debugger/reference/idebugprogram2-attach.md) metody, podając mu [ IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) obiektu, który jest późniejsza służy do przekazywania zdarzenia debugowania do SDM. `IDebugProgram2::Attach` Następnie wywołuje metodę [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) metody. Aby uzyskać więcej informacji na temat sposobu odbiera SDM `IDebugProgram2` interfejsu, zobacz [powiadamianie portu](../../extensibility/debugger/notifying-the-port.md).  
  
 Jeśli Twoje DE musi zostać uruchomiony w przestrzeni adresowej jako program debugowany, zwykle ponieważ DE tłumacza, uruchamiając skrypt, `IDebugProgramNodeAttach2::OnAttach` metoda zwraca `S_FALSE`, wskazujący, że jego zakończenie procesu dołączania.  
  
 Jeśli z drugiej strony, DE działa w przestrzeni adresowej SDM, `IDebugProgramNodeAttach2::OnAttach` metoda zwraca `S_OK` lub [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) interfejsu nie jest zaimplementowana w ogóle na [IDebugProgramNode2 ](../../extensibility/debugger/reference/idebugprogramnode2.md) obiekt skojarzony z debugowanego programu. W tym przypadku [Dołącz](../../extensibility/debugger/reference/idebugengine2-attach.md) wywoływana jest metoda po pewnym czasie ukończyć operacji dołączania.  
  
 W tym drugim przypadku należy wywołać [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) metody `IDebugProgram2` obiektu, który został przekazany do `IDebugEngine2::Attach` metody, magazyn `GUID` w lokalnym programie obiektu i zwraca ten `GUID` po `IDebugProgram2::GetProgramId` następnie wywoływana jest metoda dla tego obiektu. `GUID` Służy do identyfikowania program jednoznacznie między różnymi składnikami debugowania.  
  
 Należy pamiętać, że w przypadku właściwości `IDebugProgramNodeAttach2::OnAttach` metody zwracają `S_FALSE`, `GUID` do użycia dla programu jest przekazywany do tej metody, a jest `IDebugProgramNodeAttach2::OnAttach` metodę, która ustawia `GUID` na obiekt lokalny program.  
  
 DE zostanie dołączony do programu i jest gotowa do wysyłania zdarzenia uruchamiania.  
  
## <a name="see-also"></a>Zobacz też  
 [Dołączanie bezpośrednio do programu](../../extensibility/debugger/attaching-directly-to-a-program.md)   
 [Powiadamianie portu](../../extensibility/debugger/notifying-the-port.md)   
 [Zadania debugowania](../../extensibility/debugger/debugging-tasks.md)   
 [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [Dołącz](../../extensibility/debugger/reference/idebugprogram2-attach.md)   
 [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md)

