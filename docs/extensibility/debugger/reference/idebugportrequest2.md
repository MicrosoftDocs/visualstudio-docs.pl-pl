---
title: IDebugPortRequest2 | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortRequest2
helpviewer_keywords:
- IDebugPortRequest2 interface
ms.assetid: 556e610d-7c4b-44a8-965a-76a9d02b601a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8e2b78986b997358d7f15c9c8c73bb4bd0f73aaf
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62871483"
---
# <a name="idebugportrequest2"></a>IDebugPortRequest2
Ten interfejs zawiera opis portu. Ten opis jest wykorzystywany Aby dodać port do dostawcy portu.

## <a name="syntax"></a>Składnia

```
IDebugPortRequest2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Program Visual Studio zwykle implementuje ten interfejs, w trakcie pobierania port debugowania z dostawcy portu.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Ten interfejs jest przekazywana do [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) utworzyć portu debugowania. Wywołanie [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md) zwraca ten interfejs reprezentujący żądanie użyty do utworzenia portu w pierwszej kolejności.

## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności
 W poniższej tabeli przedstawiono metody `IDebugPortRequest2`.

|Metoda|Opis|
|------------|-----------------|
|[GetPortName](../../../extensibility/debugger/reference/idebugportrequest2-getportname.md)|Pobiera nazwę portu do utworzenia.|

## <a name="remarks"></a>Uwagi
 Aparat debugowania zazwyczaj nie wchodzi w interakcję z dostawcą portu, a także będą ma być używana dla tego interfejsu.

## <a name="requirements"></a>Wymagania
 Header: msdbg.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
- [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)