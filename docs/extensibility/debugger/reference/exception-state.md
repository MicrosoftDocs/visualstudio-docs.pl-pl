---
title: EXCEPTION_STATE | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EXCEPTION_STATE
helpviewer_keywords:
- EXCEPTION_STATE enumeration
ms.assetid: 597f4f4c-9b70-485c-b5dc-3c2e3aecc664
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cd2e280cd03ae413e0853950d13fbfefb69bc15f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736959"
---
# <a name="exception_state"></a>EXCEPTION_STATE
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
Nie zatrzymuj się na wyjątek.

`EXCEPTION_STOP_FIRST_CHANCE`\
Zatrzymaj się przy pierwszym wypalaniu wyjątku. Opisując zdarzenie wyjątku, ta flaga wskazuje, że zdarzenie wyjątku jest zdarzeniem wyjątku pierwszej szansy.

`EXCEPTION_STOP_SECOND_CHANCE`\
Zatrzymaj się przy drugim wypalaniu wyjątku. Opisując zdarzenie wyjątku, wskazuje, że zdarzenie wyjątku jest zdarzeniem wyjątku drugiej szansy.

`EXCEPTION_STOP_USER_FIRST_CHANCE`\
Zatrzymaj przy pierwszym wypalania wyjątku trybu użytkownika. Opisując zdarzenie wyjątku, wskazuje, że zdarzenie wyjątku jest zdarzeniem wyjątku użytkownika pierwszej szansy.

`EXCEPTION_STOP_USER_UNCAUGHT`\
Zatrzymaj, gdy wyjątek trybu użytkownika nie zostanie przechwycony. Opisując zdarzenie wyjątku, wskazuje, że zdarzenie wyjątku jest nieprzychyne zdarzenie wyjątku trybu użytkownika.

`EXCEPTION_STOP_ALL`\
Zatrzymaj się na każdym wyjątku. Nie jest używany podczas opisywania zdarzenia wyjątku.

`EXCEPTION_CANNOT_BE_CONTINUED`\
Opisując zdarzenie wyjątku, wskazuje, że wyjątek nie może być kontynuowany z.

`EXCEPTION_CODE_SUPPORTED`\
Wskazuje, że wyjątek ma kod obsługujący go. Używany do wyświetlania wyjątku

`EXCEPTION_CODE_DISPLAY_IN_HEX`\
Wskazuje, że kod wyjątku powinien być wyświetlany w szesnastkowej. Używane do wyświetlania wyjątku.

`EXCEPTION_JUST_MY_CODE_SUPPORTED`\
Wskazuje, że kod wyjątku obsługuje JustMyCode. Używane do wyświetlania wyjątku.

`EXCEPTION_MANAGED_DEBUG_ASSISTANT`\
Wskazuje, że debuger kodu zarządzanego powinien obsługiwać wyjątki. Jeśli nie jest ustawiona, debuger domyślny obsługuje wyjątki. Jest to przekazywane do [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) metody i nie jest używany w [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) struktury.

`EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT`\
PRZESTARZAŁE, NIE UŻYWAĆ.

`EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT`\
PRZESTARZAŁE, NIE UŻYWAĆ.

`EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT`\
PRZESTARZAŁE, NIE UŻYWAĆ.

`EXCEPTION_STOP_USER_SECOND_CHANCE_USE_PARENT`\
PRZESTARZAŁE, NIE UŻYWAĆ.

## <a name="remarks"></a>Uwagi
Używany jako `dwState` element członkowski [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) struktury, aby wskazać stan wyjątku i co można z nim zrobić.

Te wartości są również przekazywane do [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) metody, aby ustawić stan wszystkich wyjątków.

Flagi te mogą być łączone z bitowym OR.

## <a name="requirements"></a>Wymagania
Nagłówek: msdbg.h

Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
- [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)
