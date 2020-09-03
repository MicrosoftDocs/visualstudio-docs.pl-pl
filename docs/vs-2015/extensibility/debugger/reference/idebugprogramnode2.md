---
title: IDebugProgramNode2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramNode2
helpviewer_keywords:
- IDebugProgramNode2 interface
ms.assetid: 80e511d8-9b40-4a85-aa5d-952fa5ee6ae7
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1188f18e4a6f604dfd82991433bc0ffe0a07ad47
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148564"
---
# <a name="idebugprogramnode2"></a>IDebugProgramNode2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ten interfejs reprezentuje program, który może być debugowany.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugProgramNode2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Aparat debugowania (DE) lub niestandardowy dostawca portu implementuje ten interfejs, aby reprezentować program, który może być debugowany. Ten interfejs jest zwykle implementowany dla tego samego obiektu, który implementuje interfejs [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) . Ten interfejs jest zarejestrowany w programie [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] przez wywołanie [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md).  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Wywołaj [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md) , aby zwrócić ten interfejs. Dostawca portu niestandardowego odbiera ten interfejs za pomocą wywołania do [AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). A DE odbiera ten interfejs za pomocą wywołania do [dołączenia](../../../extensibility/debugger/reference/idebugengine2-attach.md).  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych  
 W poniższej tabeli przedstawiono metody `IDebugProgramNode2` .  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetProgramName](../../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)|Pobiera nazwę programu.|  
|[GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)|Pobiera nazwę procesu obsługującego program.|  
|[GetHostPid](../../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)|Pobiera identyfikator procesu systemowego dla procesu obsługującego program.|  
|[GetHostMachineName_V7](../../../extensibility/debugger/reference/idebugprogramnode2-gethostmachinename-v7.md)|Przestarzałe. NIE NALEŻY UŻYWAĆ.|  
|[Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)|Przestarzałe. NIE NALEŻY UŻYWAĆ. Zobacz interfejs [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md) , aby zapoznać się z alternatywnym podejściem.|  
|[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)|Pobiera nazwę i identyfikator nieuruchomionego programu.|  
|[DetachDebugger_V7](../../../extensibility/debugger/reference/idebugprogramnode2-detachdebugger-v7.md)|Przestarzałe. NIE NALEŻY UŻYWAĆ.|  
  
## <a name="remarks"></a>Uwagi  
 Menedżer debugowania sesji (SDM) zwykle wywołuje [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md) , aby uzyskać ten interfejs.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Msdbg. h  
  
 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)   
 [RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)   
 [Klej](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)   
 [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)
