---
title: CONNECTION_PROTOCOL | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONNECTION_PROTOCOL
helpviewer_keywords:
- CONNECTION_PROTOCOL enumeration
ms.assetid: 99df5865-8b36-486d-9f4c-d10ae2bc688a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 29ac287462149a20f52a1affdeab7fa6b8333711
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737651"
---
# <a name="connection_protocol"></a>CONNECTION_PROTOCOL
Wskazuje protokół używany do komunikacji między serwerem debugowania a pakietem debugowania (DE).

## <a name="syntax"></a>Składnia

```cpp
typedef enum tagCONNECTION_PROTOCOL {
    CONNECTION_NONE    = 0,
    CONNECTION_UNKNOWN = 1,
    CONNECTION_LOCAL   = 2,
    CONNECTION_PIPE    = 3,
    CONNECTION_TCPIP   = 4,
    CONNECTION_HTTP    = 5,
    CONNECTION_OTHER   = 6
} CONNECTION_PROTOCOL;
```

```csharp
public enum CONNECTION_PROTOCOL {
    CONNECTION_NONE    = 0,
    CONNECTION_UNKNOWN = 1,
    CONNECTION_LOCAL   = 2,
    CONNECTION_PIPE    = 3,
    CONNECTION_TCPIP   = 4,
    CONNECTION_HTTP    = 5,
    CONNECTION_OTHER   = 6
};
```

## <a name="fields"></a>Pola
`CONNECTION_NONE`\
Nie nawiązyno połączenia z serwerem.

`CONNECTION_UNKNOWN`\
Nawiązanie połączenia, ale jest typu nieznanego.

`CONNECTION_LOCAL`\
Połączenie jest z serwerem lokalnym.

`CONNECTION_PIPE`\
Połączenie odbywa się za pośrednictwem nazwanego potoku.

`CONNECTION_TCPIP`\
Połączenie używa protokołu TCP/IP.

`CONNECTION_HTTP`\
Połączenie używa protokołu HTTP (za pośrednictwem serwera sieci Web).

`CONNECTION_OTHER`\
Ustanowiono inny typ połączenia (ta wartość nie jest obecnie używana).

## <a name="remarks"></a>Uwagi
Wartości te są zwracane z [GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md) metody.

## <a name="requirements"></a>Wymagania
Nagłówek: msdbg.h

Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)
