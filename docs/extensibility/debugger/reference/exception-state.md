---
title: EXCEPTION_STATE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EXCEPTION_STATE
helpviewer_keywords:
- EXCEPTION_STATE enumeration
ms.assetid: 597f4f4c-9b70-485c-b5dc-3c2e3aecc664
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8f05596b12151b3a40b87c6fc2f15659a38e3431
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66337689"
---
# <a name="exceptionstate"></a>EXCEPTION_STATE
Określa stan wyjątku.

## <a name="syntax"></a>Składnia

```cpp
enum enum_EXCEPTION_STATE {
    EXCEPTION_NONE                          = 0x0000,
    EXCEPTION_STOP_FIRST_CHANCE             = 0x0001,
    EXCEPTION_STOP_SECOND_CHANCE            = 0x0002,
    EXCEPTION_STOP_USER_FIRST_CHANCE        = 0x0010,
    EXCEPTION_STOP_USER_UNCAUGHT            = 0x0020,
    EXCEPTION_STOP_ALL                      = 0x00FF,
    EXCEPTION_CANNOT_BE_CONTINUED           = 0x0100,

    // These are for exception types only
    EXCEPTION_CODE_SUPPORTED                = 0x1000,
    EXCEPTION_CODE_DISPLAY_IN_HEX           = 0x2000,
    EXCEPTION_JUST_MY_CODE_SUPPORTED        = 0x4000,
    EXCEPTION_MANAGED_DEBUG_ASSISTANT       = 0x8000,

    // These are no longer used
    EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT      = 0x0004,
    EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT     = 0x0008,
    EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT = 0x0040,
    EXCEPTION_STOP_USER_UNCAUGHT_USE_PARENT     = 0x0080,
};
typedef DWORD EXCEPTION_STATE;
```

```csharp
public enum enum_EXCEPTION_STATE {
    EXCEPTION_NONE                          = 0x0000,
    EXCEPTION_STOP_FIRST_CHANCE             = 0x0001,
    EXCEPTION_STOP_SECOND_CHANCE            = 0x0002,
    EXCEPTION_STOP_USER_FIRST_CHANCE        = 0x0010,
    EXCEPTION_STOP_USER_UNCAUGHT            = 0x0020,
    EXCEPTION_STOP_ALL                      = 0x00FF,
    EXCEPTION_CANNOT_BE_CONTINUED           = 0x0100,

    // These are for exception types only
    EXCEPTION_CODE_SUPPORTED                = 0x1000,
    EXCEPTION_CODE_DISPLAY_IN_HEX           = 0x2000,
    EXCEPTION_JUST_MY_CODE_SUPPORTED        = 0x4000,
    EXCEPTION_MANAGED_DEBUG_ASSISTANT       = 0x8000,

    // These are no longer used
    EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT      = 0x0004,
    EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT     = 0x0008,
    EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT = 0x0040,
    EXCEPTION_STOP_USER_UNCAUGHT_USE_PARENT     = 0x0080,
};
```

## <a name="fields"></a>Pola
`EXCEPTION_NONE`\
Nie zatrzymanie przy wyjątku.

`EXCEPTION_STOP_FIRST_CHANCE`\
Zatrzymaj przy pierwszym uruchomieniu którego wyjątku. W opisie zdarzenia wyjątków, ta flaga wskazuje, czy zdarzenie wyjątku jest zdarzenie wyjątku pierwszej szansy.

`EXCEPTION_STOP_SECOND_CHANCE`\
Zatrzymaj po uruchomieniu drugiego którego wyjątku. W opisie zdarzenia wyjątków, wskazuje zdarzenie wyjątku zdarzeń wyjątku szansy na sekundę.

`EXCEPTION_STOP_USER_FIRST_CHANCE`\
Zatrzymaj przy pierwszym uruchomieniu którego wyjątku trybu użytkownika. W opisie zdarzenia wyjątków, wskazuje zdarzenie wyjątku zdarzenie wyjątku pierwszej szansy użytkownika.

`EXCEPTION_STOP_USER_UNCAUGHT`\
Zatrzymaj, gdy nie przechwycono wyjątku trybu użytkownika. W opisie zdarzenia wyjątków, wskazuje zdarzenie wyjątku zdarzenie wyjątku tryb nieprzechwycony użytkownika.

`EXCEPTION_STOP_ALL`\
Zatrzymaj przy każdym wyjątku. Nie można używać w opisie zdarzenia wyjątku.

`EXCEPTION_CANNOT_BE_CONTINUED`\
W opisie zdarzenia wyjątków, wskazuje, że wyjątek nie może być kontynuowana z.

`EXCEPTION_CODE_SUPPORTED`\
Wskazuje, że wyjątek ma kod obsługi go. Służącego do wyświetlania wyjątek

`EXCEPTION_CODE_DISPLAY_IN_HEX`\
Wskazuje, że kod wyjątku powinien być wyświetlany w formacie szesnastkowym. Używany podczas wyświetlania wyjątek.

`EXCEPTION_JUST_MY_CODE_SUPPORTED`\
Wskazuje, że kod wyjątku obsługuje JustMyCode. Używany podczas wyświetlania wyjątek.

`EXCEPTION_MANAGED_DEBUG_ASSISTANT`\
Wskazuje, że debuger kodu zarządzanego powinna obsługiwać wyjątki. W przeciwnym razie zestawu, debuger domyślnej obsługi wyjątków. Te informacje są przekazywane do [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) metody i nie są używane w [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) struktury.

`EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT`\
PRZESTARZAŁE, NIE NALEŻY UŻYWAĆ.

`EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT`\
PRZESTARZAŁE, NIE NALEŻY UŻYWAĆ.

`EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT`\
PRZESTARZAŁE, NIE NALEŻY UŻYWAĆ.

`EXCEPTION_STOP_USER_SECOND_CHANCE_USE_PARENT`\
PRZESTARZAŁE, NIE NALEŻY UŻYWAĆ.

## <a name="remarks"></a>Uwagi
Używane jako `dwState` członkiem [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) strukturę, aby wskazać jej stan wyjątku i co można zrobić na jego temat.

Te wartości również są przekazywane do [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) metodę, aby ustawić stan wszystkich wyjątków.

Te flagi mogą być łączone z bitowe OR.

## <a name="requirements"></a>Wymagania
Header: msdbg.h

Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
- [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)
