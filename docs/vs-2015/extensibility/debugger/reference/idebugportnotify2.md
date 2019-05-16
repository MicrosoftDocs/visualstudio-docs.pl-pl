---
title: IDebugPortNotify2 | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPortNotify2
helpviewer_keywords:
- IDebugPortNotify2 interface
ms.assetid: 43278b79-bf16-4c08-bcf1-6f7f7a17feab
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 18edddd698953bf71febb8f9f2f1bac704205120
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65703926"
---
# <a name="idebugportnotify2"></a>IDebugPortNotify2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ten interfejs rejestry lub wyrejestrowuje program, który może być debugowany przy użyciu portu, na którym jest uruchomiona na.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugPortNotify2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Dostawcy niestandardowego portu implementuje ten interfejs obsługuje dodawanie i usuwanie programów z portu. Jest on zwykle implementowany w ten sam obiekt, który implementuje [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) interfejsu.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Wywołanie [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) na `IDebugPort2` interfejsu zwraca ten interfejs. Ponadto po wywołaniu [GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md) zwraca ten interfejs. Aparat debugowania można zobaczyć ten interfejs jako parametr do [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md).  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 W poniższej tabeli przedstawiono metody `IDebugPortNotify2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)|Rejestruje program, który może być debugowany przy użyciu portu, na którym jest uruchomiona na.|  
|[RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)|Wyrejestrowuje program, który może być debugowany z portu, na którym jest uruchomiona na.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli port debugowania nie ma sposobu określenia, kiedy załadowany lub zwolnione programy, dostawca port niestandardowy, należy zaimplementować ten interfejs. Wszystkie programy, które są ładowane do debugowania za pośrednictwem określonego portu są śledzone za pomocą tego interfejsu.  
  
## <a name="requirements"></a>Wymagania  
 Header: msdbg.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
