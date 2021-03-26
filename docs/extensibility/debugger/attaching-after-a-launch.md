---
title: Dołączanie po uruchomieniu | Microsoft Docs
description: Po uruchomieniu programu sesja debugowania jest gotowa do dołączenia aparatu debugowania do programu. Wybierz podejście projektowe do komunikacji z aparatem debugowania.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 5a3600a1-dc20-4e55-b2a4-809736a6ae65
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9010d2619b76c2932ca1a8a5aed8db6c6a5cf075
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105055326"
---
# <a name="attach-after-a-launch"></a>Dołącz po uruchomieniu
Po uruchomieniu programu sesja debugowania jest gotowa do dołączenia aparatu debugowania (DE) do podanego programu.

## <a name="design-decisions"></a>Decyzje projektowe
 Ze względu na to, że komunikacja jest łatwiejsza w obrębie udostępnionej przestrzeni adresowej, należy wybrać między dwoma podejściami do projektowania: Ustawianie komunikacji między sesją debugowania a DE. Lub ustaw komunikację między programami DE i. Wybierz jeden z następujących:

- Jeśli okaże się, że w celu skonfigurowania komunikacji między sesją debugowania a DE, sesja debugowania zostanie utworzona i zażąda odłączenia do programu. Ten projekt opuszcza sesję debugowania i znajduje się w jednej przestrzeni adresowej oraz w środowisku i programie środowiska uruchomieniowego w innym.

- Jeśli nie ma sensu konfigurowania komunikacji między programami a a programem, środowisko czasu wykonywania współtworzy. Ten projekt pozostawia model SDM w jednej przestrzeni adresowej, w środowisku uruchomieniowym i programie razem w innym. Ten projekt jest typowy dla DE, który jest implementowany przy użyciu interpretera do uruchamiania języków skryptowych.

    > [!NOTE]
    > Jak dołączanie do programu jest zależne od implementacji. Komunikacja między programami a a programem jest również zależna od implementacji.

## <a name="implementation"></a>Implementacja
 Program programowo, gdy Menedżer debugowania sesji najpierw odbiera obiekt [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) , który reprezentuje program do uruchomienia, wywołuje metodę [Attach](../../extensibility/debugger/reference/idebugprogram2-attach.md) , przekazując do niej obiekt [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) , który jest później używany do przekazywania zdarzeń debugowania z powrotem do modelu SDM. `IDebugProgram2::Attach`Metoda następnie wywołuje metodę [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) . Aby uzyskać więcej informacji o tym, jak model SDM odbiera `IDebugProgram2` interfejs, zobacz [Powiadamianie portu](../../extensibility/debugger/notifying-the-port.md).

 Jeśli nie ma potrzeby uruchamiania w tej samej przestrzeni adresowej co debugowany program: ponieważ DE jest zwykle częścią interpretera, który uruchamia skrypt, `IDebugProgramNodeAttach2::OnAttach` Metoda zwraca `S_FALSE` . `S_FALSE`Zwracana wartość wskazuje, że zakończył proces dołączania.

 Jeśli jednak to nie działa w przestrzeni adresowej modelu SDM: `IDebugProgramNodeAttach2::OnAttach` Metoda zwraca `S_OK` lub interfejs [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) nie jest zaimplementowany we wszystkich obiektach [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) skojarzonych z debugowanym programem. W takim przypadku Metoda [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) jest ostatecznie wywoływana w celu ukończenia operacji Attach.

 W tym drugim przypadku należy wywołać metodę [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) na `IDebugProgram2` obiekcie, który został przesłany do `IDebugEngine2::Attach` metody, zapisać `GUID` w obiekcie programu lokalnego i zwrócić go, `GUID` gdy `IDebugProgram2::GetProgramId` Metoda zostanie wywołana w tym obiekcie. Służy `GUID` do unikatowego identyfikowania programu w różnych składnikach debugowania.

 W przypadku `IDebugProgramNodeAttach2::OnAttach` zwrócenia metody `S_FALSE` , `GUID` do użycia dla programu jest przenoszona do tej metody i jest to `IDebugProgramNodeAttach2::OnAttach` Metoda, która ustawia `GUID` obiekt w obiekcie programu lokalnego.

 DE jest teraz dołączony do programu i jest gotowy do wysłania wszelkich zdarzeń uruchomienia.

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
