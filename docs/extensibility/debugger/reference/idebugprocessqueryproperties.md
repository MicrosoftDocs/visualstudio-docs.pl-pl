---
title: IDebugProcessQueryProperties | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessQueryProperties
ms.assetid: ce29a248-81a0-42c0-99a7-1606e8c548ec
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e54c51e4012bf129e7f8a8ad44fac8dca3e888c1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62917518"
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

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)