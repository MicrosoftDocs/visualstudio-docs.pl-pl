---
title: SEEK_START | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SEEK_START
helpviewer_keywords:
- SEEK_START enumeration
ms.assetid: 55bd8901-626e-428b-a263-23b14417f4c6
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: de4aa0214ab97c330ddfb689076a2c378c4d227a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66329309"
---
# <a name="seekstart"></a>SEEK_START
Określa położenie, z którym ma zostać rozpoczęte wyszukiwanie w strumieniu dezasemblacji.

## <a name="syntax"></a>Składnia

```cpp
enum enum_SEEK_START { 
   SEEK_START_BEGIN       = 0x0001,
   SEEK_START_END         = 0x0002,
   SEEK_START_CURRENT     = 0x0003,
   SEEK_START_CODECONTEXT = 0x0004,
   SEEK_START_CODELOCID   = 0x0005
};
typedef DWORD SEEK_START;
```

```csharp
public enum enum_SEEK_START { 
   SEEK_START_BEGIN       = 0x0001,
   SEEK_START_END         = 0x0002,
   SEEK_START_CURRENT     = 0x0003,
   SEEK_START_CODECONTEXT = 0x0004,
   SEEK_START_CODELOCID   = 0x0005
};
```

## <a name="fields"></a>Pola
 `SEEK_START_BEGIN`\
 Rozpoczyna się wyszukiwanie od początku bieżącego dokumentu.

 `SEEK_START_END`\
 Rozpoczyna się wyszukiwanie na koniec bieżącego dokumentu.

 `SEEK_START_CURRENT`\
 Rozpoczyna się wyszukiwanie w bieżącym położeniu bieżącego dokumentu.

 `SEEK_START_CODECONTEXT`\
 Rozpoczyna się wyszukiwanie w kontekście danego kodu bieżącego dokumentu.

 `SEEK_START_CODELOCID`\
 Rozpoczyna się wyszukiwanie na identyfikator lokalizacji danego kodu. Identyfikatory lokalizacji kodu są pobierane przez wywołanie metody [GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md).

## <a name="remarks"></a>Uwagi
 Przekazywany jako argument do [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md) metody.

## <a name="requirements"></a>Wymagania
 Header: msdbg.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)
- [GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)