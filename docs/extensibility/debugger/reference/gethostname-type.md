---
title: GETHOSTNAME_TYPE | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- GETHOSTNAME_TYPE
helpviewer_keywords:
- GETHOSTNAME_TYPE enumeration
ms.assetid: 2be92bea-8133-412b-9015-1833baf16e1b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5a7da1486f0edf52f3f0d96db699f60f24e36827
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736772"
---
# <a name="gethostname_type"></a>GETHOSTNAME_TYPE
Określa typ nazwy hosta.

## <a name="syntax"></a>Składnia

```cpp
enum enum_GETHOSTNAME_TYPE {
    GHN_FRIENDLY_NAME = 0,
    GHN_FILE_NAME     = 1
};
typedef DWORD GETHOSTNAME_TYPE;
```

```csharp
public enum enum_GETHOSTNAME_TYPE {
    GHN_FRIENDLY_NAME = 0,
    GHN_FILE_NAME     = 1
};
```

## <a name="fields"></a>Pola
`GHN_FRIENDLY_NAME`\
Określa przyjazną nazwę hosta.

`GHN_FILE_NAME`\
Określa nazwę pliku hosta.

## <a name="remarks"></a>Uwagi
Te wartości są przekazywane jako argument do [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md) metody, aby pobrać nazwę hosta w różnych formatach.

## <a name="requirements"></a>Wymagania
Nagłówek: msdbg.h

Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)
