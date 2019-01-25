---
title: IEnumDebugPorts2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugPorts2
helpviewer_keywords:
- IEnumDebugPorts2
ms.assetid: 1754eef3-cf62-42e0-b218-1911acba77d4
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c30e42592af4d34765951b5e229555556c9b57b3
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54786253"
---
# <a name="ienumdebugports2"></a>IEnumDebugPorts2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ten interfejs wylicza porty dostawcy maszynowo lub port.  
  
## <a name="syntax"></a>Składnia  
  
```  
IEnumDebugPorts2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Dostawcy niestandardowego portu implementuje ten interfejs reprezentujący listę portów tworzone przez dostawcę. Program Visual Studio implementuje ten interfejs, w odniesieniu do własnego dostawcy portu.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Wywołaj [EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) uzyskać ten interfejs reprezentujący listę portów tworzone przez dostawcę portu. Wywołaj [EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md) uzyskać ten interfejs reprezentujący listę portów, które zostały zapisane na dysku.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 W poniższej tabeli przedstawiono metody `IEnumDebugPorts2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Next](../../../extensibility/debugger/reference/ienumdebugports2-next.md)|Pobiera określoną liczbę portów w kolejności wyliczenia.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugports2-skip.md)|Pomija określoną liczbę portów w kolejności wyliczenia.|  
|[Reset](../../../extensibility/debugger/reference/ienumdebugports2-reset.md)|Resetuje sekwencji wyliczenia na początku.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugports2-clone.md)|Tworzy moduł wyliczający, który zawiera ten sam stan wyliczenia jako bieżącego modułu wyliczającego.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugports2-getcount.md)|Pobiera liczbę portów w moduł wyliczający.|  
  
## <a name="remarks"></a>Uwagi  
 Program Visual Studio używa tego interfejsu, aby pomóc, wypełnić listę portów używanych do dołączanie do procesu.  
  
 Aparat debugowania zwykle nie korzysta z tego interfejsu.  
  
## <a name="requirements"></a>Wymagania  
 Header: msdbg.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)   
 [EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)
