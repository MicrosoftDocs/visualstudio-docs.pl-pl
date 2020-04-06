---
title: FRAMEINFO_FLAGS | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FRAMEINFO_FLAGS
helpviewer_keywords:
- FRAMEINFO_FLAGS enumeration
ms.assetid: 41578062-8455-412a-9d8b-1e1e9dc8d52e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3510726400623c5ddf3e7a4d58a4903763b91245
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736798"
---
# <a name="frameinfo_flags"></a>FRAMEINFO_FLAGS
Określa informacje o obiekcie ramki stosu.

## <a name="syntax"></a>Składnia

```cpp
enum enum_FRAMEINFO_FLAGS {
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
public enum enum_FRAMEINFO_FLAGS {
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
Inicjowanie/używanie tego `m_bstrFuncName` pola.

`FIF_RETURNTYPE`\
Inicjowanie/używanie tego `m_bstrReturnType` pola.

`FIF_ARGS`\
Inicjowanie/używanie tego `m_bstrArgs` pola.

`FIF_LANGUAGE`\
Inicjowanie/używanie tego `m_bstrLanguage` pola.

`FIF_MODULE`\
Inicjowanie/używanie tego `m_bstrModule` pola.

`FIF_STACKRANGE`\
Inicjuj/użyj pól `m_addrMin` (zakres `m_addrMax` stosu).

`FIF_FRAME`\
Inicjowanie/używanie tego `m_pFrame` pola.

`FIF_DEBUGINFO`\
Inicjowanie/używanie tego `m_fHasDebugInfo` pola.

`FIF_STALECODE`\
Inicjowanie/używanie tego `m_fStaleCode` pola.

`FIF_ANNOTATEDFRAME`\
Inicjowanie/używanie tego `m_fAnnotatedFrame` pola.

`FIF_DEBUG_MODULEP`\
Inicjowanie/używanie tego `m_pModule` pola.

`FIF_FUNCNAME_FORMAT`\
Formatuje nazwę funkcji. Wynik jest zwracany `m_bstrFunName` w polu i żadne inne pola nie są wypełniane.

`FIF_FUNCNAME_RETURNTYPE`\
Dodaje typ zwracany `m_bstrFuncName` do pola.

`FIF_FUNCNAME_ARGS`\
Dodaje argumenty do `m_bstrFuncName` pola.

`FIF_FUNCNAME_LANGUAGE`\
Dodaje język do `m_bstrFuncName` pola.

`FIF_FUNCNAME_MODULE`\
Dodaje nazwę modułu `m_bstrFuncName` do tego pola.

`FIF_FUNCNAME_LINES`\
Dodaje liczbę wierszy `m_bstrFuncName` do pola.

`FIF_FUNCNAME_OFFSET`\
Dodaje do `m_bstrFuncName` pola przesunięcie w bajtach od `FIF_FUNCNAME_LINES` początku wiersza, jeśli jest określony. Jeśli `FIF_FUNCNAME_LINES` nie jest określony lub jeśli numery wierszy nie są dostępne, dodaje przesunięcie w bajtach od początku funkcji.

`FIF_FUNCNAME_ARGS_TYPES`\
Dodaje typ każdego argumentu `m_bstrFuncName` funkcji do pola.

`FIF_FUNCNAME_ARGS_NAMES`\
Dodaje nazwę każdego argumentu `m_bstrFuncName` funkcji do pola.

`FIF_FUNCNAME_ARGS_VALUES`\
Dodaje wartość każdego argumentu `m_bstrFuncName` funkcji do pola.

`FIF_FUNCNAME_ARGS_ALL`\
Dodaje do `m_bstrFuncName` pola typ, nazwę i wartość wszystkich argumentów.

`FIF_ARGS_TYPES`\
Typy argumentów są pobierane i formatowane.

`FIF_ARGS_NAMES`\
Nazwy argumentów są pobierane i formatowane.

`FIF_ARGS_VALUES`\
Wartości argumentów są pobierane i formatowane.

`FIF_ARGS_ALL`\
Pobieranie i formatowanie typu, nazwy i wartości wszystkich argumentów.

`FIF_ARGS_NOFORMAT`\
Określa, że argumenty nie są formatowane (na przykład nie należy dodawać nawiasów otwierania i zamykania wokół listy argumentów ani nie dodawać separatora między argumentami).

`FIF_ARGS_NO_FUNC_EVAL`\
Określa, że ocena funkcji (właściwości) nie powinna być używana podczas pobierania wartości argumentów.

`FIF_FILTER_NON_USER_CODE`\
Aparat debugowania jest filtrowanie ramek kodu innych niż użytkownik, więc nie są one uwzględniane.

`FIF_ARGS_NO_TOSTRING`\
Nie zezwalaj na `ToString()` ocenę funkcji lub formatowanie podczas zwracania argumentów funkcji.

`FIF_DESIGN_TIME_EXPR_EVAL`\
Informacje o ramce powinny być ujmowane z hostowanego domeny aplikacji, a nie z procesu hostingu.

## <a name="remarks"></a>Uwagi
Flagi te są przekazywane do [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) i [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md) metody, aby wskazać, które pola mają być inicjowane w [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) struktury lub struktur.

Flagi te są również używane do wskazania, które pola [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) struktury są używane i prawidłowe, gdy struktura jest zwracana. Wartości te mogą być łączone z bitowym `OR`.

## <a name="requirements"></a>Wymagania
Nagłówek: msdbg.h

Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
- [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)
