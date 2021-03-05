---
description: Wskazuje protokół używany do komunikacji między serwerem debugowania a pakietem debugowania (DE).
title: CONNECTION_PROTOCOL | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONNECTION_PROTOCOL
helpviewer_keywords:
- CONNECTION_PROTOCOL enumeration
ms.assetid: 99df5865-8b36-486d-9f4c-d10ae2bc688a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 24ac267552166bea43df77f31cb79d8198fb7514
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102170864"
---
# <a name="connection_protocol"></a>CONNECTION_PROTOCOL
Wskazuje protokół używany do komunikacji między serwerem debugowania a pakietem debugowania (DE).

## <a name="syntax"></a>Składnia

```cpp
typedef enum tagCONNECTION_PROTOCOL {
    CONNECTION_NONE    = 0,
    CONNECTION_UNKNOWN = 1,
    CONNECTION_LOCAL   = 2,
    CONNECTION_PIPE    = 3,
    CONNECTION_TCPIP   = 4,
    CONNECTION_HTTP    = 5,
    CONNECTION_OTHER   = 6
} CONNECTION_PROTOCOL;
```

```csharp
public enum CONNECTION_PROTOCOL {
    CONNECTION_NONE    = 0,
    CONNECTION_UNKNOWN = 1,
    CONNECTION_LOCAL   = 2,
    CONNECTION_PIPE    = 3,
    CONNECTION_TCPIP   = 4,
    CONNECTION_HTTP    = 5,
    CONNECTION_OTHER   = 6
};
```

## <a name="fields"></a>Pola
`CONNECTION_NONE`\
Nie wprowadzono połączenia z serwerem.

`CONNECTION_UNKNOWN`\
Połączenie zostało nawiązane, ale jego typ jest nieznany.

`CONNECTION_LOCAL`\
Połączenie jest serwerem lokalnym.

`CONNECTION_PIPE`\
Połączenie odbywa się za pomocą nazwanego potoku.

`CONNECTION_TCPIP`\
Połączenie używa protokołu TCP/IP.

`CONNECTION_HTTP`\
Połączenie korzysta z protokołu HTTP (za pośrednictwem serwera sieci Web).

`CONNECTION_OTHER`\
Nawiązano połączenie innego typu (ta wartość nie jest obecnie używana).

## <a name="remarks"></a>Uwagi
Te wartości są zwracane z metody [GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md) .

## <a name="requirements"></a>Wymagania
Nagłówek: Msdbg. h

Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)
