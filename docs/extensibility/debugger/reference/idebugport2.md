---
description: Ten interfejs reprezentuje port debugowania na komputerze.
title: IDebugPort2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPort2
helpviewer_keywords:
- IDebugPort2 interface
ms.assetid: 8fd87f05-a950-4d14-b925-98be29d4facc
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f78db8ba9a29b40d111dc5a82827395b100302b5
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102169486"
---
# <a name="idebugport2"></a>IDebugPort2
Ten interfejs reprezentuje port debugowania na komputerze.

## <a name="syntax"></a>Składnia

```
IDebugPort2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Dostawca portu niestandardowego implementuje ten interfejs, aby reprezentować port debugowania na komputerze.

 Jeśli port obsługuje wysyłanie zdarzeń portów, musi również zaimplementować <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> interfejs do obsługi <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> interfejsu, który z kolei udostępnia interfejs [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) .

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Wywołania metody [GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md) lub [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) zwracają ten interfejs reprezentujący żądany port.

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 W poniższej tabeli przedstawiono metody `IDebugPort2` .

|Metoda|Opis|
|------------|-----------------|
|[GetPortName](../../../extensibility/debugger/reference/idebugport2-getportname.md)|Zwraca nazwę portu.|
|[GetPortId](../../../extensibility/debugger/reference/idebugport2-getportid.md)|Zwraca identyfikator portu.|
|[GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)|Zwraca żądanie użyte do utworzenia portu (jeśli jest dostępne).|
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)|Zwraca dostawcę portu dla tego portu.|
|[GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)|Zwraca interfejs do procesu, w którym znajduje się identyfikator procesu.|
|[EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md)|Wylicza wszystkie procesy działające na porcie.|

## <a name="remarks"></a>Uwagi
 Port lokalny zapewnia dostęp do wszystkich procesów i programów uruchomionych na komputerze lokalnym. Inne porty mogą reprezentować połączenie kablowe z urządzeniem opartym na Windows CE lub połączenie sieciowe z komputerem innym niż DCOM. `IDebugPort2`Interfejs jest używany do znajdowania nazwy i identyfikatora portu i wyliczania wszystkich procesów uruchomionych na porcie. Urządzenia do uruchamiania i kończenia procesów na porcie są zaimplementowane w `IDebugPortEx2` interfejsie.

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
