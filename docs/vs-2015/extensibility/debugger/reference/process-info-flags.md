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
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54786448"
---
# <a name="processinfoflags"></a>PROCESS_INFO_FLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

W tym artykule opisano lub określa właściwości procesu.  
  
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
 Wskazuje, że proces jest proces systemowy.  
  
 PIFLAG_DEBUGGER_ATTACHED  
 Wskazuje, że proces jest debugowany przez debuger. Może być [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] debugera, lub może być kilka innych debugera, na przykład WinDbg.  
  
 PIFLAG_PROCESS_STOPPED  
 Wskazuje, że proces zostanie zatrzymany. Prawidłowe tylko wtedy, gdy `PIFLAG_DEBUGGER_ATTACHED` jest także określona. Dostępne w [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] i nowszych.  
  
 PIFLAG_PROCESS_RUNNING  
 Wskazuje, że proces jest uruchomiony. Prawidłowe tylko wtedy, gdy `PIFLAG_DEBUGGER_ATTACHED` jest także określona. Dostępne w [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] i nowszych.  
  
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
