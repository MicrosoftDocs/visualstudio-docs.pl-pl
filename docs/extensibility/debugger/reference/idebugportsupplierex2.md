---
title: IDebugPortSupplierEx2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortSupplierEx2 interface
ms.assetid: dae0050a-a50a-4f35-bfbd-e538f537b20f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 26387618b320ed56ce754e64698fbb1c4223f2f6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80724324"
---
# <a name="idebugportsupplierex2"></a>IDebugPortSupplierEx2
Zapewnia obsługę dostawcy portów w celu wyboru i współpracy z serwerem podstawowym.

## <a name="syntax"></a>Składnia

```
IDebugPortSupplierEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Niestandardowy dostawca portu implementuje ten interfejs, aby można było wybrać serwer podstawowy do użycia.

## <a name="methods"></a>Metody
 W poniższej tabeli przedstawiono metody **IDebugPortSupplierEx2**.

|Metoda|Opis|
|------------|-----------------|
|[SetServer](../../../extensibility/debugger/reference/idebugportsupplierex2-setserver.md)|Ustawia serwer podstawowy dla dostawcy portów.|

## <a name="requirements"></a>Wymagania
 Nagłówek: Portpriv. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)
