---
title: CONNECTION_PROTOCOL | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- CONNECTION_PROTOCOL
helpviewer_keywords:
- CONNECTION_PROTOCOL enumeration
ms.assetid: 99df5865-8b36-486d-9f4c-d10ae2bc688a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4dcf3d271d331664d6d2ef210868245b50c264d6
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2019
ms.locfileid: "56316487"
---
# <a name="connectionprotocol"></a>CONNECTION_PROTOCOL
Określa protokół używany do komunikacji między serwerem debugowania i debugowanie pakietu (DE).

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

#### <a name="parameters"></a>Parametry
CONNECTION_NONE  
Połączenie nie zostało ustanowione do serwera.

CONNECTION_UNKNOWN  
Połączenie zostało wykonane, ale jest nieznanego typu.

CONNECTION_LOCAL  
To połączenie serwera lokalnego.

CONNECTION_PIPE  
Połączenie jest użycie nazwanego potoku.

CONNECTION_TCPIP  
Połączenie używa protokołu TCP/IP.

CONNECTION_HTTP  
Połączenie korzysta z protokołu HTTP (za pośrednictwem serwera sieci Web).

CONNECTION_OTHER  
Inny rodzaj połączenie zostało ustanowione (Ta wartość nie jest obecnie używany).

## <a name="remarks"></a>Uwagi
Te wartości są zwracane z [GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md) metody.

## <a name="requirements"></a>Wymagania
Header: msdbg.h

Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
[Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)  
[GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)
