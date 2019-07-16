---
title: IDebugMemoryContext2 | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2
helpviewer_keywords:
- IDebugMemoryContext2 interface
ms.assetid: 3a544c8b-11dc-46bb-8549-261e4ac5bbc4
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6f5a0533e2f7ce50dce7ccdf1285e4ab28a4b7a4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68146354"
---
# <a name="idebugmemorycontext2"></a>IDebugMemoryContext2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ten interfejs reprezentuje pozycję w przestrzeni adresowej maszyny z uruchomionym programem debugowanego programu.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugMemoryContext2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Aparat debugowania (DE) implementuje ten interfejs reprezentujący adres w pamięci.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Wywołanie [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) lub [GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md) zwraca ten interfejs. Ponadto wywołania [Dodaj](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md) i [Subtract](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md) zwracają nowe kopie tego interfejsu, po zastosowaniu odpowiednich operacji arytmetycznej.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 W poniższej tabeli przedstawiono metody `IDebugMemoryContext2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetName](../../../extensibility/debugger/reference/idebugmemorycontext2-getname.md)|Pobiera nazwę użytkownika zawiera dla tego kontekstu.|  
|[GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)|Pobiera informacje z opisem w tym kontekście.|  
|[Add](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md)|Dodaje określoną wartość do adresu bieżącego kontekstu, aby utworzyć nowy kontekst.|  
|[Subtract](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md)|Odejmuje określoną wartość z bieżącego kontekstu adres, aby utworzyć nowy kontekst.|  
|[Compare](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)|Porównuje dwa konteksty w sposób wskazany przez porównanie flag.|  
  
## <a name="remarks"></a>Uwagi  
 Visual Studio **pamięci** wywołania okna [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) uzyskać `IDebugMemoryContext2` interfejsu, który zawiera obliczane wyrażenie używane dla adresu pamięci. Ten kontekst jest następnie przekazywany do [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md) i [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md) do określenia adresu do odczytu lub zapisu.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)   
 [GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)   
 [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)   
 [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)
