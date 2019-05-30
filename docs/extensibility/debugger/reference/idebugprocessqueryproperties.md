---
title: IDebugProcessQueryProperties | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessQueryProperties
ms.assetid: ce29a248-81a0-42c0-99a7-1606e8c548ec
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2ddb98c2d7e63fc27ad1469dfbfc76eaaee38582
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353103"
---
# <a name="idebugprocessqueryproperties"></a>IDebugProcessQueryProperties
Ten interfejs jest implementowany przez interfejs rozszerzenia [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) implementacje. Umożliwia ona implementujący można pobrać informacji na temat środowiska debugowania procesu.

## <a name="syntax"></a>Składnia

```
IDebugProcessQueryProperties: IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Implementuje ten interfejs, aby uzyskać informacje o środowisku wykonawczym debugowania procesu.

## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności
 W poniższej tabeli przedstawiono metody `IDebugProcessQueryProperties`.

|Metoda|Opis|
|------------|-----------------|
|[QueryProperty](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperty.md)|Zapytania dotyczące wartości właściwości.|
|[QueryProperties](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperties.md)|Zapytania dotyczące wartości właściwości.|

## <a name="remarks"></a>Uwagi
 Ten interfejs rzadko jest zaimplementowana.

## <a name="requirements"></a>Wymagania
 Nagłówek: Portpriv.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)