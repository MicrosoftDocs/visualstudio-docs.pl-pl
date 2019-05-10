---
title: IEnumDebugModules2 | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugModules2
helpviewer_keywords:
- IEnumDebugModules2
ms.assetid: 4fe28074-a960-41ad-b74d-b57f04c0c0ad
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 548bcd0328f7bdf52e47eb9a4295168ca47a2517
ms.sourcegitcommit: 6196d0b7fdcb08ba6d28a8151ad36b8d1139f2cc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65226692"
---
# <a name="ienumdebugmodules2"></a>IEnumDebugModules2
Ten interfejs wylicza listę modułów.

## <a name="syntax"></a>Składnia

```
IEnumDebugModules2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Aparat debugowania (DE) implementuje ten interfejs reprezentujący listę moduły załadowane w programie.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Visual Studio wywołania [enummodules —](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) uzyskać ten interfejs.

## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności
 W poniższej tabeli przedstawiono metody `IEnumDebugModules2`.

|Metoda|Opis|
|------------|-----------------|
|[Next](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md)|Pobiera określoną liczbę modułów w kolejności wyliczenia.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugmodules2-skip.md)|Pomija określoną liczbę modułów w kolejności wyliczenia.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugmodules2-reset.md)|Resetuje sekwencji wyliczenia na początku.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugmodules2-clone.md)|Tworzy moduł wyliczający, który zawiera ten sam stan wyliczenia jako bieżącego modułu wyliczającego.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugmodules2-getcount.md)|Pobiera liczbę modułów.|

## <a name="remarks"></a>Uwagi
 Program Visual Studio używa tego interfejsu, głównie w celu aktualizacji **modułów** okna.

 Na potrzeby debugowania w programie Visual Studio program jest logicznej kolejności instrukcji kodu, które mogą między granicami modułów, dlatego potrzebę listę modułów dla pojedynczego [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interfejsu. Moduł pierwszy na liście zazwyczaj zawiera punkt wejścia początkowej dla skojarzonego programu.

## <a name="requirements"></a>Wymagania
 Header: msdbg.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)