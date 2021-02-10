---
title: EXCEPTION_STATE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EXCEPTION_STATE
helpviewer_keywords:
- EXCEPTION_STATE enumeration
ms.assetid: 597f4f4c-9b70-485c-b5dc-3c2e3aecc664
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f804f9a47314bfd239e6904286122776977e92e7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99936928"
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
Nie przerywaj z powodu wyjątku.

`EXCEPTION_STOP_FIRST_CHANCE`\
Zatrzymaj przy pierwszym wyzwalaniu wyjątku. W przypadku opisywania zdarzenia wyjątku ta flaga wskazuje, że zdarzenie wyjątku jest zdarzeniem wyjątku pierwszej szansy.

`EXCEPTION_STOP_SECOND_CHANCE`\
Zatrzymaj przy drugim zapłonie wyjątku. Podczas opisywania zdarzenia wyjątku wskazuje, że zdarzenie wyjątku jest zdarzeniem wyjątku drugiej szansy.

`EXCEPTION_STOP_USER_FIRST_CHANCE`\
Zatrzymaj podczas pierwszego uruchamiania wyjątku trybu użytkownika. Podczas opisywania zdarzenia wyjątku wskazuje, że zdarzenie wyjątku jest zdarzeniem wyjątku użytkownika pierwszej szansy.

`EXCEPTION_STOP_USER_UNCAUGHT`\
Zatrzymaj, gdy nie przechwycono wyjątku trybu użytkownika. Podczas opisywania zdarzenia wyjątku wskazuje, że zdarzenie wyjątku jest nieprzechwycone zdarzenie wyjątku trybu użytkownika.

`EXCEPTION_STOP_ALL`\
Zatrzymaj na dowolnym wyjątku. Nieużywane podczas opisywania zdarzenia wyjątku.

`EXCEPTION_CANNOT_BE_CONTINUED`\
Podczas opisywania zdarzenia wyjątku, wskazuje, że nie można kontynuować z powodu wyjątku.

`EXCEPTION_CODE_SUPPORTED`\
Wskazuje, że wyjątek ma kod obsługujący go. Używane podczas wyświetlania wyjątku

`EXCEPTION_CODE_DISPLAY_IN_HEX`\
Wskazuje, że kod wyjątku powinien być wyświetlany w formacie szesnastkowym. Używane podczas wyświetlania wyjątku.

`EXCEPTION_JUST_MY_CODE_SUPPORTED`\
Wskazuje, że kod wyjątku obsługuje JustMyCode. Używane podczas wyświetlania wyjątku.

`EXCEPTION_MANAGED_DEBUG_ASSISTANT`\
Wskazuje, że debuger kodu zarządzanego powinien obsługiwać wyjątki. Jeśli nie zostanie ustawiona, domyślny Debuger obsługuje wyjątki. Jest ona przenoszona do metody [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) i nie jest używana w strukturze [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) .

`EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT`\
PRZESTARZAŁE, NIE UŻYWAJ.

`EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT`\
PRZESTARZAŁE, NIE UŻYWAJ.

`EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT`\
PRZESTARZAŁE, NIE UŻYWAJ.

`EXCEPTION_STOP_USER_SECOND_CHANCE_USE_PARENT`\
PRZESTARZAŁE, NIE UŻYWAJ.

## <a name="remarks"></a>Uwagi
Używany jako `dwState` element członkowski struktury [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) , aby wskazać stan wyjątku i jak można go wykonać.

Te wartości są również przesyłane do metody [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) w celu ustawienia stanu wszystkich wyjątków.

Flagi te mogą być połączone z bitowym lub.

## <a name="requirements"></a>Wymagania
Nagłówek: Msdbg. h

Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
- [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)
