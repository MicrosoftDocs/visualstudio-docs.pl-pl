---
title: Powiadamianie portu | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ports, notification
ms.assetid: f9fce48e-7d4e-4627-a0fb-77b75428146a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b022cca2b69c8cb80b24fa34e3b020923cff4022
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56689203"
---
# <a name="notify-the-port"></a>Powiadom portu
Po uruchomieniu programu, numer portu musi być powiadomiony, w następujący sposób:

1. Gdy port otrzymuje nowy węzeł program, wysyła zdarzenie tworzenia programu do sesji debugowania. Zdarzenie niesie ze sobą interfejs, który reprezentuje program.

2. Program dla identyfikatora aparat debugowania (DE), który można dołączyć do wysyła zapytanie do sesji debugowania.

3. Sesja debugowania sprawdza, czy DE na liście dopuszczalnych DEs dla tego programu. Sesja debugowania pobiera tej listy z aktywnym programem ustawień rozwiązania pierwotnie przekazana do niej przy użyciu pakietu debugowania.

    DE musi znajdować się na liście dopuszczalny rozmiar, w przeciwnym razie DE nie zostanie dołączony do programu.

   Programowo, gdy port otrzymuje najpierw nowego węzła programu, tworzy [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) interfejsu do reprezentowania program.

> [!NOTE]
>  To nie należy mylić z `IDebugProgram2` interfejsu utworzone później przez aparat debugowania (DE).

 Port wysyła [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) zdarzenie tworzenia programu do Menedżer debugowania sesji (SDM) za pomocą COM `IConnectionPoint` interfejsu.

> [!NOTE]
>  To nie należy mylić z `IDebugProgramCreateEvent2` interfejsu, która jest wysyłana później przez DE.

 Wraz z samego interfejsu do zdarzenia, wysyła port [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md), [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md), i [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) interfejsów, które reprezentują port, przetwarzania, i Program, odpowiednio. Wywołania SDM [IDebugProgram2::GetEngineInfo](../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md) można pobrać identyfikatora GUID DE, który można debugować program. Identyfikator GUID początkowo zostały pobrane z [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) interfejsu.

 SDM sprawdza, czy DE na liście dopuszczalnych DEs. SDM pobiera tej listy z aktywnym programem ustawień rozwiązania pierwotnie przekazana do niej przy użyciu pakietu debugowania. DE musi znajdować się na liście dopuszczalny rozmiar, w przeciwnym razie nie można dołączyć do programu.

 Tożsamość DE jest znany, SDM po chcesz dołączyć do programu.

## <a name="see-also"></a>Zobacz także
- [Uruchamianie programu](../../extensibility/debugger/launching-a-program.md)
- [Dołączanie po uruchomieniu](../../extensibility/debugger/attaching-after-a-launch.md)
- [Zadania debugowania](../../extensibility/debugger/debugging-tasks.md)