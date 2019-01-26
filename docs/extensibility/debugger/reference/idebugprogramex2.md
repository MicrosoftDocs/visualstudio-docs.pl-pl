---
title: IDebugProgramEx2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProgramEx2
helpviewer_keywords:
- IDebugProgramEx2 interface
ms.assetid: 663359ed-635a-4539-addb-0cc52f19d1bd
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c30be6fb9bd87972c3a3d186acc1fae9568ccc20
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55011965"
---
# <a name="idebugprogramex2"></a>IDebugProgramEx2
Ten interfejs umożliwia sesji debugowania manager (SDM) Dołącz do programu i przełączyć węzeł program skojarzony z programu.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugProgramEx2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Dostawcy niestandardowego portu implementuje ten interfejs na ten sam obiekt jako [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interfejsu, aby umożliwić SDM dołączyć do programu, gdy w tym samym czasie co dostawcy portu śledzić wszystkie sesje dołączony do Program. Dostawca numery portów mogą implementować ten interfejs, jeśli go wybierze.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Wywołania SDM [QueryInterface](/cpp/atl/queryinterface) na `IDebugProgram2` interfejsu, aby uzyskać ten interfejs do śledzenia sesji, które zostały dołączone do programów.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 W poniższej tabeli przedstawiono metody `IDebugProgramEx2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Attach](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)|Dołącza program do sesji.|  
|[GetProgramNode](../../../extensibility/debugger/reference/idebugprogramex2-getprogramnode.md)|Pobiera węzeł program skojarzony z programu.|  
  
## <a name="remarks"></a>Uwagi  
 Ten interfejs jest prywatny między SDM i programem.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Portpriv.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)