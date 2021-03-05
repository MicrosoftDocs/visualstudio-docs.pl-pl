---
description: Określa sposób interpretacji identyfikatora procesu w strukturze AD_PROCESS_ID.
title: AD_PROCESS_ID_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AD_PROCESS_ID_TYPE
helpviewer_keywords:
- AD_PROCESS_ID_TYPE enumeration
ms.assetid: 0aab80e9-285a-4697-94ac-c864d42a6aaa
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f56ca1db0462a85bd68b193147f5dd3a46c6bee9
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102164347"
---
# <a name="ad_process_id_type"></a>AD_PROCESS_ID_TYPE
Określa sposób interpretacji identyfikatora procesu w strukturze [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) .

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
Identyfikator procesu to identyfikator systemowy. Użyj `ProcessId.dwProcessId` pola struktury [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) .

`AD_PROCESS_ID_GUID`\
Identyfikator procesu jest identyfikatorem GUID. Użyj `ProcessId.guidProcessId` pola `AD_PROCESS_ID` struktury.

## <a name="remarks"></a>Uwagi
Używane dla `ProcessIdType` elementu członkowskiego struktury [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) do identyfikowania typu identyfikatora procesu, który jest zawarty w strukturze. Określa sposób interpretacji `ProcessId` Unii w strukturze.

## <a name="requirements"></a>Wymagania
Nagłówek: Msdbg. h

Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
