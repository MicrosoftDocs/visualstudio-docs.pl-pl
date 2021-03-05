---
description: Opisuje lub określa właściwości procesu.
title: PROCESS_INFO_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROCESS_INFO_FLAGS
helpviewer_keywords:
- PROCESS_INFO_FLAGS enumeration
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e192a51c2c371754778ecbe697d280d1b254f224
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102225334"
---
# <a name="process_info_flags"></a>PROCESS_INFO_FLAGS

Opisuje lub określa właściwości procesu.

## <a name="syntax"></a>Składnia

```cpp
enum enum_PROCESS_INFO_FLAGS { 
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,
   PIFLAG_PROCESS_STOPPED   = 0x00000004,
   PIFLAG_PROCESS_RUNNING   = 0x00000008,
};
typedef DWORD PROCESS_INFO_FLAGS;
```

```csharp
enum enum_PROCESS_INFO_FLAGS { 
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,
   PIFLAG_PROCESS_STOPPED   = 0x00000004,
   PIFLAG_PROCESS_RUNNING   = 0x00000008,
};
```

## <a name="fields"></a>Pola

`PIFLAG_SYSTEM_PROCESS`\
Wskazuje, że proces jest procesem systemowym.

`PIFLAG_DEBUGGER_ATTACHED`\
Wskazuje, że proces jest debugowany przez debuger. Może być [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] debugerem lub może być innym debugerem, na przykład WinDbg.

`PIFLAG_PROCESS_STOPPED`\
Wskazuje, że proces jest zatrzymany. Prawidłowy tylko wtedy, gdy `PIFLAG_DEBUGGER_ATTACHED` jest również określony. Dostępne w programie Visual Studio 2005 i nowszych.

`PIFLAG_PROCESS_RUNNING`\
Wskazuje, że proces jest uruchomiony. Prawidłowy tylko wtedy, gdy `PIFLAG_DEBUGGER_ATTACHED` jest również określony. Dostępne w programie Visual Studio 2005 i nowszych.

## <a name="remarks"></a>Uwagi

Używane dla `Flags` elementu członkowskiego struktury [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) .

Flagi te mogą być połączone z bitową `OR` .

## <a name="requirements"></a>Wymagania

Nagłówek: Msdbg. h

Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też

- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)
