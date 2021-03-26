---
description: Zapewnia obsługę dostawcy portów w celu wyboru i współpracy z serwerem podstawowym.
title: IDebugPortSupplierEx2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortSupplierEx2 interface
ms.assetid: dae0050a-a50a-4f35-bfbd-e538f537b20f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c2020f3efe2bd7562640fd44e45a10c9a3a6c767
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105071847"
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
