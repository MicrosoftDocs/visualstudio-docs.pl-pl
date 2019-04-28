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
ms.openlocfilehash: 835509048e888e13b91c53d9e35bd03d7aebdfed
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62913504"
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

## <a name="members"></a>Elementy członkowskie
 PIF_FILE_NAME zainicjować bądź użyj `bstrFileName` pole [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) struktury.

 PIF_BASE_NAME zainicjować bądź użyj `bstrBaseName` pole `PROCESS_INFO` struktury.

 PIF_TITLE zainicjować bądź użyj `bstrTitle` pole `PROCESS_INFO` struktury.

 PIF_PROCESS_ID zainicjować bądź użyj `ProcessId` pole `PROCESS_INFO` struktury.

 PIF_SESSION_ID zainicjować bądź użyj `dwSessionId` pole `PROCESS_INFO` struktury.

 PIF_ATTACHED_SESSION_NAME zainicjować bądź użyj `bstrAttachedSessionName` pole `PROCESS_INFO` struktury.

 PIF_CREATION_TIME zainicjować bądź użyj `CreationTime` pole `PROCESS_INFO` struktury.

 PIF_FLAGS zainicjować bądź użyj `Flags` pole `PROCESS_INFO` struktury.

 PIF_ALL wypełnia wszystkie pola.

## <a name="remarks"></a>Uwagi
 Przekazany do [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) metodę, aby wskazać, które pola [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) struktury, które mają zostać zainicjowane.

 Używany również w `Fields` pole `PROCESS_INFO` struktury, aby wskazać, które pola są używane i prawidłowy.

 Te flagi mogą być łączone przy użyciu bitowego operatora `OR`.

## <a name="requirements"></a>Wymagania
 Header: msdbg.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)