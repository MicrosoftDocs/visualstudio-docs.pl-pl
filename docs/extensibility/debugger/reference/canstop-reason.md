---
title: CANSTOP_REASON | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CANSTOP_REASON
helpviewer_keywords:
- CANSTOP_REASON enumeration
ms.assetid: 6da944eb-36cd-4a8c-8d71-544c775cfcc1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d7be361d4468584c109db52f487b3de3c1fdff0a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737681"
---
# <a name="canstop_reason"></a>CANSTOP_REASON
Służy do określenia, czy program może zatrzymać wykonanie po osiągnięciu określonego punktu w wykonaniu.

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
Przekazany jako argument do [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) metody, aby potwierdzić za pomocą Menedżera debugowania sesji (SDM), jeśli jest w porządku, aby zatrzymać po osiągnięciu punktu wejścia programu lub po przejściu do funkcji lub metody.

## <a name="requirements"></a>Wymagania
Nagłówek: msdbg.h

Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)
