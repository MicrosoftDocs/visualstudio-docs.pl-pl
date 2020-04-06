---
title: PROCESS_INFO_FIELDS | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714010"
---
# <a name="process_info_fields"></a>PROCESS_INFO_FIELDS
Określono, jakiego rodzaju informacje mają być pobierane dla procesu.

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
 Inicjuj/użyj `bstrFileName` pola [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) struktury.

 `PIF_BASE_NAME`\
 Inicjuj/użyj `bstrBaseName` `PROCESS_INFO` pola konstrukcji.

 `PIF_TITLE`\
 Inicjuj/użyj `bstrTitle` `PROCESS_INFO` pola konstrukcji.

 `PIF_PROCESS_ID`\
 Inicjuj/użyj `ProcessId` `PROCESS_INFO` pola konstrukcji.

 `PIF_SESSION_ID`\
 Inicjuj/użyj `dwSessionId` `PROCESS_INFO` pola konstrukcji.

 `PIF_ATTACHED_SESSION_NAME`\
 Inicjuj/użyj `bstrAttachedSessionName` `PROCESS_INFO` pola konstrukcji.

 `PIF_CREATION_TIME`\
 Inicjuj/użyj `CreationTime` `PROCESS_INFO` pola konstrukcji.

 `PIF_FLAGS`\
 Inicjuj/użyj `Flags` `PROCESS_INFO` pola konstrukcji.

 `PIF_ALL`\
 Wypełnia wszystkie pola.

## <a name="remarks"></a>Uwagi
 Przekazany do [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) metody, aby wskazać, które pola [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) struktury mają być inicjowane.

 Używany również `Fields` w `PROCESS_INFO` polu struktury, aby wskazać, które pola są używane i prawidłowe.

 Flagi te mogą być łączone z bitowym `OR`.

## <a name="requirements"></a>Wymagania
 Nagłówek: msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)
