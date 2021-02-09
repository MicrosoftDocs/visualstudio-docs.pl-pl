---
title: IDebugProcessEx2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2
helpviewer_keywords:
- IDebugProcessEx2 interface
ms.assetid: 44e309ba-1d6f-499b-aa7e-9b34858a6d57
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9e8966be5c30bf2061fc1e03be6798279afbe8ac
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99900172"
---
# <a name="idebugprocessex2"></a>IDebugProcessEx2
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

- Model SDM wywołuje metodę [QueryInterface](/cpp/atl/queryinterface) w `IDebugProcess2` interfejsie, aby uzyskać ten interfejs.

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
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
