---
title: Debugowanie jest &apos; t możliwy, ponieważ debuger jądra jest włączony w systemie | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a06ed9092145188bf5fbecd2caeb42f5ad5c2e3a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871770"
---
# <a name="error-debugging-isn39t-possible-because-a-kernel-debugger-is-enabled-on-the-system"></a>Błąd: debugowanie jest&#39;t możliwy, ponieważ w systemie jest włączony debuger jądra
Podczas debugowania kodu zarządzanego może zostać wyświetlony następujący komunikat o błędzie:

```cmd
Debugging isn't possible because a kernel debugger is enabled on the system
```

 Ten komunikat występuje podczas próby debugowania kodu zarządzanego:

- w [!INCLUDE[win7](../debugger/includes/win7_md.md)] systemie lub [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)] , który został uruchomiony w trybie debugowania.

- aplikacja używa środowiska CLR w wersji 2,0, 3,0 lub 3,5.

## <a name="solution"></a>Rozwiązanie

#### <a name="to-fix-this-problem"></a>Aby rozwiązać ten problem

- Uaktualnij aplikację do korzystania z aparatu CLR w wersji 4,0 lub 4,5

   —lub—

- Wyłącz debugowanie jądra i Debuguj w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

   —lub—

- Debuguj przy użyciu debugera jądra zamiast [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

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

1. Znajdź boot.ini na dysku systemowym (zazwyczaj C: \\ ). Plik boot.ini może być ukryty i tylko do odczytu. W związku z tym należy użyć następującego polecenia, aby je wyświetlić:

    ```cmd
    dir /ASH
    ```

2. Otwórz boot.ini przy użyciu Notatnika i Usuń następujące opcje:

    ```cmd
    /debug
    /debugport
    /baudrate
    ```

3. Uruchom ponownie komputer.

#### <a name="to-debug-with-the-kernel-debugger"></a>Aby debugować za pomocą debugera jądra

1. Jeśli debuger jądra zostanie podłączony, zobaczysz komunikat z pytaniem, czy chcesz kontynuować debugowanie. Kliknij przycisk, aby kontynuować.

2. Może się pojawić w `User break exception(Int 3).` razie wystąpienia tego problemu, aby kontynuować debugowanie, wpisz następujące polecenie debugera jądra:

     `gn`

## <a name="see-also"></a>Zobacz też
- [Zabezpieczenia debugera](../debugger/debugger-security.md)
- [Debugowanie zarządzanego kodu](../debugger/debugging-managed-code.md)
