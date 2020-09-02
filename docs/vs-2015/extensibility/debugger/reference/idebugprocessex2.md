---
title: IDebugProcessEx2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProcessEx2
helpviewer_keywords:
- IDebugProcessEx2 interface
ms.assetid: 44e309ba-1d6f-499b-aa7e-9b34858a6d57
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d2b036bd68aca126675f26b9823d2c786a0ae652
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65675327"
---
# <a name="idebugprocessex2"></a>IDebugProcessEx2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ten interfejs umożliwia menedżerowi debugowania sesji powiadamianie procesu, który jest dołączany lub odłączany od procesu.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugProcessEx2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Niestandardowy dostawca portu implementuje ten interfejs na tym samym obiekcie co Interfejs [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) , aby:  
  
- Obsługa śledzenia sesji połączonych z procesem  
  
- Obsługa automatyczne dołączanie wielu aparatów debugowania  
  
  Dostawca portu niestandardowego może zaimplementować ten interfejs, jeśli zostanie wybrany.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
  
- Model SDM wywołuje metodę [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) w `IDebugProcess2` interfejsie, aby uzyskać ten interfejs.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych  
 W poniższej tabeli przedstawiono metody `IDebugProcessEx2` .  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Dołącz](../../../extensibility/debugger/reference/idebugprocessex2-attach.md)|Informuje proces, że sesja teraz debuguje proces.|  
|[Odłącz](../../../extensibility/debugger/reference/idebugprocessex2-detach.md)|Informuje proces, że sesja nie jest już debugowana.|  
|[AddImplicitProgramNodes](../../../extensibility/debugger/reference/idebugprocessex2-addimplicitprogramnodes.md)|Dodaje węzły programu do listy aparatów debugowania.|  
  
## <a name="remarks"></a>Uwagi  
 Ten interfejs jest prywatny między modelem SDM a procesem.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Portpriv. h  
  
 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
