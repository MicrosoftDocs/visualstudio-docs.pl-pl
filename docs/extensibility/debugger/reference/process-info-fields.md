---
title: PROCESS_INFO_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROCESS_INFO_FIELDS
helpviewer_keywords:
- PROCESS_INFO_FIELDS enumeration
ms.assetid: 0d9cc345-3d3a-44d8-ae15-a67acb97a828
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 28af715c307ebede5fa264c46cd42b85e8868674
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/09/2019
ms.locfileid: "65457956"
---
# <a name="processinfofields"></a>PROCESS_INFO_FIELDS
Określić, jakiego rodzaju informacje należy pobrać dla procesu.

## <a name="syntax"></a>Składnia

```cpp
enum enum_PROCESS_INFO_FIELDS { 
   PIF_FILE_NAME             = 0x00000001,
   PIF_BASE_NAME             = 0x00000002,
   PIF_TITLE                 = 0x00000004,
   PIF_PROCESS_ID            = 0x00000008,
   PIF_SESSION_ID            = 0x00000010,
   PIF_ATTACHED_SESSION_NAME = 0x00000020,
   PIF_CREATION_TIME         = 0x00000040,
   PIF_FLAGS                 = 0x00000080,
   PIF_ALL                   = 0x000000ff
};
typedef DWORD PROCESS_INFO_FIELDS;
```

```csharp
public enum enum_PROCESS_INFO_FIELDS { 
   PIF_FILE_NAME             = 0x00000001,
   PIF_BASE_NAME             = 0x00000002,
   PIF_TITLE                 = 0x00000004,
   PIF_PROCESS_ID            = 0x00000008,
   PIF_SESSION_ID            = 0x00000010,
   PIF_ATTACHED_SESSION_NAME = 0x00000020,
   PIF_CREATION_TIME         = 0x00000040,
   PIF_FLAGS                 = 0x00000080,
   PIF_ALL                   = 0x000000ff
};
```

## <a name="fields"></a>Pola
 `PIF_FILE_NAME`\
 Inicjowanie bądź użyj `bstrFileName` pole [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) struktury.

 `PIF_BASE_NAME`\
 Inicjowanie bądź użyj `bstrBaseName` pole `PROCESS_INFO` struktury.

 `PIF_TITLE`\
 Inicjowanie bądź użyj `bstrTitle` pole `PROCESS_INFO` struktury.

 `PIF_PROCESS_ID`\
 Inicjowanie bądź użyj `ProcessId` pole `PROCESS_INFO` struktury.

 `PIF_SESSION_ID`\
 Inicjowanie bądź użyj `dwSessionId` pole `PROCESS_INFO` struktury.

 `PIF_ATTACHED_SESSION_NAME`\
 Inicjowanie bądź użyj `bstrAttachedSessionName` pole `PROCESS_INFO` struktury.

 `PIF_CREATION_TIME`\
 Inicjowanie bądź użyj `CreationTime` pole `PROCESS_INFO` struktury.

 `PIF_FLAGS`\
 Inicjowanie bądź użyj `Flags` pole `PROCESS_INFO` struktury.

 `PIF_ALL`\
 Wypełnia wszystkie pola.

## <a name="remarks"></a>Uwagi
 Przekazany do [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) metodę, aby wskazać, które pola [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) struktury, które mają zostać zainicjowane.

 Używany również w `Fields` pole `PROCESS_INFO` struktury, aby wskazać, które pola są używane i prawidłowy.

 Te flagi mogą być łączone przy użyciu bitowego operatora `OR`.

## <a name="requirements"></a>Wymagania
 Header: msdbg.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)