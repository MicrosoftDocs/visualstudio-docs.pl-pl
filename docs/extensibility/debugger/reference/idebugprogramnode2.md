---
title: IDebugProgramNode2 | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2
helpviewer_keywords:
- IDebugProgramNode2 interface
ms.assetid: 80e511d8-9b40-4a85-aa5d-952fa5ee6ae7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 51f49ca90837cf80c22856ae2e8f89a98da43d86
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62869966"
---
# <a name="idebugprogramnode2"></a>IDebugProgramNode2
Ten interfejs reprezentuje program, który może być debugowany.

## <a name="syntax"></a>Składnia

```
IDebugProgramNode2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Aparat debugowania (DE) lub dostawcy niestandardowego portu implementuje ten interfejs do reprezentowania program, który może być debugowany. Ten interfejs jest zwykle implementowany w ten sam obiekt, który implementuje [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interfejsu. Ten interfejs jest zarejestrowane w usłudze [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] przez wywołanie metody [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md).

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Wywołaj [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md) do zwrócenia tego interfejsu. Dostawcy niestandardowego portu otrzyma ten interfejs, za pomocą wywołania [AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). DE otrzyma ten interfejs, za pomocą wywołania [Dołącz](../../../extensibility/debugger/reference/idebugengine2-attach.md).

## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności
 W poniższej tabeli przedstawiono metody `IDebugProgramNode2`.

|Metoda|Opis|
|------------|-----------------|
|[GetProgramName](../../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)|Pobiera nazwę programu.|
|[GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)|Pobiera nazwę procesu hostingu programu.|
|[GetHostPid](../../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)|Pobiera identyfikator procesu systemu dla procesu hostingu programu.|
|[GetHostMachineName_V7](../../../extensibility/debugger/reference/idebugprogramnode2-gethostmachinename-v7.md)|PRZESTARZAŁE. NIE NALEŻY UŻYWAĆ.|
|[Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)|PRZESTARZAŁE. NIE NALEŻY UŻYWAĆ. Zobacz [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md) interfejs alternatywnym podejściem.|
|[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)|Pobiera nazwę i identyfikator DE program został uruchomiony.|
|[DetachDebugger_V7](../../../extensibility/debugger/reference/idebugprogramnode2-detachdebugger-v7.md)|PRZESTARZAŁE. NIE NALEŻY UŻYWAĆ.|

## <a name="remarks"></a>Uwagi
 Menedżer debugowania sesji (SDM) zwykle wywołuje [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md) uzyskać ten interfejs.

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
- [RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)
- [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)
- [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)