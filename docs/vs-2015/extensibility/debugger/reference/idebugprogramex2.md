---
title: IDebugProgramEx2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramEx2
helpviewer_keywords:
- IDebugProgramEx2 interface
ms.assetid: 663359ed-635a-4539-addb-0cc52f19d1bd
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2d3abc956d736f5c9273134b41c0fc9c2dc7db62
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65688941"
---
# <a name="idebugprogramex2"></a>IDebugProgramEx2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ten interfejs umożliwia sesji debugowania manager (SDM) Dołącz do programu i przełączyć węzeł program skojarzony z programu.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugProgramEx2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Dostawcy niestandardowego portu implementuje ten interfejs na ten sam obiekt jako [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interfejsu, aby umożliwić SDM dołączyć do programu, gdy w tym samym czasie co dostawcy portu śledzić wszystkie sesje dołączony do Program. Dostawca numery portów mogą implementować ten interfejs, jeśli go wybierze.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Wywołania SDM [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) na `IDebugProgram2` interfejsu, aby uzyskać ten interfejs do śledzenia sesji, które zostały dołączone do programów.  
  
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
