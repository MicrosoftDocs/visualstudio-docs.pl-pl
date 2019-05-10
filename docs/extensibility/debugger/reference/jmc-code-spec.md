---
title: JMC_CODE_SPEC | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- JMC_CODE_SPEC
helpviewer_keywords:
- JMC_CODE_SPEC structure
ms.assetid: d89498f1-4234-46d9-b4e2-abbcbca5068a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4fe0a804922296e26846b9b477091883c742253e
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/09/2019
ms.locfileid: "65458080"
---
# <a name="jmccodespec"></a>JMC_CODE_SPEC
Ta struktura jest używana do ustawiania informacji JustMyCode dla modułu.

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
Niezerowa Koniunkcja (`TRUE`) Jeśli moduł jest uważane za kod użytkownika; w przeciwnym razie wartość zero (`FALSE`) Jeśli moduł jest traktowane jako kod zewnętrzny, a nie można debugować.

`bstrModuleName`\
Nazwa w danym module.

## <a name="remarks"></a>Uwagi
Ta struktura jest przekazywany jako listę takich struktur [SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md) metody.

## <a name="requirements"></a>Wymagania
Header: msdbg.h

Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md)
