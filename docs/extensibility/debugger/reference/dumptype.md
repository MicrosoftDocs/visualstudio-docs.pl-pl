---
title: DUMPTYPE | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DUMPTYPE
helpviewer_keywords:
- DUMPTYPE enumeration
ms.assetid: ea8160db-8732-4056-a1d7-892ef72da71e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7edb3129733aec29bb5eda64d388024bec4d5ece
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66318190"
---
# <a name="dumptype"></a>DUMPTYPE
Określa, ile stanu programu (np. uruchamianie wątków, ramek stosu i bieżący adres instrukcji) zrzutu.

## <a name="syntax"></a>Składnia

```cpp
enum enum_DUMPTYPE {
    DUMP_MINIDUMP = 0,
    DUMP_FULLDUMP = 1
};
typedef DWORD DUMPTYPE;
```

```csharp
public enum enum_DUMPTYPE {
    DUMP_MINIDUMP = 0,
    DUMP_FULLDUMP = 1
};
```

## <a name="fields"></a>Pola
`DUMP_MINIDUMP`\
Określa zrzutu małe, compact.

`DUMP_FULLDUMP`\
Określa duża, pełny zrzut.

## <a name="remarks"></a>Uwagi
Przekazywany jako argument do [WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md) metody.

## <a name="requirements"></a>Wymagania
Header: msdbg.h

Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md)
