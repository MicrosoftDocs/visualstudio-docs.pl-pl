---
title: IDebugCodeContext3 | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugCodeContext3 interface
ms.assetid: 524eb882-0ad5-4bfb-95eb-eb3abb3d0237
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e9ff7ac48c745416dbbed799521048997fba5662
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54956444"
---
# <a name="idebugcodecontext3"></a>IDebugCodeContext3
Rozszerza [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) interfejsu, aby umożliwić pobieranie interfejsy modułu i procesu.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugCodeContext3 : IDebugCodeContext2  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Implementowany przez aparaty debugowania i używane przez [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] debugowanie pakietu.  
  
## <a name="methods"></a>Metody  
 Oprócz metod na `IDebugCodeContext2` interfejsu, ten interfejs implementuje następujące metody:  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetModule](../../../extensibility/debugger/reference/idebugcodecontext3-getmodule.md)|Pobiera odwołanie do interfejsu debugowania modułu.|  
|[GetProcess](../../../extensibility/debugger/reference/idebugcodecontext3-getprocess.md)|Pobiera odwołanie do interfejsu debugowania procesu.|  
  
## <a name="remarks"></a>Uwagi  
 Jest to opcjonalne interfejsu, który zazwyczaj nie muszą być wykonywane.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Msdbg.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll