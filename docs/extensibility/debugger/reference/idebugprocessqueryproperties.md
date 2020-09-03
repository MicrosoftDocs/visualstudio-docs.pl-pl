---
title: IDebugProcessQueryProperties | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessQueryProperties
ms.assetid: ce29a248-81a0-42c0-99a7-1606e8c548ec
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 08abf401b4e8f0e7a33d882e8178d77e6f248318
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80723282"
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
