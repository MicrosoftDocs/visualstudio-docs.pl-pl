---
title: IDebugProcessEx2 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2
helpviewer_keywords:
- IDebugProcessEx2 interface
ms.assetid: 44e309ba-1d6f-499b-aa7e-9b34858a6d57
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 743dd1aa72d9b8db6b848618c8a2ad6c8c8ecaaf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723328"
---
# <a name="idebugprocessex2"></a>IDebugProcessEx2
Ten interfejs umożliwia menedżera debugowania sesji (SDM) powiadamiać proces, który jest dołączanie do lub odłączanie od procesu.

## <a name="syntax"></a>Składnia

```
IDebugProcessEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Dostawca portu niestandardowego implementuje ten interfejs na tym samym obiekcie co interfejs [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) w celu:

- Obsługa śledzenia sesji połączonych z procesem

- Obsługa automatycznego dołączania w wielu aparatach debugowania

  Dostawca portu niestandardowego można zaimplementować ten interfejs, jeśli wybierze.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania

- SDM wywołuje [QueryInterface](/cpp/atl/queryinterface) `IDebugProcess2` na interfejsie w celu uzyskania tego interfejsu.

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 W poniższej tabeli `IDebugProcessEx2`przedstawiono metody .

|Metoda|Opis|
|------------|-----------------|
|[Dołącz](../../../extensibility/debugger/reference/idebugprocessex2-attach.md)|Informuje proces, że sesja jest teraz debugowania procesu.|
|[Odłącz](../../../extensibility/debugger/reference/idebugprocessex2-detach.md)|Informuje proces, że sesja nie jest już debugowanie procesu.|
|[AddImplicitProgramNodes](../../../extensibility/debugger/reference/idebugprocessex2-addimplicitprogramnodes.md)|Dodaje węzły programu dla listy aparatów debugowania.|

## <a name="remarks"></a>Uwagi
 Ten interfejs jest prywatny między modułem SDM a procesem.

## <a name="requirements"></a>Wymagania
 Nagłówek: Portpriv.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
