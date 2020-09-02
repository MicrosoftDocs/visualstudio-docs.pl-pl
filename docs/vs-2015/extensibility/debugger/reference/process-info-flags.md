---
title: PROCESS_INFO_FLAGS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- PROCESS_INFO_FLAGS
helpviewer_keywords:
- PROCESS_INFO_FLAGS enumeration
ms.assetid: 696951ce-701a-40c2-ac8c-b897f3aae6e2
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 88ff2a1da1f937fd4011932979bd95057eb40dfd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205057"
---
# <a name="process_info_flags"></a>PROCESS_INFO_FLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Opisuje lub określa właściwości procesu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
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
 Wskazuje, że proces jest procesem systemowym.  
  
 PIFLAG_DEBUGGER_ATTACHED  
 Wskazuje, że proces jest debugowany przez debuger. Może być [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] debugerem lub może być innym debugerem, na przykład WinDbg.  
  
 PIFLAG_PROCESS_STOPPED  
 Wskazuje, że proces jest zatrzymany. Prawidłowy tylko wtedy, gdy `PIFLAG_DEBUGGER_ATTACHED` jest również określony. Dostępne w [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] i nowszych wersjach.  
  
 PIFLAG_PROCESS_RUNNING  
 Wskazuje, że proces jest uruchomiony. Prawidłowy tylko wtedy, gdy `PIFLAG_DEBUGGER_ATTACHED` jest również określony. Dostępne w [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] i nowszych wersjach.  
  
## <a name="remarks"></a>Uwagi  
 Używane dla `Flags` elementu członkowskiego struktury [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) .  
  
 Flagi te mogą być połączone z bitową `OR` .  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Msdbg. h  
  
 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)
