---
title: EVALFLAGS90 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- EVALFLAGS90 enumeration
ms.assetid: 64fb0139-8b04-4726-b52c-db2e04d65498
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 01951885541ba4acce33f3e4f06f7106116ccc62
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737103"
---
# <a name="evalflags90"></a>EVALFLAGS90
Wylicza prawidłowe wartości dla flag, które kontrolują ocenę wyrażenia. To wyliczenie rozszerza wyliczenie [EVALFLAGS.](../../../extensibility/debugger/reference/evalflags.md)

## <a name="syntax"></a>Składnia

```cpp
enum enum_EVALFLAGS90
{
    // VS 8.0 values
    EVAL90_RETURNVALUE                 = 0x0002,
    EVAL90_NOSIDEEFFECTS               = 0x0004,
    EVAL90_ALLOWBPS                    = 0x0008,
    EVAL90_ALLOWERRORREPORT            = 0x0010,
    EVAL90_FUNCTION_AS_ADDRESS         = 0x0040,
    EVAL90_NOFUNCEVAL                  = 0x0080,
    EVAL90_NOEVENTS                    = 0x1000,
    EVAL90_DESIGN_TIME_EXPR_EVAL       = 0x2000,
    EVAL90_ALLOW_IMPLICIT_VARS         = 0x4000,

    // Values added in VS 9.0
    EVAL90_FORCE_EVALUATION_NOW        = 0x8000
};
typedef DWORD EVALFLAGS90;
```

```csharp
public enum enum_EVALFLAGS90
{
    // VS 8.0 values
    EVAL90_RETURNVALUE                 = 0x0002,
    EVAL90_NOSIDEEFFECTS               = 0x0004,
    EVAL90_ALLOWBPS                    = 0x0008,
    EVAL90_ALLOWERRORREPORT            = 0x0010,
    EVAL90_FUNCTION_AS_ADDRESS         = 0x0040,
    EVAL90_NOFUNCEVAL                  = 0x0080,
    EVAL90_NOEVENTS                    = 0x1000,
    EVAL90_DESIGN_TIME_EXPR_EVAL       = 0x2000,
    EVAL90_ALLOW_IMPLICIT_VARS         = 0x4000,

    // Values added in VS 9.0
    EVAL90_FORCE_EVALUATION_NOW        = 0x8000
};
```

## <a name="fields"></a>Pola
`EVAL90_RETURNVALUE`\
Określa, że wartość zwracana, jeśli istnieje, być oceniane.

`EVAL90_NOSIDEEFFECTS`\
Określa, że działania niepożądane nie są dozwolone.

`EVAL90_ALLOWBPS`\
Określa zatrzymywanie punktów przerwania.

`EVAL90_ALLOWERRORREPORT`\
Określa, że raportowanie błędów do hosta ma być dozwolone. Używany głównie do oceny wyrażenia w skrypcie w programie Internet Explorer.

`EVAL90_FUNCTION_AS_ADDRESS`\
Wymusza funkcje, które mają być oceniane jako adresy, zamiast wywoływania funkcji.

`EVAL90_NOFUNCEVAL`\
Zapobiega ocenie funkcji. Rozważmy na `int` przykład token `myExpression(int) + 10`w wyrażeniu . Ta funkcja może być poprawnie oceniona jako adres, ale nie jako wartość.

`EVAL90_NOEVENTS`\
Flaga, aby wskazać, że zdarzenia, które występują podczas oceny wyrażenia nie powinny być wysyłane do menedżera debugowania sesji (SDM) lub ide.

`EVAL90_DESIGN_TIME_EXPR_EVAL`\
Umożliwia ocenę wyrażenia w czasie projektowania.

`EVAL90_ALLOW_IMPLICIT_VARS`\
Umożliwia tworzenie niejawnej zmiennej.

`EVAL90_FORCE_EVALUATION_NOW`\
Wymusza natychmiastowe wystąpienie oceny. Jest to przydatne podczas obsługi żądania, takich jak żądanie użytkownika.

## <a name="requirements"></a>Wymagania
Nagłówek: Msdbg90.h

Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
