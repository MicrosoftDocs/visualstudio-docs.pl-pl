---
title: PROVIDER_FLAGS | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROVIDER_FLAGS
helpviewer_keywords:
- PROVIDER_FLAGS enumeration
ms.assetid: 8cbd2312-ed2f-4477-b192-c3f25c6098c3
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 803d9569c611e3c4cd70f2c82ecd525716d8ddb3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62913530"
---
# <a name="providerflags"></a>PROVIDER_FLAGS
Określa żądane właściwości, które mają zostać uzyskane od dostawcy programu.

## <a name="syntax"></a>Składnia

```cpp
enum enum_PROVIDER_FLAGS {
   PFLAG_NONE                    = 0x00,
   PFLAG_REMOTE_PORT             = 0x01,
   PFLAG_DEBUGGEE                = 0x02,
   PFLAG_ATTACHED_TO_DEBUGGEE    = 0x04,
   PFLAG_REASON_WATCH            = 0x08,
   PFLAG_GET_PROGRAM_NODES       = 0x10,
   PFLAG_GET_IS_DEBUGGER_PRESENT = 0x20
};
typedef DWORD PROVIDER_FLAGS;
```

```csharp
public enum enum_PROVIDER_FLAGS {
   PFLAG_NONE                    = 0x00,
   PFLAG_REMOTE_PORT             = 0x01,
   PFLAG_DEBUGGEE                = 0x02,
   PFLAG_ATTACHED_TO_DEBUGGEE    = 0x04,
   PFLAG_REASON_WATCH            = 0x08,
   PFLAG_GET_PROGRAM_NODES       = 0x10,
   PFLAG_GET_IS_DEBUGGER_PRESENT = 0x20
};
```

## <a name="members"></a>Elementy członkowskie
 Flagi PFLAG_NONE nie określono.

 PFLAG_REMOTE_PORT obiekt wywołujący chce listę programów na innym komputerze niż [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)].

 Ten proces jest teraz debugowana przez to wystąpienie elementu PFLAG_DEBUGGEE [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)].

 PFLAG_ATTACH_TODEBUGGEE [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] jest dołączony do debugowanego programu, ale nie uruchomiony.

 PFLAG_REASON_WATCH [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] obserwuje dla zdarzeń.

 PFLAG_GET_PROGRAM_NODES obiekt wywołujący chce `ProgramNodes` pole [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) struktury.

 PFLAG_GET_IS_DEBUGGER_PRESENT obiekt wywołujący chce `fIsTheDebuggerPresent` pole `PROVIDER_PROCESS_DATA` struktury.

## <a name="remarks"></a>Uwagi
 Te flagi są przekazywane do następujących metod:

- [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)

- [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)

- [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)

  Te wartości można łączyć przy użyciu bitowego operatora `OR`.

## <a name="requirements"></a>Wymagania
 Header: msdbg.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)
- [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)
- [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)
- [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)