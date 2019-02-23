---
title: EVALFLAGS90 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- EVALFLAGS90 enumeration
ms.assetid: 64fb0139-8b04-4726-b52c-db2e04d65498
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 73673d0b0ca7ccb640a3fab2043bc35b26657a9b
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56720305"
---
# <a name="evalflags90"></a>EVALFLAGS90
Wylicza prawidłowe wartości dla flagi sterujące Obliczanie wyrażenia. To wyliczenie rozszerza [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) wyliczenia.

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

#### <a name="parameters"></a>Parametry
EVAL90_RETURNVALUE Określa, że wartość zwracana, jeśli istnieje, można obliczyć.

EVAL90_NOSIDEEFFECTS Określa, że efekty uboczne niemożliwe.

EVAL90_ALLOWBPS określa zatrzymywanie punktów przerwania.

EVAL90_ALLOWERRORREPORT Określa, że raportów o błędach do hosta mają być dozwolone. Używane głównie do obliczenia wyrażenia w skrypcie w programie Internet Explorer.

Funkcje wymusza EVAL90_FUNCTION_AS_ADDRESS, która ma zostać obliczone jako adresy, zamiast wywoływania funkcji.

Funkcja zapobiega EVAL90_NOFUNCEVAL z oceniane. Na przykład, rozważmy `int` tokenu w wyrażeniu `myExpression(int) + 10`. Ta funkcja może być poprawnie określona jako adres, ale nie jako wartość.

Flaga EVAL90_NOEVENTS do wskazania, że zdarzenia, które wystąpiły podczas obliczania wyrażenia nie powinny być wysyłane, Menedżer debugowania sesji (SDM) lub środowiska IDE.

Włącza EVAL90_DESIGN_TIME_EXPR_EVAL Obliczanie wyrażenia czasu projektowania.

Umożliwia EVAL90_ALLOW_IMPLICIT_VARS niejawnego tworzenia zmiennej.

Obliczanie EVAL90_FORCE_EVALUATION_NOW wymusza natychmiastowe. Jest to przydatne podczas obsługi żądania, takie jak żądania użytkownika.

## <a name="requirements"></a>Wymagania
Nagłówek: Msdbg90.h

Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
