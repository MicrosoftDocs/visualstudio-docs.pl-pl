---
description: Określa położenie, od którego należy zacząć odszukać w strumieniu demontażu.
title: SEEK_START | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SEEK_START
helpviewer_keywords:
- SEEK_START enumeration
ms.assetid: 55bd8901-626e-428b-a263-23b14417f4c6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a15635f2cf56f3be1e9955af4ee79782ed3c85fa
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105061527"
---
# <a name="seek_start"></a>SEEK_START
Określa położenie, od którego należy zacząć odszukać w strumieniu demontażu.

## <a name="syntax"></a>Składnia

```cpp
enum enum_SEEK_START { 
   SEEK_START_BEGIN       = 0x0001,
   SEEK_START_END         = 0x0002,
   SEEK_START_CURRENT     = 0x0003,
   SEEK_START_CODECONTEXT = 0x0004,
   SEEK_START_CODELOCID   = 0x0005
};
typedef DWORD SEEK_START;
```

```csharp
public enum enum_SEEK_START { 
   SEEK_START_BEGIN       = 0x0001,
   SEEK_START_END         = 0x0002,
   SEEK_START_CURRENT     = 0x0003,
   SEEK_START_CODECONTEXT = 0x0004,
   SEEK_START_CODELOCID   = 0x0005
};
```

## <a name="fields"></a>Pola
 `SEEK_START_BEGIN`\
 Rozpoczyna wyszukiwanie na początku bieżącego dokumentu.

 `SEEK_START_END`\
 Zaczyna przeszukiwanie na końcu bieżącego dokumentu.

 `SEEK_START_CURRENT`\
 Zaczyna wyszukiwanie w bieżącym położeniu bieżącego dokumentu.

 `SEEK_START_CODECONTEXT`\
 Zaczyna wyszukiwanie w danym kontekście kodu bieżącego dokumentu.

 `SEEK_START_CODELOCID`\
 Zaczyna wyszukiwanie w danym identyfikatorze lokalizacji kodu. Identyfikatory lokalizacji kodu są uzyskiwane przez wywołanie [GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md).

## <a name="remarks"></a>Uwagi
 Przekazanie jako argument do metody [wyszukiwania](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md) .

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)
- [GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)
