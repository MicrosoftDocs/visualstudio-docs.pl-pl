---
title: EVALFLAGS90 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80737103"
---
# <a name="evalflags90"></a>EVALFLAGS90
Wylicza prawidłowe wartości dla flag kontrolujących Obliczanie wyrażenia. To Wyliczenie rozszerza Wyliczenie [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) .

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
Określa, że wartość zwracana, jeśli ma zostać obliczona.

`EVAL90_NOSIDEEFFECTS`\
Określa, że efekty uboczne nie są dozwolone.

`EVAL90_ALLOWBPS`\
Określa zatrzymanie dla punktów przerwania.

`EVAL90_ALLOWERRORREPORT`\
Określa, że raportowanie błędów ma być dozwolone dla hosta. Służy głównie do oceny wyrażeń w skrypcie w programie Internet Explorer.

`EVAL90_FUNCTION_AS_ADDRESS`\
Wymusza, aby funkcje były oceniane jako adresy zamiast wywoływania funkcji.

`EVAL90_NOFUNCEVAL`\
Zapobiega ocenie funkcji. Rozważmy na przykład `int` token w wyrażeniu `myExpression(int) + 10` . Ta funkcja może być poprawnie oceniona jako adres, ale nie jako wartość.

`EVAL90_NOEVENTS`\
Flaga wskazująca, że zdarzenia występujące podczas obliczania wyrażenia nie powinny być wysyłane do Menedżera debugowania sesji (SDM) ani do IDE.

`EVAL90_DESIGN_TIME_EXPR_EVAL`\
Włącza obliczanie wyrażeń czasu projektowania.

`EVAL90_ALLOW_IMPLICIT_VARS`\
Umożliwia niejawne Tworzenie zmiennych.

`EVAL90_FORCE_EVALUATION_NOW`\
Wymusza natychmiastowe wypróbowanie. Jest to przydatne podczas obsługi żądania, takiego jak żądanie użytkownika.

## <a name="requirements"></a>Wymagania
Nagłówek: Msdbg90. h

Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
