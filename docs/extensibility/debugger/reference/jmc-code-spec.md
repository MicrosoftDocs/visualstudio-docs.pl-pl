---
description: Ta struktura służy do ustawiania informacji JustMyCode dla modułu.
title: JMC_CODE_SPEC | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- JMC_CODE_SPEC
helpviewer_keywords:
- JMC_CODE_SPEC structure
ms.assetid: d89498f1-4234-46d9-b4e2-abbcbca5068a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d9bb05d55268d3f0ef497831616b8e27aae4bb86
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105058082"
---
# <a name="jmc_code_spec"></a>JMC_CODE_SPEC
Ta struktura służy do ustawiania informacji JustMyCode dla modułu.

## <a name="syntax"></a>Składnia

```cpp
typedef struct _JMC_CODE_SPEC {
    BOOL fIsUserCode;
    BSTR bstrModuleName;
} JMC_CODE_SPEC;
```

```csharp
public struct JMC_CODE_SPEC {
    public int    fIsUserCode;
    public string bstrModuleName;
};
```

## <a name="members"></a>Elementy członkowskie
`fIsUserCode`\
Wartość niezerowa ( `TRUE` ), jeśli moduł ma być uznawany za kod użytkownika; w przeciwnym razie, zero ( `FALSE` ), jeśli moduł ma być traktowany jako kod zewnętrzny i nie powinien być debugowany.

`bstrModuleName`\
Nazwa danego modułu.

## <a name="remarks"></a>Uwagi
Ta struktura jest przenoszona jako lista takich struktur do metody [SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md) .

## <a name="requirements"></a>Wymagania
Nagłówek: Msdbg. h

Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md)
