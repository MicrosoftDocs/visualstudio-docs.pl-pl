---
title: CANSTOP_REASON | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CANSTOP_REASON
helpviewer_keywords:
- CANSTOP_REASON enumeration
ms.assetid: 6da944eb-36cd-4a8c-8d71-544c775cfcc1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bbc4143c61a0223fe3940b4167748727d1ebd560
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56711621"
---
# <a name="canstopreason"></a>CANSTOP_REASON
Używany do określenia, jeśli program zatrzymać wykonywanie po osiągnięciu określonego punktu w realizacji.

## <a name="syntax"></a>Składnia

```cpp
enum enum_CANSTOP_REASON {
    CANSTOP_ENTRYPOINT = 0x0000,
    CANSTOP_STEPIN     = 0x0001
};
typedef DWORD CANSTOP_REASON;
```

```csharp
public enum enum_CANSTOP_REASON {
    CANSTOP_ENTRYPOINT = 0x0000,
    CANSTOP_STEPIN     = 0x0001
};
```

## <a name="members"></a>Elementy członkowskie
CANSTOP_ENTRYPOINT określa punkt wejścia w danym programu.

CANSTOP_STEPIN określa przechodzenie krok po kroku do funkcji.

## <a name="remarks"></a>Uwagi
Przekazywany jako argument do [getreason —](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) metodę, aby potwierdzić z sesji debugowania Manager (SDM), jeśli ma nic złego zatrzymać po osiągnięciu punktu wejścia programu, lub po przejściu do funkcji lub metody.

## <a name="requirements"></a>Wymagania
Header: msdbg.h

Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)
