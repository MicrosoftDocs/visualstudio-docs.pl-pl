---
title: FIELD_KIND_EX | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- FIELD_KIND_EX enumeration
ms.assetid: 922c3208-1e94-485f-b70a-3bc96affeff8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f0c13d83f80b311838eca32945462c1f17ca23f4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736877"
---
# <a name="field_kind_ex"></a>FIELD_KIND_EX
Wylicza dodatkowe rodzaje pól, które może zawierać obiekt [IDebugField.](../../../extensibility/debugger/reference/idebugfield.md) To wyliczenie rozszerza wyliczenie [FIELD_KIND.](../../../extensibility/debugger/reference/field-kind.md)

## <a name="syntax"></a>Składnia

```cpp
enum enum_FIELD_KIND_EX
{
    FIELD_KIND_EX_NONE = 0,
    FIELD_TYPE_EX_METHODVAR = 0x1,
    FIELD_TYPE_EX_CLASSVAR = 0x2
};
typedef DWORD FIELD_KIND_EX;
```

```csharp
public enum enum_FIELD_KIND_EX
{
    FIELD_KIND_EX_NONE = 0,
    FIELD_TYPE_EX_METHODVAR = 0x1,
    FIELD_TYPE_EX_CLASSVAR = 0x2
};
```

## <a name="fields"></a>Pola
`FIELD_KIND_EX_NONE`\
Pole nie zawiera typu rozszerzonego.

`FIELD_TYPE_EX_METHODVAR`\
Pole zawiera zmienną metody.

`FIELD_TYPE_EX_CLASSVAR`\
Pole zawiera zmienną klasy.

## <a name="requirements"></a>Wymagania
Nagłówek: Sh.h

Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetExtendedKind](../../../extensibility/debugger/reference/idebugextendedfield-getextendedkind.md)
