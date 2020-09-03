---
title: PROCESS_INFO_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROCESS_INFO_FIELDS
helpviewer_keywords:
- PROCESS_INFO_FIELDS enumeration
ms.assetid: 0d9cc345-3d3a-44d8-ae15-a67acb97a828
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f81709e7146bbdef13daa3564bb784fd9c08d58e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80714010"
---
# <a name="process_info_fields"></a>PROCESS_INFO_FIELDS
Określony rodzaj informacji do pobrania dla procesu.

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
 Zainicjuj/Użyj `bstrFileName` pola struktury [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) .

 `PIF_BASE_NAME`\
 Zainicjuj/Użyj `bstrBaseName` pola `PROCESS_INFO` struktury.

 `PIF_TITLE`\
 Zainicjuj/Użyj `bstrTitle` pola `PROCESS_INFO` struktury.

 `PIF_PROCESS_ID`\
 Zainicjuj/Użyj `ProcessId` pola `PROCESS_INFO` struktury.

 `PIF_SESSION_ID`\
 Zainicjuj/Użyj `dwSessionId` pola `PROCESS_INFO` struktury.

 `PIF_ATTACHED_SESSION_NAME`\
 Zainicjuj/Użyj `bstrAttachedSessionName` pola `PROCESS_INFO` struktury.

 `PIF_CREATION_TIME`\
 Zainicjuj/Użyj `CreationTime` pola `PROCESS_INFO` struktury.

 `PIF_FLAGS`\
 Zainicjuj/Użyj `Flags` pola `PROCESS_INFO` struktury.

 `PIF_ALL`\
 Wypełnia wszystkie pola.

## <a name="remarks"></a>Uwagi
 Przeszedł do metody [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) , aby wskazać, które pola struktury [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) mają być inicjowane.

 Używane również w `Fields` polu `PROCESS_INFO` struktury do wskazywania, które pola są używane i są prawidłowe.

 Flagi te mogą być połączone z bitową `OR` .

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)
