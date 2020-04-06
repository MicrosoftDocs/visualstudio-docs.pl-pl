---
title: PROCESS_INFO_FLAGS | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROCESS_INFO_FLAGS
helpviewer_keywords:
- PROCESS_INFO_FLAGS enumeration
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 36c4cbbe17a109eacd69b76500e8c10d21d2d554
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713962"
---
# <a name="process_info_flags"></a>PROCESS_INFO_FLAGS

Opisuje lub określa właściwości procesu.

## <a name="syntax"></a>Składnia

```cpp
enum enum_PROCESS_INFO_FLAGS { 
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,
   PIFLAG_PROCESS_STOPPED   = 0x00000004,
   PIFLAG_PROCESS_RUNNING   = 0x00000008,
};
typedef DWORD PROCESS_INFO_FLAGS;
```

```csharp
enum enum_PROCESS_INFO_FLAGS { 
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
Wskazuje, że proces jest debugowany przez debugera. Może to [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] być debuger lub może to być inny debuger, na przykład WinDbg.

`PIFLAG_PROCESS_STOPPED`\
Wskazuje, że proces został zatrzymany. Prawidłowy `PIFLAG_DEBUGGER_ATTACHED` tylko wtedy, gdy jest również określony. Dostępne w programie Visual Studio 2005 i nowszych.

`PIFLAG_PROCESS_RUNNING`\
Wskazuje, że proces jest uruchomiony. Prawidłowy `PIFLAG_DEBUGGER_ATTACHED` tylko wtedy, gdy jest również określony. Dostępne w programie Visual Studio 2005 i nowszych.

## <a name="remarks"></a>Uwagi

Używany dla `Flags` członka struktury [PROCESS_INFO.](../../../extensibility/debugger/reference/process-info.md)

Flagi te mogą być łączone z bitowym `OR`.

## <a name="requirements"></a>Wymagania

Nagłówek: msdbg.h

Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też

- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)
