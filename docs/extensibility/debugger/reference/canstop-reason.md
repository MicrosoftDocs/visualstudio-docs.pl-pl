---
description: Służy do określenia, czy program może zatrzymać wykonywanie po osiągnięciu określonego punktu w wykonaniu.
title: CANSTOP_REASON | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CANSTOP_REASON
helpviewer_keywords:
- CANSTOP_REASON enumeration
ms.assetid: 6da944eb-36cd-4a8c-8d71-544c775cfcc1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: def5bdbb6433f6a154eb6f84a88fb39004bc41ae
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102171001"
---
# <a name="canstop_reason"></a>CANSTOP_REASON
Służy do określenia, czy program może zatrzymać wykonywanie po osiągnięciu określonego punktu w wykonaniu.

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

## <a name="fields"></a>Pola
`CANSTOP_ENTRYPOINT`\
Określa punkt wejścia danego programu.

`CANSTOP_STEPIN`\
Określa przechodzenie do funkcji.

## <a name="remarks"></a>Uwagi
Przeszedł jako argument do metody [Getpowód](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) , aby potwierdzić z menedżerem debugowania sesji (SDM), jeśli nie można go zatrzymać po osiągnięciu punktu wejścia programu lub po przejściu do funkcji lub metody.

## <a name="requirements"></a>Wymagania
Nagłówek: Msdbg. h

Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)
