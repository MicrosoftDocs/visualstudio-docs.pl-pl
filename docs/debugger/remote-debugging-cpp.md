---
title: Debugowanie zdalne projektu w języku C++ | Microsoft Docs
description: Dowiedz się, jak debugować aplikację Visual Studio C++ z komputera zdalnego, wykonując następujące instrukcje krok po kroku.
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
ms.openlocfilehash: a8d3b578e62b917a7553b42a04e53062c406c4fd
ms.sourcegitcommit: 105e7b5a486262bc92939980383ceee068098a11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/30/2020
ms.locfileid: "97815805"
---
# <a name="remote-debugging-a-c-project-in-visual-studio"></a>Zdalne debugowanie projektu języka C++ w programie Visual Studio
Aby debugować aplikację programu Visual Studio na innym komputerze, zainstaluj i Uruchom narzędzia zdalne na komputerze, na którym zostanie wdrożona aplikacja, skonfiguruj projekt do łączenia się z komputerem zdalnym z programu Visual Studio, a następnie wdróż i uruchom aplikację.

![Składniki debugera zdalnego](../debugger/media/remote-debugger-client-apps.png "Remote_debugger_components")

Aby uzyskać informacje o zdalnym debugowaniu aplikacji systemu Windows (platformy UWP), zobacz [debugowanie zainstalowanego pakietu aplikacji](debug-installed-app-package.md).

## <a name="requirements"></a>Wymagania

Zdalny debuger jest obsługiwany w systemie Windows 7 i nowszych (nie Phone) oraz wersjach systemu Windows Server począwszy od systemu Windows Server 2008 z dodatkiem Service Pack 2. Aby uzyskać pełną listę wymagań, zobacz [wymagania](../debugger/remote-debugging.md#requirements_msvsmon).

> [!NOTE]
> Debugowanie między dwoma komputerami połączonymi za pomocą serwera proxy nie jest obsługiwane. Debugowanie w przypadku dużych opóźnień lub połączeń o niskiej przepustowości, takich jak Internet telefoniczny lub przez Internet w różnych krajach, nie jest zalecane i może się nie powieść.

## <a name="download-and-install-the-remote-tools"></a>Pobieranie i Instalowanie narzędzi zdalnych

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

> [!TIP]
> W niektórych scenariuszach może być najbardziej wydajne uruchamianie zdalnego debugera z udziału plików. Aby uzyskać więcej informacji, zobacz [Uruchamianie zdalnego debugera z udziału plików](../debugger/remote-debugging.md#fileshare_msvsmon).

## <a name="set-up-the-remote-debugger"></a><a name="BKMK_setup"></a> Konfigurowanie zdalnego debugera

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Jeśli musisz dodać uprawnienia dla dodatkowych użytkowników, zmienić tryb uwierzytelniania lub numer portu dla zdalnego debugera, zobacz [Konfigurowanie zdalnego debugera](../debugger/remote-debugging.md#configure_msvsmon).

## <a name="remote-debug-a-c-project"></a><a name="remote_cplusplus"></a> Debugowanie zdalne projektu C++
 W poniższej procedurze nazwa i ścieżka projektu to C:\remotetemp\MyMfc, a nazwa komputera zdalnego to **MJO-DL**.

1. Utwórz aplikację MFC o nazwie **mymfc.**

2. Ustaw punkt przerwania w aplikacji, która jest łatwo dostępna, na przykład w **MainFrm. cpp**, na początku `CMainFrame::OnCreate` .

3. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Właściwości**. Otwórz kartę **debugowanie** .

4. Ustaw **debuger do uruchamiania** na **zdalny debuger systemu Windows**.

    ![Zrzut ekranu karty debugowanie we właściwościach Eksplorator rozwiązań programu Visual Studio. Właściwość debuger do uruchomienia jest ustawiona na zdalny debuger systemu Windows.](../debugger/media/remotedebuggingcplus.png)

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

    ![Zrzut ekranu przedstawiający Configuration Manager w Eksplorator rozwiązań programu Visual Studio. Wybrana jest Konfiguracja debugowania, a wdrożenie jest zaznaczone.](../debugger/media/remotedebugcplusdeploy.png)

8. Rozpocznij debugowanie (**debuguj > rozpocząć debugowanie** lub **F5**).

9. Plik wykonywalny jest automatycznie wdrażany na komputerze zdalnym.

10. Jeśli zostanie wyświetlony monit, wprowadź poświadczenia sieciowe, aby nawiązać połączenie z maszyną zdalną.

     Wymagane poświadczenia są specyficzne dla konfiguracji zabezpieczeń sieci. Na przykład na komputerze domeny można wybrać certyfikat zabezpieczeń lub podać nazwę domeny i hasło. Na komputerze niebędącym domeną możesz wprowadzić nazwę komputera i prawidłową nazwę konta użytkownika, na przykład <strong>MJO-DL\name@something.com</strong> , wraz z prawidłowym hasłem.

11. Na komputerze z Visual Studio powinno być widoczne, że wykonywanie zostało zatrzymane w punkcie przerwania.

    > [!TIP]
    > Alternatywnie można wdrożyć pliki w osobnym kroku. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy węzeł **MyMfc** **,** a następnie wybierz polecenie **Wdróż**.

    Jeśli masz pliki inne niż kod, które są wymagane przez aplikację, możesz je określić w **dodatkowych plikach do wdrożenia** na stronie **zdalnego debugera systemu Windows** .

    Alternatywnie można uwzględnić pliki w projekcie i ustawić właściwość **Content** na **wartość Yes (tak** ) na stronie **Właściwości** dla każdego pliku. Te pliki są kopiowane do **katalogu wdrożenia** określonego na stronie **zdalnego debugera systemu Windows** . Możesz również zmienić **Typ elementu** na **Kopiuj plik** i określić dodatkowe właściwości tam, gdzie pliki mają być kopiowane do podfolderu **katalogu wdrożenia**.

## <a name="set-up-debugging-with-remote-symbols"></a>Konfigurowanie debugowania ze zdalnymi symbolami

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]

## <a name="see-also"></a>Zobacz też
- [Debugowanie w Visual Studio](../debugger/index.yml)
- [Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md)
- [Konfigurowanie zapory systemu Windows na potrzeby debugowania zdalnego](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Przypisania portów zdalnego debugera](../debugger/remote-debugger-port-assignments.md)
- [Zdalne debugowanie platformy ASP.NET na komputerze zdalnym usług IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)
- [Błędy debugowania zdalnego i rozwiązywanie problemów](../debugger/remote-debugging-errors-and-troubleshooting.md)