---
title: PROCESS_INFO_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- PROCESS_INFO_FLAGS
helpviewer_keywords:
- PROCESS_INFO_FLAGS enumeration
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1d3541355da9ea144129e730efe9876b4e6d642f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55009573"
---
# <a name="processinfoflags"></a>PROCESS_INFO_FLAGS

W tym artykule opisano lub określa właściwości procesu.

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

## <a name="members"></a>Elementy członkowskie

PIFLAG_SYSTEM_PROCESS  
Wskazuje, że proces jest proces systemowy.

PIFLAG_DEBUGGER_ATTACHED  
Wskazuje, że proces jest debugowany przez debuger. Może być [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] debugera, lub może być kilka innych debugera, na przykład WinDbg.

PIFLAG_PROCESS_STOPPED  
Wskazuje, że proces zostanie zatrzymany. Prawidłowe tylko wtedy, gdy `PIFLAG_DEBUGGER_ATTACHED` jest także określona. Dostępne w programie Visual Studio 2005 i nowszych wersjach.

PIFLAG_PROCESS_RUNNING  
Wskazuje, że proces jest uruchomiony. Prawidłowe tylko wtedy, gdy `PIFLAG_DEBUGGER_ATTACHED` jest także określona. Dostępne w programie Visual Studio 2005 i nowszych wersjach.

## <a name="remarks"></a>Uwagi

Używany do `Flags` członkiem [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) struktury.

Te flagi mogą być łączone przy użyciu bitowego operatora `OR`.

## <a name="requirements"></a>Wymagania

Header: msdbg.h

Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też

[Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)  
[PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)