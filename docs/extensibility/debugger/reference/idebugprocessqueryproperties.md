---
description: Ten interfejs jest interfejsem rozszerzenia implementowanym przez implementacje IDebugProcess2.
title: IDebugProcessQueryProperties | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessQueryProperties
ms.assetid: ce29a248-81a0-42c0-99a7-1606e8c548ec
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8205b96723a1b48da46e6e19162c50139c9fe71d
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166219"
---
# <a name="idebugprocessqueryproperties"></a>IDebugProcessQueryProperties
Ten interfejs jest interfejsem rozszerzenia implementowanym przez implementacje [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) . Umożliwia ona programowi implementującemu pobieranie informacji o środowisku procesu debugowania.

## <a name="syntax"></a>Składnia

```
IDebugProcessQueryProperties: IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Zaimplementuj ten interfejs, aby uzyskać informacje o środowisku wykonywania procesu debugowania.

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 W poniższej tabeli przedstawiono metody `IDebugProcessQueryProperties` .

|Metoda|Opis|
|------------|-----------------|
|[QueryProperty](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperty.md)|Wykonuje zapytania dotyczące wartości właściwości.|
|[QueryProperties](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperties.md)|Zapytania dotyczące wartości właściwości.|

## <a name="remarks"></a>Uwagi
 Ten interfejs jest rzadko zaimplementowany.

## <a name="requirements"></a>Wymagania
 Nagłówek: Portpriv. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
