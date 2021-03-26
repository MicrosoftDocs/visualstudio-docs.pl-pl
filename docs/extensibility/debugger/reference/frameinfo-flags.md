---
description: Określa informacje do pobrania na temat obiektu ramki stosu.
title: FRAMEINFO_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FRAMEINFO_FLAGS
helpviewer_keywords:
- FRAMEINFO_FLAGS enumeration
ms.assetid: 41578062-8455-412a-9d8b-1e1e9dc8d52e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d4214dd81945c3e7e2711a500e2e3a2b173e33e0
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105059265"
---
# <a name="frameinfo_flags"></a>FRAMEINFO_FLAGS
Określa informacje do pobrania na temat obiektu ramki stosu.

## <a name="syntax"></a>Składnia

```cpp
enum enum_FRAMEINFO_FLAGS {
    FIF_FUNCNAME              = 0x00000001,
    FIF_RETURNTYPE            = 0x00000002,
    FIF_ARGS                  = 0x00000004,
    FIF_LANGUAGE              = 0x00000008,
    FIF_MODULE                = 0x00000010,
    FIF_STACKRANGE            = 0x00000020,
    FIF_FRAME                 = 0x00000040,
    FIF_DEBUGINFO             = 0x00000080,
    FIF_STALECODE             = 0x00000100,
    FIF_ANNOTATEDFRAME        = 0x00000200,
    FIF_DEBUG_MODULEP         = 0x00000400,
    FIF_FUNCNAME_FORMAT       = 0x00001000,
    FIF_FUNCNAME_RETURNTYPE   = 0x00002000,
    FIF_FUNCNAME_ARGS         = 0x00004000,
    FIF_FUNCNAME_LANGUAGE     = 0x00008000,
    FIF_FUNCNAME_MODULE       = 0x00010000,
    FIF_FUNCNAME_LINES        = 0x00020000,
    FIF_FUNCNAME_OFFSET       = 0x00040000,
    FIF_FUNCNAME_ARGS_TYPES   = 0x00100000,
    FIF_FUNCNAME_ARGS_NAMES   = 0x00200000,
    FIF_FUNCNAME_ARGS_VALUES  = 0x00400000,
    FIF_FUNCNAME_ARGS_ALL     = 0x00700000,
    FIF_ARGS_TYPES            = 0x01000000,
    FIF_ARGS_NAMES            = 0x02000000,
    FIF_ARGS_VALUES           = 0x04000000,
    FIF_ARGS_ALL              = 0x07000000,
    FIF_ARGS_NOFORMAT         = 0x08000000,
    FIF_ARGS_NO_FUNC_EVAL     = 0x10000000,
    FIF_FILTER_NON_USER_CODE  = 0x20000000,
    FIF_ARGS_NO_TOSTRING      = 0x40000000,
    FIF_DESIGN_TIME_EXPR_EVAL = 0x80000000
};
typedef DWORD FRAMEINFO_FLAGS;
```

```csharp
public enum enum_FRAMEINFO_FLAGS {
    FIF_FUNCNAME              = 0x00000001,
    FIF_RETURNTYPE            = 0x00000002,
    FIF_ARGS                  = 0x00000004,
    FIF_LANGUAGE              = 0x00000008,
    FIF_MODULE                = 0x00000010,
    FIF_STACKRANGE            = 0x00000020,
    FIF_FRAME                 = 0x00000040,
    FIF_DEBUGINFO             = 0x00000080,
    FIF_STALECODE             = 0x00000100,
    FIF_ANNOTATEDFRAME        = 0x00000200,
    FIF_DEBUG_MODULEP         = 0x00000400,
    FIF_FUNCNAME_FORMAT       = 0x00001000,
    FIF_FUNCNAME_RETURNTYPE   = 0x00002000,
    FIF_FUNCNAME_ARGS         = 0x00004000,
    FIF_FUNCNAME_LANGUAGE     = 0x00008000,
    FIF_FUNCNAME_MODULE       = 0x00010000,
    FIF_FUNCNAME_LINES        = 0x00020000,
    FIF_FUNCNAME_OFFSET       = 0x00040000,
    FIF_FUNCNAME_ARGS_TYPES   = 0x00100000,
    FIF_FUNCNAME_ARGS_NAMES   = 0x00200000,
    FIF_FUNCNAME_ARGS_VALUES  = 0x00400000,
    FIF_FUNCNAME_ARGS_ALL     = 0x00700000,
    FIF_ARGS_TYPES            = 0x01000000,
    FIF_ARGS_NAMES            = 0x02000000,
    FIF_ARGS_VALUES           = 0x04000000,
    FIF_ARGS_ALL              = 0x07000000,
    FIF_ARGS_NOFORMAT         = 0x08000000,
    FIF_ARGS_NO_FUNC_EVAL     = 0x10000000,
    FIF_FILTER_NON_USER_CODE  = 0x20000000,
    FIF_ARGS_NO_TOSTRING      = 0x40000000,
    FIF_DESIGN_TIME_EXPR_EVAL = 0x80000000
};
```

## <a name="fields"></a>Pola
`FIF_FUNCNAME`\
Zainicjuj/Użyj `m_bstrFuncName` pola.

`FIF_RETURNTYPE`\
Zainicjuj/Użyj `m_bstrReturnType` pola.

`FIF_ARGS`\
Zainicjuj/Użyj `m_bstrArgs` pola.

`FIF_LANGUAGE`\
Zainicjuj/Użyj `m_bstrLanguage` pola.

`FIF_MODULE`\
Zainicjuj/Użyj `m_bstrModule` pola.

`FIF_STACKRANGE`\
Zainicjuj/Użyj `m_addrMin` `m_addrMax` pól i (zakres stosu).

`FIF_FRAME`\
Zainicjuj/Użyj `m_pFrame` pola.

`FIF_DEBUGINFO`\
Zainicjuj/Użyj `m_fHasDebugInfo` pola.

`FIF_STALECODE`\
Zainicjuj/Użyj `m_fStaleCode` pola.

`FIF_ANNOTATEDFRAME`\
Zainicjuj/Użyj `m_fAnnotatedFrame` pola.

`FIF_DEBUG_MODULEP`\
Zainicjuj/Użyj `m_pModule` pola.

`FIF_FUNCNAME_FORMAT`\
Formatuje nazwę funkcji. Wynik jest zwracany w `m_bstrFunName` polu i żadne inne pola nie są wypełnione.

`FIF_FUNCNAME_RETURNTYPE`\
Dodaje zwracany typ do `m_bstrFuncName` pola.

`FIF_FUNCNAME_ARGS`\
Dodaje argumenty do `m_bstrFuncName` pola.

`FIF_FUNCNAME_LANGUAGE`\
Dodaje język do `m_bstrFuncName` pola.

`FIF_FUNCNAME_MODULE`\
Dodaje nazwę modułu do `m_bstrFuncName` pola.

`FIF_FUNCNAME_LINES`\
Dodaje liczbę wierszy do `m_bstrFuncName` pola.

`FIF_FUNCNAME_OFFSET`\
Dodaje do `m_bstrFuncName` pola przesunięcie w bajtach od początku wiersza, jeśli `FIF_FUNCNAME_LINES` jest określony. Jeśli `FIF_FUNCNAME_LINES` nie jest określony lub numery wierszy nie są dostępne, program dodaje przesunięcie w bajtach od początku funkcji.

`FIF_FUNCNAME_ARGS_TYPES`\
Dodaje typ każdego argumentu funkcji do `m_bstrFuncName` pola.

`FIF_FUNCNAME_ARGS_NAMES`\
Dodaje nazwę każdego argumentu funkcji do `m_bstrFuncName` pola.

`FIF_FUNCNAME_ARGS_VALUES`\
Dodaje wartość każdego argumentu funkcji do `m_bstrFuncName` pola.

`FIF_FUNCNAME_ARGS_ALL`\
Dodaje typ, nazwę i wartość wszystkich argumentów do `m_bstrFuncName` pola.

`FIF_ARGS_TYPES`\
Typy argumentów są pobierane i formatowane.

`FIF_ARGS_NAMES`\
Nazwy argumentów są pobierane i formatowane.

`FIF_ARGS_VALUES`\
Wartości argumentów są pobierane i formatowane.

`FIF_ARGS_ALL`\
Pobierz i sformatuj typ, nazwę i wartość wszystkich argumentów.

`FIF_ARGS_NOFORMAT`\
Określa, że argumenty nie są formatowane (na przykład nie należy dodawać nawiasów otwierających i zamykających wokół listy argumentów ani dodawać separatora między argumentami).

`FIF_ARGS_NO_FUNC_EVAL`\
Określa, że podczas pobierania wartości argumentów nie należy używać oceny funkcji (właściwości).

`FIF_FILTER_NON_USER_CODE`\
Aparat debugowania przefiltruje ramki kodu niebędące użytkownikami, więc nie są one uwzględniane.

`FIF_ARGS_NO_TOSTRING`\
Nie Zezwalaj na `ToString()` Obliczanie ani formatowanie funkcji podczas zwracania argumentów funkcji.

`FIF_DESIGN_TIME_EXPR_EVAL`\
Informacje o ramce powinny być uzyskane z hostowanej domeny aplikacji, a nie procesu hostingu.

## <a name="remarks"></a>Uwagi
Te flagi są przekazywane do metod [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) i [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md) , aby wskazać, które pola mają być inicjowane w strukturze lub strukturach [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) .

Te flagi są również używane do wskazywania, które pola struktury [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) są używane i są ważne podczas zwracania struktury. Te wartości mogą być połączone z bitową `OR` .

## <a name="requirements"></a>Wymagania
Nagłówek: Msdbg. h

Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
- [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)
