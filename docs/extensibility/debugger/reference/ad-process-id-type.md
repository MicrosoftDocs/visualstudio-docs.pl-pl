---
title: AD_PROCESS_ID_TYPE | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AD_PROCESS_ID_TYPE
helpviewer_keywords:
- AD_PROCESS_ID_TYPE enumeration
ms.assetid: 0aab80e9-285a-4697-94ac-c864d42a6aaa
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a88fbe97cede8d343f1a96bc1917a69b8905b02b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738188"
---
# <a name="ad_process_id_type"></a>AD_PROCESS_ID_TYPE
Określa sposób interpretowania identyfikatora procesu w strukturze [AD_PROCESS_ID.](../../../extensibility/debugger/reference/ad-process-id.md)

## <a name="syntax"></a>Składnia

```cpp
enum enum_AD_PROCESS_ID {
    AD_PROCESS_ID_SYSTEM = 0,
    AD_PROCESS_ID_GUID   = 1
};
typedef DWORD AD_PROCESS_ID_TYPE;
```

```csharp
public enum enum_AD_PROCESS_ID {
    AD_PROCESS_ID_SYSTEM = 0,
    AD_PROCESS_ID_GUID   = 1
};
```

## <a name="fields"></a>Pola
`AD_PROCESS_ID_SYSTEM`\
Identyfikator procesu jest identyfikatorem systemu. Użyj `ProcessId.dwProcessId` pola [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) struktury.

`AD_PROCESS_ID_GUID`\
Identyfikator procesu jest identyfikatorem GUID. Użyj `ProcessId.guidProcessId` pola `AD_PROCESS_ID` konstrukcji.

## <a name="remarks"></a>Uwagi
Używany dla `ProcessIdType` elementu członkowskiego [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) struktury do identyfikowania typu identyfikatora procesu, który znajduje się w strukturze. Określa sposób interpretowania `ProcessId` unii w strukturze.

## <a name="requirements"></a>Wymagania
Nagłówek: msdbg.h

Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
