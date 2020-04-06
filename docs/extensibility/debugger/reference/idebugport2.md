---
title: IDebugPort2 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPort2
helpviewer_keywords:
- IDebugPort2 interface
ms.assetid: 8fd87f05-a950-4d14-b925-98be29d4facc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 62912be9fdfecc98a264a58c9713cc12ccaf28f2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725233"
---
# <a name="idebugport2"></a>IDebugPort2
Ten interfejs reprezentuje port debugowania na komputerze.

## <a name="syntax"></a>Składnia

```
IDebugPort2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Dostawca portu niestandardowego implementuje ten interfejs do reprezentowania portu debugowania na komputerze.

 Jeśli port obsługuje wysyłanie zdarzeń portu, <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> musi również <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> zaimplementować interfejs do obsługi interfejsu, który z kolei zapewnia interfejs [IDebugPortEvents2.](../../../extensibility/debugger/reference/idebugportevents2.md)

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Wywołania [GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md) lub [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) zwracają ten interfejs, reprezentujący żądany port.

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 W poniższej tabeli `IDebugPort2`przedstawiono metody .

|Metoda|Opis|
|------------|-----------------|
|[GetPortName](../../../extensibility/debugger/reference/idebugport2-getportname.md)|Zwraca nazwę portu.|
|[GetPortId](../../../extensibility/debugger/reference/idebugport2-getportid.md)|Zwraca identyfikator portu.|
|[GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)|Zwraca żądanie użyte do utworzenia portu (jeśli jest dostępne).|
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)|Zwraca dostawcę portu dla tego portu.|
|[GetProcess ( GetProcess )](../../../extensibility/debugger/reference/idebugport2-getprocess.md)|Zwraca interfejs do procesu, biorąc pod uwagę identyfikator procesu.|
|[EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md)|Wylicza wszystkie procesy uruchomione na porcie.|

## <a name="remarks"></a>Uwagi
 Port lokalny zapewnia dostęp do wszystkich procesów i programów uruchomionych na komputerze lokalnym. Inne porty mogą reprezentować połączenie kablowe szeregowe z urządzeniem z systemem Windows CE lub połączeniem sieciowym z komputerem innym niż DCOM. Interfejs `IDebugPort2` służy do znajdowania nazwy i identyfikatora portu i wylicza wszystkie procesy uruchomione na porcie. W `IDebugPortEx2` interfejsie realizowane są urządzenia do uruchamiania i końcowania procesów na porcie.

## <a name="requirements"></a>Wymagania
 Nagłówek: msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
