---
title: IDebugPortRequest2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortRequest2
helpviewer_keywords:
- IDebugPortRequest2 interface
ms.assetid: 556e610d-7c4b-44a8-965a-76a9d02b601a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 163718fda344ba5f3f44ef630b4eba3e5613dc61
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80724784"
---
# <a name="idebugportrequest2"></a>IDebugPortRequest2
Ten interfejs opisuje port. Ten opis służy do dodawania portu do dostawcy portów.

## <a name="syntax"></a>Składnia

```
IDebugPortRequest2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Program Visual Studio zwykle implementuje ten interfejs w procesie uzyskiwania portu debugowania od dostawcy portów.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Ten interfejs jest przesyłany do [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) w celu utworzenia portu debugowania. Wywołanie [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md) zwraca ten interfejs reprezentujący żądanie użyte do utworzenia portu w pierwszym miejscu.

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 W poniższej tabeli przedstawiono metody `IDebugPortRequest2` .

|Metoda|Opis|
|------------|-----------------|
|[GetPortName](../../../extensibility/debugger/reference/idebugportrequest2-getportname.md)|Pobiera nazwę portu do utworzenia.|

## <a name="remarks"></a>Uwagi
 Aparat debugowania zwykle nie współdziała z dostawcą portu i nie będzie miał zastosowania do tego interfejsu.

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
- [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)
