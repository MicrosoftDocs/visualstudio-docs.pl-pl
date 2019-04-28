---
title: AD_PROCESS_ID_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AD_PROCESS_ID_TYPE
helpviewer_keywords:
- AD_PROCESS_ID_TYPE enumeration
ms.assetid: 0aab80e9-285a-4697-94ac-c864d42a6aaa
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 405d11b0c685017d59251ba83126a73fe1a96db2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62925276"
---
# <a name="adprocessidtype"></a>AD_PROCESS_ID_TYPE
Określa, jak interpretować procesu o identyfikatorze w [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) struktury.

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

## <a name="members"></a>Elementy członkowskie
Identyfikator procesu AD_PROCESS_ID_SYSTEM jest identyfikator systemu. Użyj `ProcessId.dwProcessId` pole [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) struktury.

Identyfikator procesu AD_PROCESS_ID_GUID jest identyfikatorem GUID. Użyj `ProcessId.guidProcessId` pole `AD_PROCESS_ID` struktury.

## <a name="remarks"></a>Uwagi
Używany do `ProcessIdType` członkiem [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) struktury w celu określenia typu Identyfikator procesu, który znajduje się w strukturze. Określa, jak interpretować `ProcessId` Unii w strukturze.

## <a name="requirements"></a>Wymagania
Header: msdbg.h

Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
