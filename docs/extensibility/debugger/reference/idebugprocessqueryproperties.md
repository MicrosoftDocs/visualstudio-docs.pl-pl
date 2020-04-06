---
title: Właściwości IDebugProcessQueryProperties | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723282"
---
# <a name="idebugprocessqueryproperties"></a>IDebugProcessQueryProperties
Ten interfejs jest interfejsem rozszerzenia zaimplementowanym przez realizatorów [IDebugProcess2.](../../../extensibility/debugger/reference/idebugprocess2.md) Umożliwia realizatorowi uzyskanie informacji na temat środowiska procesu debugowania.

## <a name="syntax"></a>Składnia

```
IDebugProcessQueryProperties: IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Zaimplementuj ten interfejs, aby uzyskać informacje o środowisku wykonywania procesu debugowania.

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 W poniższej tabeli `IDebugProcessQueryProperties`przedstawiono metody .

|Metoda|Opis|
|------------|-----------------|
|[QueryProperty](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperty.md)|Kwerendy dla wartości właściwości.|
|[QueryProperties](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperties.md)|Kwerendy dotyczące wartości właściwości.|

## <a name="remarks"></a>Uwagi
 Ten interfejs jest rzadko implementowane.

## <a name="requirements"></a>Wymagania
 Nagłówek: Portpriv.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
