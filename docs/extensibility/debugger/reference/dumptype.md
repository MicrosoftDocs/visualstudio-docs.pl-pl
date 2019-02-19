---
title: DUMPTYPE | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- DUMPTYPE
helpviewer_keywords:
- DUMPTYPE enumeration
ms.assetid: ea8160db-8732-4056-a1d7-892ef72da71e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c81d9c9f3f5dc6b0a849e405133b7ecef1e4e59b
ms.sourcegitcommit: 7153e2fc717d32e0e9c8a9b8c406dc4053c9fd53
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2019
ms.locfileid: "56412971"
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

## <a name="members"></a>Elementy członkowskie
DUMP_MINIDUMP  
Określa zrzutu małe, compact.

DUMP_FULLDUMP  
Określa duża, pełny zrzut.

## <a name="remarks"></a>Uwagi
Przekazywany jako argument do [WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md) metody.

## <a name="requirements"></a>Wymagania
Header: msdbg.h

Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
[Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)  
[WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md)
