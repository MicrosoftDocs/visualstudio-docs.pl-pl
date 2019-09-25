---
title: Debugowanie zdalne projektu wizualnego C++ | Microsoft Docs
ms.custom: remotedebugging
ms.date: 08/14/2018
ms.topic: conceptual
dev_langs:
- C++
- FSharp
- CSharp
- JScript
- VB
helpviewer_keywords:
- remote debugging, setup
ms.assetid: 8b8eca0d-122f-4eda-848a-cf0945f207d0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 81a5ebba2d14a0e091b3b0bcd78a066ef50ed759
ms.sourcegitcommit: ea182703e922c74725045afc251bcebac305068a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71211114"
---
# <a name="remote-debugging-a-visual-c-project-in-visual-studio"></a>Debugowanie zdalne projektu wizualizacji C++ w Visual Studio
Aby debugować aplikację programu Visual Studio na innym komputerze, zainstaluj i Uruchom narzędzia zdalne na komputerze, na którym zostanie wdrożona aplikacja, skonfiguruj projekt do łączenia się z komputerem zdalnym z programu Visual Studio, a następnie wdróż i uruchom aplikację.

![Składniki zdalnego debugera](../debugger/media/remote-debugger-client-apps.png "Remote_debugger_components")

Aby dowiedzieć się, zdalne debugowanie Universal Windows Apps (platformy UWP), zobacz [debugowanie zainstalowanego pakietu aplikacji](debug-installed-app-package.md).

## <a name="requirements"></a>Wymagania

Zdalny debuger jest obsługiwane w systemie Windows 7 lub nowszej (nie phone) i wersji systemu Windows Server, począwszy od systemu Windows Server 2008 Service Pack 2. Aby uzyskać pełną listę wymagań, zobacz [wymagania](../debugger/remote-debugging.md#requirements_msvsmon).

> [!NOTE]
> Debugowanie między dwoma komputerami połączonymi za pośrednictwem serwera proxy nie jest obsługiwane. Debugowanie za pośrednictwem duże opóźnienie lub połączenia o niskiej przepustowości, takich jak Internet, połączenia telefonicznego lub przez Internet między krajów nie jest zalecane i może zakończyć się niepowodzeniem lub zbyt wolno.

## <a name="download-and-install-the-remote-tools"></a>Pobieranie i instalowanie narzędzi zdalnych

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

> [!TIP]
> W niektórych scenariuszach może być najbardziej efektywny, aby uruchomić zdalny debuger z udziału plików. Aby uzyskać więcej informacji, zobacz [uruchomienia zdalnego debugera z udziału plików](../debugger/remote-debugging.md#fileshare_msvsmon).

## <a name="BKMK_setup"></a> Konfigurowanie debugera zdalnego

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Jeśli potrzebujesz dodać uprawnienia dla dodatkowych użytkowników do zmienić tryb uwierzytelniania lub numer portu dla zdalnego debugera, zobacz [Konfigurowanie debugera zdalnego](../debugger/remote-debugging.md#configure_msvsmon).

## <a name="remote_cplusplus"></a>Debugowanie zdalne projektu wizualnego C++
 W poniższej procedurze nazwa i ścieżka projektu to C:\remotetemp\MyMfc, a nazwa komputera zdalnego to **MJO-DL**.

1. Utwórz aplikację MFC o nazwie **mymfc.**

2. Ustaw punkt przerwania w aplikacji, która jest łatwo dostępna, na przykład w **MainFrm. cpp**, na początku `CMainFrame::OnCreate`.

3. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Właściwości**. Otwórz kartę **debugowanie** .

4. Ustaw **debuger do uruchamiania** na **zdalny debuger systemu Windows**.

    ![RemoteDebuggingCPlus](../debugger/media/remotedebuggingcplus.png "RemoteDebuggingCPlus")

5. Wprowadź następujące zmiany właściwości:

   |Ustawienie|Wartość|
   |-|-|
   |Polecenie zdalne|C:\remotetemp\mymfc.exe|
   |Katalog roboczy|C:\remotetemp|
   |Nazwa serwera zdalnego|MJO-DL:*numer_portu*|
   |Połączenie|Zdalne z uwierzytelnianiem systemu Windows|
   |Typ debugera|Tylko natywny|
   |Katalog wdrażania|C:\remotetemp.|
   |Dodatkowe pliki do wdrożenia|C:\data\mymfcdata.txt.|

    W przypadku wdrażania dodatkowych plików (opcjonalnie) folder musi istnieć na obu komputerach.

6. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy rozwiązanie i wybierz pozycję **Configuration Manager**.

7. W obszarze Konfiguracja **debugowania** zaznacz pole wyboru **Wdróż** .

    ![RemoteDebugCplusDeploy](../debugger/media/remotedebugcplusdeploy.png "RemoteDebugCplusDeploy")

8. Rozpocznij debugowanie (**debuguj > rozpocząć debugowanie**lub **F5**).

9. Plik wykonywalny jest automatycznie wdrażany na komputerze zdalnym.

10. Po wyświetleniu monitu wprowadź poświadczenia sieci, aby nawiązać połączenie z komputerem zdalnym.

     Wymagane poświadczenia są specyficzne dla konfiguracji zabezpieczeń sieci. Na przykład na komputerze domeny można wybrać certyfikat zabezpieczeń lub podać nazwę domeny i hasło. Na komputerze nienależących do domeny, wprowadzić nazwę komputera i prawidłową nazwę konta użytkownika, takie jak <strong>MJO-DL\name@something.com</strong>, oraz prawidłowe hasło.

11. Na komputerze z Visual Studio powinno być widoczne, że wykonywanie zostało zatrzymane w punkcie przerwania.

    > [!TIP]
    > Alternatywnie można wdrożyć pliki w osobnym kroku. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy węzeł **MyMfc** **,** a następnie wybierz polecenie **Wdróż**.

    Jeśli masz pliki inne niż kod, które są wymagane przez aplikację, możesz je określić w **dodatkowych plikach do wdrożenia** na stronie **zdalnego debugera systemu Windows** .

    Alternatywnie można uwzględnić pliki w projekcie i ustawić właściwość **Content** na **wartość Yes (tak** ) na stronie **Właściwości** dla każdego pliku. Te pliki są kopiowane do **katalogu wdrożenia** określonego na stronie **zdalnego debugera systemu Windows** . Możesz również zmienić **Typ elementu** na **Kopiuj plik** i określić dodatkowe właściwości tam, gdzie pliki mają być kopiowane do podfolderu **katalogu wdrożenia**.

## <a name="set-up-debugging-with-remote-symbols"></a>Konfigurowanie debugowania przy użyciu zdalnego symboli

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]

## <a name="see-also"></a>Zobacz też
- [Debugowanie w programie Visual Studio](../debugger/index.yml)
- [Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md)
- [Konfigurowanie zapory systemu Windows na potrzeby debugowania zdalnego](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Przypisania portów debugera zdalnego](../debugger/remote-debugger-port-assignments.md)
- [Zdalne debugowanie platformy ASP.NET na komputerze zdalnym usług IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)
- [Błędy związane z debugowaniem zdalnym i rozwiązywanie problemów](../debugger/remote-debugging-errors-and-troubleshooting.md)