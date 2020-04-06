---
title: IDebugPortRequest2 | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724784"
---
# <a name="idebugportrequest2"></a>IDebugPortRequest2
Ten interfejs opisuje port. Ten opis służy do dodawania portu do dostawcy portu.

## <a name="syntax"></a>Składnia

```
IDebugPortRequest2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Visual Studio zazwyczaj implementuje ten interfejs w procesie uzyskiwania portu debugowania od dostawcy portu.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Ten interfejs jest przekazywany do [AddPort,](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) aby utworzyć port debugowania. Wywołanie [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md) zwraca ten interfejs, reprezentujący żądanie używane do utworzenia portu w pierwszej kolejności.

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 W poniższej tabeli `IDebugPortRequest2`przedstawiono metody .

|Metoda|Opis|
|------------|-----------------|
|[GetPortName](../../../extensibility/debugger/reference/idebugportrequest2-getportname.md)|Pobiera nazwę portu do utworzenia.|

## <a name="remarks"></a>Uwagi
 Aparat debugowania zazwyczaj nie wchodzi w interakcję z dostawcą portu i nie będzie miał zastosowania dla tego interfejsu.

## <a name="requirements"></a>Wymagania
 Nagłówek: msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
- [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)
