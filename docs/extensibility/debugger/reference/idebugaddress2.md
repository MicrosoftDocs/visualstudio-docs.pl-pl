---
title: IDebugAddress2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress2
helpviewer_keywords:
- IDebugAddress2 interface
ms.assetid: b150e0ed-4ac0-4f8c-9732-4b3e54b9d243
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 66fd149bc3eed7633586c156f6493c8febcbeaac
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66330362"
---
# <a name="idebugaddress2"></a>IDebugAddress2
Ten interfejs zapewnia dostęp do Identyfikatora procesu, który jest właścicielem obiektu, którego adres jest reprezentowany przez ten interfejs.

## <a name="syntax"></a>Składnia

```
IDebugAddress2 : IDebugAddress
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Dostawca symboli implementuje ten interfejs dla tego samego obiektu, który implementuje [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interfejsu. Ten interfejs zapewnia dostęp do Identyfikatora procesu, który jest właścicielem obiektu, który jest powiązany z tym adresem.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Użyj [QueryInterface](/cpp/atl/queryinterface) uzyskać ten interfejs z [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interfejsu.

## <a name="methods-in-vtable-order"></a>Metody w vtable kolejności
 Oprócz metod odziedziczone [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interfejsu, ten interfejs implementuje następującą metodę:

|Metoda|Opis|
|------------|-----------------|
|[GetProcessID](../../../extensibility/debugger/reference/idebugaddress2-getprocessid.md)|Pobiera identyfikator procesu, który jest właścicielem obiektu reprezentowanego przez ten interfejs.|

## <a name="requirements"></a>Wymagania
 Nagłówek: sh.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)