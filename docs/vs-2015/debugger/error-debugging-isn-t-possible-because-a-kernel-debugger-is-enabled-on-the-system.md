---
title: 'Błąd: Debugowanie nie jest&#39;t możliwe ponieważ w systemie jest włączony debuger jądra | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.kernel_dbg_enabled
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
- CSharp
- C++
helpviewer_keywords:
- kernel debugger
ms.assetid: 630a7abd-3303-4aaa-888a-6de3de14bc01
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cdc000a4ad825be495c28bb59d35f8ef378c563f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54781747"
---
# <a name="error-debugging-isn39t-possible-because-a-kernel-debugger-is-enabled-on-the-system"></a>Błąd: Debugowanie nie jest&#39;t możliwe ponieważ w systemie jest włączony debuger jądra
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podczas debugowania kodu zarządzanego, mogą pojawić się następujący komunikat o błędzie:  
  
```  
Debugging isn't possible because a kernel debugger is enabled on the system  
```  
  
 Ten komunikat występuje podczas próby debugowania kodu zarządzanego:  
  
-   na [!INCLUDE[win7](../includes/win7-md.md)] lub [!INCLUDE[wiprlhext](../includes/wiprlhext-md.md)]system, który został uruchomiony w trybie debugowania.  
  
-   aplikacja korzysta z wersji środowiska CLR CLR 2.0, 3.0 lub 3.5.  
  
## <a name="solution"></a>Rozwiązanie  
  
#### <a name="to-fix-this-problem"></a>Aby rozwiązać ten problem  
  
-   Uaktualnianie aplikacji do użycia środowisko CLR w wersji 4.0 lub 4.5  
  
     —lub—  
  
-   Wyłącz debugowanie jądra i debugowanie w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
     —lub—  
  
-   Debugowanie za pomocą debugera jądra zamiast [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
     —lub—  
  
-   W debugerze jądra wyłączyć wyjątki trybu użytkownika.  
  
#### <a name="to-disable-kernel-debugging-in-the-current-session"></a>Aby wyłączyć debugowanie jądra w bieżącej sesji  
  
-   W wierszu polecenia wpisz polecenie:  
  
    ```  
    Kdbgctrl.exe -d  
    ```  
  
#### <a name="to-disable-kernel-debugging-for-all-sessions-windows-vista-and-windows-7"></a>Aby wyłączyć debugowanie jądra dla wszystkich sesji (Windows Vista i Windows 7)  
  
1.  W wierszu polecenia wpisz polecenie:  
  
    ```  
    bcdedit /debug off   
    ```  
  
2.  Uruchom ponownie komputer.  
  
#### <a name="to-disable-kernel-debugging-for-all-sessions-other-windows-operating-systems"></a>Aby wyłączyć debugowanie jądra dla wszystkich sesji (inne systemy operacyjne Windows)  
  
1.  Zlokalizuj plik boot.ini na dysku systemowym (zwykle C:\\). Plik boot.ini może być ukryta i tylko do odczytu. W związku z tym należy użyć następujące polecenia, aby zobaczyć, jak to:  
  
    ```  
    dir /ASH  
    ```  
  
2.  Otwórz plik boot.ini za pomocą Notatnika i Usuń następujące opcje:  
  
    ```  
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
