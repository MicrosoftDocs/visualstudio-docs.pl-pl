---
title: 'Błąd: Debugowanie nie jest&#39;t możliwe ponieważ w systemie jest włączony debuger jądra | Dokumentacja firmy Microsoft'
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
ms.openlocfilehash: c35910a7682d4e9a6d848f270dd8d6c86e4bd850
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54954153"
---
# <a name="error-debugging-isn39t-possible-because-a-kernel-debugger-is-enabled-on-the-system"></a>Błąd: Debugowanie nie jest&#39;t możliwe ponieważ w systemie jest włączony debuger jądra
Podczas debugowania kodu zarządzanego, mogą pojawić się następujący komunikat o błędzie:  
  
```cmd
Debugging isn't possible because a kernel debugger is enabled on the system  
```  
  
 Ten komunikat występuje podczas próby debugowania kodu zarządzanego:  
  
- na [!INCLUDE[win7](../debugger/includes/win7_md.md)] lub [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)]system, który został uruchomiony w trybie debugowania.  
  
- aplikacja korzysta z wersji środowiska CLR CLR 2.0, 3.0 lub 3.5.  
  
## <a name="solution"></a>Rozwiązanie  
  
#### <a name="to-fix-this-problem"></a>Aby rozwiązać ten problem  
  
- Uaktualnianie aplikacji do użycia środowisko CLR w wersji 4.0 lub 4.5  
  
   —lub—  
  
- Wyłącz debugowanie jądra i debugowanie w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
   —lub—  
  
- Debugowanie za pomocą debugera jądra zamiast [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
   —lub—  
  
- W debugerze jądra wyłączyć wyjątki trybu użytkownika.  
  
#### <a name="to-disable-kernel-debugging-in-the-current-session"></a>Aby wyłączyć debugowanie jądra w bieżącej sesji  
  
-   W wierszu polecenia wpisz polecenie:  
  
    ```cmd
    Kdbgctrl.exe -d  
    ```  
  
#### <a name="to-disable-kernel-debugging-for-all-sessions-windows-vista-and-windows-7"></a>Aby wyłączyć debugowanie jądra dla wszystkich sesji (Windows Vista i Windows 7)  
  
1.  W wierszu polecenia wpisz polecenie:  
  
    ```cmd
    bcdedit /debug off   
    ```  
  
2.  Uruchom ponownie komputer.  
  
#### <a name="to-disable-kernel-debugging-for-all-sessions-other-windows-operating-systems"></a>Aby wyłączyć debugowanie jądra dla wszystkich sesji (inne systemy operacyjne Windows)  
  
1.  Zlokalizuj plik boot.ini na dysku systemowym (zwykle C:\\). Plik boot.ini może być ukryta i tylko do odczytu. W związku z tym należy użyć następujące polecenia, aby zobaczyć, jak to:  
  
    ```cmd
    dir /ASH  
    ```  
  
2.  Otwórz plik boot.ini za pomocą Notatnika i Usuń następujące opcje:  
  
    ```cmd
    /debug  
    /debugport  
    /baudrate  
    ```  
  
3.  Uruchom ponownie komputer.  
  
#### <a name="to-debug-with-the-kernel-debugger"></a>Aby debugować z debuger jądra  
  
1.  Jeśli debuger jądra jest podłączany, zobaczysz komunikat z pytaniem, czy chcesz kontynuować debugowanie. Kliknij przycisk Tak, aby kontynuować.  
  
2.  Możesz otrzymać `User break exception(Int 3).` w takiej sytuacji wpisz następujące polecenie debuger jądra, aby kontynuować debugowanie:  
  
     `gn`  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczenia debugera](../debugger/debugger-security.md)   
 [Debugowanie kodu zarządzanego](../debugger/debugging-managed-code.md)
