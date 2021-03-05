---
description: Ten interfejs reprezentuje proces uruchomiony i jego programy.
title: IDebugProcess3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3
helpviewer_keywords:
- IDebugProcess3 interface
ms.assetid: 7bd6b952-cf34-4e66-b8f6-d472dac3748f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a2303dfef18a1abccc728d80def0de25b4e7eadd
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102169187"
---
# <a name="idebugprocess3"></a>IDebugProcess3
Ten interfejs reprezentuje proces uruchomiony i jego programy. Ten interfejs istnieje jako zamiennik do kilku metod w interfejsie [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) . Zapewnia kontrolę nad wszystkimi programami w procesie.

> [!NOTE]
> Metody [Continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md), [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md)i [Step](../../../extensibility/debugger/reference/idebugprogram2-step.md) są przestarzałe i nie powinny być już używane. Zamiast tego użyj odpowiednich metod w `IDebugProcess3` interfejsie.

## <a name="syntax"></a>Składnia

```
IDebugProcess3 : IDebugProcess2
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Ten interfejs jest implementowany przez niestandardowego dostawcę portu do zarządzania programami jako grupą. Gdy programy są zarządzane jako Grupa, można kontrolować ich wykonywanie i ustanawiać język dla ewaluatora wyrażeń. Ten interfejs musi być zaimplementowany przez dostawcę portu.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Ten interfejs jest wywoływany głównie przez Menedżera debugowania sesji (SDM) w celu współdziałania z grupą programów identyfikowanych w tym procesie.

 Wywołaj metodę [QueryInterface](/cpp/atl/queryinterface) na interfejsie [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) , aby uzyskać ten interfejs.

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 Oprócz metod dziedziczonych z [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md), `IDebugProcess3` implementuje następujące metody.

|Metoda|Opis|
|------------|-----------------|
|[Kontynuuj](../../../extensibility/debugger/reference/idebugprocess3-continue.md)|Kontynuuje wykonywanie operacji lub przechodzenie przez proces.|
|[Wykonaj polecenie](../../../extensibility/debugger/reference/idebugprocess3-execute.md)|Rozpoczyna wykonywanie procesu.|
|[Krok](../../../extensibility/debugger/reference/idebugprocess3-step.md)|Kroki do przodu jednej instrukcji lub instrukcji w procesie.|
|[GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)|Pobiera przyczynę uruchomienia procesu na potrzeby debugowania.|
|[SetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-sethostingprocesslanguage.md)|Ustawia język hostingu, aby aparat debugowania mógł załadować odpowiednie ewaluatora wyrażeń.|
|[GetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md)|Pobiera aktualnie ustawiony język dla tego procesu.|
|[DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)|Wyłącza funkcję Edytuj i Kontynuuj (ENC) dla tego procesu.<br /><br /> Dostawca portu niestandardowego nie implementuje tej metody (zawsze powinna zwracać `E_NOTIMPL` ).|
|[GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)|Pobierz stan ENC dla tego procesu.<br /><br /> Dostawca portu niestandardowego nie implementuje tej metody (zawsze powinna zwracać `E_NOTIMPL` ).|
|[GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md)|Pobiera tablicę unikatowych identyfikatorów dla dostępnych aparatów debugowania.|

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
