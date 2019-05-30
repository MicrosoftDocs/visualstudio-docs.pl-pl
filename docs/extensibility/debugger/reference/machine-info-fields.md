---
title: MACHINE_INFO_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MACHINE_INFO_FIELDS
helpviewer_keywords:
- MACHINE_INFO_FIELDS enumeration
ms.assetid: 2d61d206-7d40-4df1-8c88-1b3c9c78821e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 79bd733d987511a624235c06b5dbe83206e0c5bd
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66339358"
---
# <a name="machineinfofields"></a>MACHINE_INFO_FIELDS
Określa, jakiego rodzaju informacje należy pobrać dla określonego komputera.

## <a name="syntax"></a>Składnia

```cpp
enum enum_MACHINE_INFO_FIELDS { 
   MCIF_NAME  = 0x00000001,
   MCIF_FLAGS = 0x00000002,
   MCIF_ALL   = 0x00000003
};
typedef DWORD MACHINE_INFO_FIELDS;
```

```csharp
public enum enum_MACHINE_INFO_FIELDS { 
   MCIF_NAME  = 0x00000001,
   MCIF_FLAGS = 0x00000002,
   MCIF_ALL   = 0x00000003
};
```

## <a name="fields"></a>Pola
 `MCIF_NAME`\
 Inicjowanie bądź użyj `bstrName` pole w strukturze.

 `MCIF_FLAGS`\
 Inicjowanie bądź użyj `Flags` pole w strukturze.

 `MIF_ALL`\
 Inicjowanie bądź użyj wszystkie pola w strukturze.

## <a name="remarks"></a>Uwagi
 Te wartości są przekazywane do [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md) metodę, aby wskazać, którzy członkowie [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md) struktury, które mają zostać zainicjowane.

 Używany również w `Fields` członkiem `MACHINE_INFO` struktury, aby wskazać, które pola są używane i prawidłowy.

 Te flagi mogą być łączone przy użyciu bitowego operatora `OR`.

## <a name="requirements"></a>Wymagania
 Header: msdbg.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md)
- [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)