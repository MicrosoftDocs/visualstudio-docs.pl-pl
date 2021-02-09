---
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
ms.openlocfilehash: b6756d574c36d6381b606be597ca0e54e7945763
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874359"
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
