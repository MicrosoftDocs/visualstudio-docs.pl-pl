---
title: IDebugPortSupplierEx2 | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortSupplierEx2 interface
ms.assetid: dae0050a-a50a-4f35-bfbd-e538f537b20f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3bebf232e17df54d4dae2392a40f2ccbc3fc711c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353317"
---
# <a name="idebugportsupplierex2"></a>IDebugPortSupplierEx2
Zapewnia obsługę dostawcy portu wybrać i interakcyjnie z instalacją server core.

## <a name="syntax"></a>Składnia

```
IDebugPortSupplierEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Dostawcy niestandardowego portu implementuje ten interfejs, tak, aby go wybrać serwer podstawowy do użycia.

## <a name="methods"></a>Metody
 W poniższej tabeli przedstawiono metody **IDebugPortSupplierEx2**.

|Metoda|Opis|
|------------|-----------------|
|[SetServer](../../../extensibility/debugger/reference/idebugportsupplierex2-setserver.md)|Ustawia core server dla dostawcy portu.|

## <a name="requirements"></a>Wymagania
 Nagłówek: Portpriv.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)