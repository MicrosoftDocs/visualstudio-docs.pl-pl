---
title: 'Błąd: debugowanie jest&#39;t jest możliwe, ponieważ debuger jądra jest włączony w systemie | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.kernel_dbg_enabled
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- kernel debugger
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2a966869ff1d200a51c6019a6ae937bea7c447bd
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72737745"
---
# <a name="error-debugging-isn39t-possible-because-a-kernel-debugger-is-enabled-on-the-system"></a>Błąd: debugowanie jest&#39;t jest możliwe, ponieważ w systemie jest włączony debuger jądra
Podczas debugowania kodu zarządzanego może zostać wyświetlony następujący komunikat o błędzie:

```cmd
Debugging isn't possible because a kernel debugger is enabled on the system
```

 Ten komunikat występuje podczas próby debugowania kodu zarządzanego:

- w systemie [!INCLUDE[win7](../debugger/includes/win7_md.md)] lub [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)], który został uruchomiony w trybie debugowania.

- aplikacja używa środowiska CLR w wersji 2,0, 3,0 lub 3,5.

## <a name="solution"></a>Rozwiązanie

#### <a name="to-fix-this-problem"></a>Aby rozwiązać ten problem

- Uaktualnij aplikację do korzystania z aparatu CLR w wersji 4,0 lub 4,5

   —lub—

- Wyłącz debugowanie jądra i debugowanie w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

   —lub—

- Debuguj przy użyciu debugera jądra zamiast [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

   —lub—

- W debugerze jądra Wyłącz wyjątki w trybie użytkownika.

#### <a name="to-disable-kernel-debugging-in-the-current-session"></a>Aby wyłączyć debugowanie jądra w bieżącej sesji

- W wierszu polecenia wpisz polecenie:

    ```cmd
    Kdbgctrl.exe -d
    ```

#### <a name="to-disable-kernel-debugging-for-all-sessions-windows-vista-and-windows-7"></a>Aby wyłączyć debugowanie jądra dla wszystkich sesji (Windows Vista i Windows 7)

1. W wierszu polecenia wpisz polecenie:

    ```cmd
    bcdedit /debug off
    ```

2. Uruchom ponownie komputer.

#### <a name="to-disable-kernel-debugging-for-all-sessions-other-windows-operating-systems"></a>Aby wyłączyć debugowanie jądra dla wszystkich sesji (inne systemy operacyjne Windows)

1. Zlokalizuj plik Boot. ini na dysku systemowym (zazwyczaj C:\\). Plik Boot. ini może być ukryty i tylko do odczytu. W związku z tym należy użyć następującego polecenia, aby je wyświetlić:

    ```cmd
    dir /ASH
    ```

2. Otwórz plik Boot. ini przy użyciu programu Notepad i Usuń następujące opcje:

    ```cmd
    /debug
    /debugport
    /baudrate
    ```

3. Uruchom ponownie komputer.

#### <a name="to-debug-with-the-kernel-debugger"></a>Aby debugować za pomocą debugera jądra

1. Jeśli debuger jądra zostanie podłączony, zobaczysz komunikat z pytaniem, czy chcesz kontynuować debugowanie. Kliknij przycisk, aby kontynuować.

2. Jeśli wystąpi taka sytuacja, możesz uzyskać `User break exception(Int 3).` w takim przypadku wpisz następujące polecenie debugera jądra, aby kontynuować debugowanie:

     `gn`

## <a name="see-also"></a>Zobacz także
- [Zabezpieczenia debugera](../debugger/debugger-security.md)
- [Debugowanie kodu zarządzanego](../debugger/debugging-managed-code.md)
