---
title: BP_LOCATION_CODE_ADDRESS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- BP_LOCATION_CODE_ADDRESS
helpviewer_keywords:
- BP_LOCATION_CODE_ADDRESS structure
ms.assetid: 83c9da8b-19d9-4be5-b225-854543654901
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e90801f17690b48ba82e9fa80fba345e206c50b2
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2019
ms.locfileid: "56315927"
---
# <a name="bplocationcodeaddress"></a>BP_LOCATION_CODE_ADDRESS
W tym artykule opisano lokalizacji punktu przerwania pod adresem w kodzie.

## <a name="syntax"></a>Składnia

```cpp
typedef struct _BP_LOCATION_CODE_ADDRESS {
    BSTR bstrContext;
    BSTR bstrModuleUrl;
    BSTR bstrFunction;
    BSTR bstrAddress;
} BP_LOCATION_CODE_ADDRESS;
```

## <a name="members"></a>Elementy członkowskie
`bstrContext`  
Kontekst punktu przerwania, zazwyczaj nazwę metody lub funkcji wyświetlanego w stosie wywołań.

`bstrModuleUrl`  
Adres URL moduł, który zawiera punkt przerwania.

`bstrFunction`  
Nazwa funkcji, która zawiera punkt przerwania.

`bstrAddress`  
Adres punktu przerwania, który jest analizowany przez ewaluatora wyrażeń, aby powiązać [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) obiektu.

## <a name="remarks"></a>Uwagi
Ta struktura jest elementem członkowskim [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) struktur w ramach złożenia.

## <a name="requirements"></a>Wymagania
Header: msdbg.h

Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
[Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)  
[BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)  
[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
