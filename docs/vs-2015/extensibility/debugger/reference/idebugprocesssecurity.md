---
title: IDebugProcessSecurity | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity interface
ms.assetid: 8a52ddca-bd99-49c0-9778-469dce7abd44
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 836b971963587aa89440c6e023ee255612d2a087
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187948"
---
# <a name="idebugprocesssecurity"></a>IDebugProcessSecurity
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

`IDebugProcessSecurity` Program jest implementowany przez dostawcę portu w celu ostrzeżenia użytkownika, który dołączany do procesu jest niebezpieczny.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugProcessSecurity : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych  
 W poniższej tabeli przedstawiono metody `IDebugProcessSecurity` .  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetUserName](../../../extensibility/debugger/reference/idebugprocesssecurity-getusername.md)|Pobiera nazwę użytkownika z dostawcy portów.|  
|[QueryCanSafelyAttach](../../../extensibility/debugger/reference/idebugprocesssecurity-querycansafelyattach.md)|Ostrzega użytkownika, który dołączany do procesu debugowania jest niebezpieczny.|  
  
## <a name="remarks"></a>Uwagi  
 Zaimplementuj ten interfejs, aby wyświetlić ostrzeżenie i zezwolić użytkownikowi na anulowanie, jeśli proces, do którego chcesz dołączyć, może być traktowany jako niebezpieczny.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Msdbg. h  
  
 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Np](../../../extensibility/debugger/ports.md)   
 [Dostawcy portów](../../../extensibility/debugger/port-suppliers.md)   
 [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
