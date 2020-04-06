---
title: IDebugProcess3 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3
helpviewer_keywords:
- IDebugProcess3 interface
ms.assetid: 7bd6b952-cf34-4e66-b8f6-d472dac3748f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b423ee2cb95ad55296c452cfdc4b891ee4cd26a0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723547"
---
# <a name="idebugprocess3"></a>IDebugProcess3
Ten interfejs reprezentuje uruchomiony proces i jego programy. Ten interfejs istnieje jako zamiennik kilku metod w interfejsie [IDebugProgram2.](../../../extensibility/debugger/reference/idebugprogram2.md) Zapewnia kontrolę nad wszystkimi programami w procesie.

> [!NOTE]
> [Kontynuuj](../../../extensibility/debugger/reference/idebugprogram2-continue.md), [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md)i [Step](../../../extensibility/debugger/reference/idebugprogram2-step.md) metody są przestarzałe i nie powinny być już używane. Zamiast tego użyj `IDebugProcess3` odpowiednich metod w interfejsie.

## <a name="syntax"></a>Składnia

```
IDebugProcess3 : IDebugProcess2
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Ten interfejs jest implementowany przez niestandardowego dostawcę portu do zarządzania programami jako grupa. Gdy programy są zarządzane jako grupa, można kontrolować ich wykonanie i ustanowić język dla oceniającego wyrażenie. Ten interfejs musi być zaimplementowany przez dostawcę portu.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Ten interfejs jest wywoływany głównie przez menedżera debugowania sesji (SDM) w celu interakcji z grupą programów zidentyfikowanych w tym procesie.

 Wywołanie [QueryInterface](/cpp/atl/queryinterface) na [interfejsie IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) w celu uzyskania tego interfejsu.

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 Oprócz metod dziedziczonych z [IDebugProcess2,](../../../extensibility/debugger/reference/idebugprocess2.md) `IDebugProcess3` implementuje następujące metody.

|Metoda|Opis|
|------------|-----------------|
|[Kontynuować](../../../extensibility/debugger/reference/idebugprocess3-continue.md)|Kontynuuje wykonywanie lub przechodzenie przez proces.|
|[Realizacja](../../../extensibility/debugger/reference/idebugprocess3-execute.md)|Rozpoczyna wykonywanie procesu.|
|[Krok](../../../extensibility/debugger/reference/idebugprocess3-step.md)|Kroki do przodu jedną instrukcję lub instrukcję w procesie.|
|[GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)|Pobiera powód, że proces został uruchomiony do debugowania.|
|[SetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-sethostingprocesslanguage.md)|Ustawia język hostingu, dzięki czemu aparat debugowania można załadować oceniającego odpowiednie wyrażenie.|
|[GetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md)|Pobiera język aktualnie ustawiony dla tego procesu.|
|[DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)|Wyłącza edycję i kontynuuj (ENC) dla tego procesu.<br /><br /> Niestandardowy dostawca portu nie implementuje tej `E_NOTIMPL`metody (zawsze powinien zwracać).|
|[GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)|Pobierz stan ENC dla tego procesu.<br /><br /> Niestandardowy dostawca portu nie implementuje tej `E_NOTIMPL`metody (zawsze powinien zwracać).|
|[GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md)|Pobiera tablicę unikatowych identyfikatorów dla dostępnych aparatów debugowania.|

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
