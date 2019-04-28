---
title: IDebugPort2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPort2
helpviewer_keywords:
- IDebugPort2 interface
ms.assetid: 8fd87f05-a950-4d14-b925-98be29d4facc
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 14c21b4f1546b262fb61c0da3ea95adee2aef8fa
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62918285"
---
# <a name="idebugport2"></a>IDebugPort2
Ten interfejs reprezentuje port debugowania na komputerze.

## <a name="syntax"></a>Składnia

```
IDebugPort2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Dostawcy niestandardowego portu implementuje ten interfejs do reprezentowania port debugowania na komputerze.

 Jeśli port obsługuje wysyłanie zdarzeń do portu, musi implementować też <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> obsługiwany przez interfejs <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> interfejs, który z kolei udostępnia [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) interfejsu.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Wywołania [GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md) lub [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) zwraca ten interfejs reprezentujący żądanym porcie.

## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności
 W poniższej tabeli przedstawiono metody `IDebugPort2`.

|Metoda|Opis|
|------------|-----------------|
|[GetPortName](../../../extensibility/debugger/reference/idebugport2-getportname.md)|Zwraca nazwę portu.|
|[GetPortId](../../../extensibility/debugger/reference/idebugport2-getportid.md)|Zwraca identyfikator portu.|
|[GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)|Zwraca żądanie użyty do utworzenia portu (jeśli jest dostępny).|
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)|Zwraca dostawcy portu dla tego portu.|
|[GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)|Zwraca interfejs do procesu, który został podany identyfikator procesu.|
|[EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md)|Wylicza wszystkie procesy, które są uruchomione na porcie.|

## <a name="remarks"></a>Uwagi
 Port lokalny zapewnia dostęp do wszystkich procesów i programy uruchomione na komputerze lokalnym. Inne porty może reprezentować połączenia kabel szeregowy do urządzenia z systemem Windows CE lub połączenie sieciowe z komputerem bez modelu DCOM. `IDebugPort2` Interfejs służy do znajdowania nazwy i identyfikatora portu i wyliczyć wszystkie procesy uruchomione na porcie. Funkcje służące do uruchamiania i zakończenie procesów na porcie są implementowane w `IDebugPortEx2` interfejsu.

## <a name="requirements"></a>Wymagania
 Header: msdbg.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)