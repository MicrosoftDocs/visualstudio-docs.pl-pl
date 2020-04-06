---
title: Dołączanie po uruchomieniu | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 5a3600a1-dc20-4e55-b2a4-809736a6ae65
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3a4ce0a7465891035b43bbb8f6f22f0c064d104c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739286"
---
# <a name="attach-after-a-launch"></a>Dołącz po uruchomieniu
Po uruchomieniu programu sesja debugowania jest gotowa do dołączenia aparatu debugowania (DE) do wspomnianego programu.

## <a name="design-decisions"></a>Decyzje projektowe
 Ponieważ komunikacja jest łatwiejsza w udostępnionej przestrzeni adresowej, należy wybrać między dwoma podejściami projektowych: ustawić komunikację między sesją debugowania a DE. Możesz też ustawić komunikację między DE a programem. Wybierz jedną z następujących opcji:

- Jeśli bardziej sensowne jest skonfigurowanie komunikacji między sesją debugowania a de, sesja debugowania współtworzy DE i prosi DE o dołączenie do programu. Ten projekt pozostawia sesji debugowania i DE razem w jednej przestrzeni adresowej i środowiska wykonywania i programu razem w innym.

- Jeśli bardziej sensowne jest skonfigurowanie komunikacji między DE a programem, środowisko wykonywania współtworzy DE. Ten projekt pozostawia SDM w jednej przestrzeni adresowej i DE, środowisko wykonywania i program razem w innym. Ten projekt jest typowy dla DE, który jest implementowany z interpreterem do uruchamiania języków skryptowych.

    > [!NOTE]
    > Jak DE dołącza do programu jest zależna od implementacji. Komunikacja między DE a programem jest również zależna od implementacji.

## <a name="implementation"></a>Wdrażanie
 Programowo, gdy menedżer debugowania sesji (SDM) po raz pierwszy odbiera obiekt [IDebugProgram2,](../../extensibility/debugger/reference/idebugprogram2.md) który reprezentuje program, który ma zostać uruchomiony, wywołuje [metodę Dołącz,](../../extensibility/debugger/reference/idebugprogram2-attach.md) przekazując jej obiekt [IDebugEventCallback2,](../../extensibility/debugger/reference/idebugeventcallback2.md) który jest później używany do przekazywania zdarzeń debugowania z powrotem do SDM. Metoda `IDebugProgram2::Attach` następnie wywołuje [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) metody. Aby uzyskać więcej informacji na temat `IDebugProgram2` sposobu odciąwania interfejsu przez moduł SDM, zobacz [Powiadamianie portu](../../extensibility/debugger/notifying-the-port.md).

 Jeśli de musi działać w tej samej przestrzeni adresowej co program, który debugujesz: ponieważ DE jest zazwyczaj `IDebugProgramNodeAttach2::OnAttach` częścią `S_FALSE`interpretera, który uruchamia skrypt, metoda zwraca . Return `S_FALSE` wskazuje, że zakończył proces dołączania.

 Jeśli jednak DE działa w przestrzeni adresowej SDM: `IDebugProgramNodeAttach2::OnAttach` `S_OK`metoda zwraca lub [interfejs IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) nie jest w ogóle zaimplementowany na [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) obiektu skojarzonego z programem, który debugujesz. W takim przypadku [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) metoda jest po pewnym czasie wywoływana, aby zakończyć operację dołączania.

 W tym ostatnim przypadku należy wywołać [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) `IDebugProgram2` metody na `IDebugEngine2::Attach` obiekt, który `GUID` został przekazany do metody, `GUID` przechowywać w lokalnym obiekcie programu i zwrócić to, gdy `IDebugProgram2::GetProgramId` metoda jest następnie wywoływana na ten obiekt. Jest `GUID` używany do identyfikowania programu jednoznacznie w różnych składnikach debugowania.

 W przypadku `IDebugProgramNodeAttach2::OnAttach` metody zwracanej `S_FALSE`, `GUID` do użycia dla programu jest przekazywana `IDebugProgramNodeAttach2::OnAttach` do tej `GUID` metody i jest to metoda, która ustawia na lokalnym obiekcie programu.

 DE jest teraz dołączony do programu i gotowy do wysłania wszelkich zdarzeń startowych.

## <a name="see-also"></a>Zobacz też
- [Dołączanie bezpośrednio do programu](../../extensibility/debugger/attaching-directly-to-a-program.md)
- [Powiadamianie portu](../../extensibility/debugger/notifying-the-port.md)
- [Zadania debugowania](../../extensibility/debugger/debugging-tasks.md)
- [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)
- [Dołącz](../../extensibility/debugger/reference/idebugprogram2-attach.md)
- [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [Dołącz](../../extensibility/debugger/reference/idebugengine2-attach.md)
