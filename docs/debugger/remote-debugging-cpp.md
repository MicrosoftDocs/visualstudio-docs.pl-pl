---
title: Zdalne debugowanie projektu języka C++ | Dokumenty firmy Microsoft
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
ms.openlocfilehash: 0173ed557afa47129e0cc92d9ef9b2d94a7b198f
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302113"
---
# <a name="remote-debugging-a-c-project-in-visual-studio"></a>Zdalne debugowanie projektu języka C++ w programie Visual Studio
Aby debugować aplikację programu Visual Studio na innym komputerze, zainstaluj i uruchom narzędzia zdalne na komputerze, na którym można wdrożyć aplikację, skonfiguruj projekt tak, aby łączył się z komputerem zdalnym z programu Visual Studio, a następnie wdrażaj i uruchamiaj aplikację.

![Składniki zdalnego debugera](../debugger/media/remote-debugger-client-apps.png "Remote_debugger_components")

Aby uzyskać informacje dotyczące zdalnego debugowania uniwersalnych aplikacji systemu Windows (UWP), zobacz [Debugowanie zainstalowanego pakietu aplikacji](debug-installed-app-package.md).

## <a name="requirements"></a>Wymagania

Debuger zdalny jest obsługiwany w systemie Windows 7 i nowszym (nie telefon) oraz wersjach systemu Windows Server, począwszy od systemu Windows Server 2008 z dodatkiem Service Pack 2. Aby uzyskać pełną listę wymagań, zobacz [Wymagania](../debugger/remote-debugging.md#requirements_msvsmon).

> [!NOTE]
> Debugowanie między dwoma komputerami podłączonymi za pośrednictwem serwera proxy nie jest obsługiwane. Debugowanie za pośrednictwem połączenia o dużej masie lub niskiej przepustowości, takiego jak dialup Internet lub przez Internet w różnych krajach, nie jest zalecane i może zakończyć się niepowodzeniem lub być niedopuszczalnie powolne.

## <a name="download-and-install-the-remote-tools"></a>Pobieranie i instalowanie narzędzi zdalnych

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

> [!TIP]
> W niektórych scenariuszach może być najbardziej efektywne uruchomienie zdalnego debugera z udziału plików. Aby uzyskać więcej informacji, zobacz [Uruchamianie zdalnego debugera z udziału plików](../debugger/remote-debugging.md#fileshare_msvsmon).

## <a name="set-up-the-remote-debugger"></a><a name="BKMK_setup"></a>Konfigurowanie zdalnego debugera

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Jeśli chcesz dodać uprawnienia dla dodatkowych użytkowników, zmień tryb uwierzytelniania lub numer portu dla zdalnego debugera, zobacz [Konfigurowanie debugera zdalnego](../debugger/remote-debugging.md#configure_msvsmon).

## <a name="remote-debug-a-c-project"></a><a name="remote_cplusplus"></a>Zdalne debugowanie projektu języka C++
 W poniższej procedurze nazwa i ścieżka projektu to C:\remotetemp\MyMfc, a nazwa komputera zdalnego to **MJO-DL**.

1. Utwórz aplikację MFC o nazwie **mymfc.**

2. Ustaw punkt przerwania gdzieś w aplikacji, który jest łatwo dostępny, na przykład `CMainFrame::OnCreate`w **MainFrm.cpp**, na początku .

3. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Właściwości**. Otwórz kartę **Debugowanie.**

4. Ustaw **debuger, aby uruchomić** do **zdalnego debugera systemu Windows**.

    ![RemoteDebuggingCPlus](../debugger/media/remotedebuggingcplus.png "RemoteDebuggingCPlus")

5. Wprowadzać następujące zmiany we właściwościach:

   |Ustawienie|Wartość|
   |-|-|
   |Polecenie zdalne|C:\remotetemp\mymfc.exe|
   |Katalog roboczy|C:\remotetemp|
   |Nazwa serwera zdalnego|MJO-DL:*numer portnumber*|
   |Połączenie|Zdalny z uwierzytelnianiem systemu Windows|
   |Typ debugera|Tylko natywny|
   |Katalog wdrożeniów|C:\remotetemp.|
   |Dodatkowe pliki do wdrożenia|C:\data\mymfcdata.txt.|

    Jeśli wdrożysz dodatkowe pliki (opcjonalnie), folder musi istnieć na obu komputerach.

6. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy rozwiązanie i wybierz polecenie **Menedżer konfiguracji**.

7. W przypadku konfiguracji **debugowania** zaznacz pole wyboru **Wdrażanie.**

    ![RemoteDebugCplusDeploy](../debugger/media/remotedebugcplusdeploy.png "RemoteDebugCplusDeploy")

8. Rozpocznij debugowanie **(Debugowanie > Rozpocznij debugowanie**lub **F5**).

9. Plik wykonywalny jest automatycznie wdrażany na komputerze zdalnym.

10. Jeśli zostanie wyświetlony monit, wprowadź poświadczenia sieci, aby połączyć się z komputerem zdalnym.

     Wymagane poświadczenia są specyficzne dla konfiguracji zabezpieczeń sieci. Na przykład na komputerze domeny można wybrać certyfikat zabezpieczeń lub wprowadzić nazwę domeny i hasło. Na komputerze spoza domeny można wprowadzić nazwę komputera i prawidłową <strong>MJO-DL\name@something.com</strong>nazwę konta użytkownika, na przykład , wraz z poprawnym hasłem.

11. Na komputerze z programem Visual Studio powinien zostać wyświetlony, że wykonanie jest zatrzymane w punkcie przerwania.

    > [!TIP]
    > Alternatywnie można wdrożyć pliki jako osobny krok. W **Eksploratorze rozwiązań** kliknij prawym przyciskiem myszy węzeł **mymfc,** a następnie wybierz polecenie **Wdrażanie**.

    Jeśli masz pliki inne niż kod, które są wymagane przez aplikację, można określić je w **plikach dodatkowych do wdrożenia** na stronie **zdalnego debugera systemu Windows.**

    Alternatywnie można dołączyć pliki w projekcie i ustawić **Content** właściwości **tak** na **właściwości** strony dla każdego pliku. Pliki te są kopiowane do **katalogu wdrażania** określonego na stronie **Zdalny debuger systemu Windows.** Można również zmienić **typ elementu** na **Kopiuj plik** i określić tam dodatkowe właściwości, jeśli potrzebne są pliki do skopiowania do podfolderu katalogu **wdrażania**.

## <a name="set-up-debugging-with-remote-symbols"></a>Konfigurowanie debugowania za pomocą symboli zdalnych

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]

## <a name="see-also"></a>Zobacz też
- [Debugowanie w programie Visual Studio](../debugger/index.yml)
- [Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md)
- [Konfigurowanie Zapory systemu Windows do zdalnego debugowania](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Remote Debugger Port Assignments (Przypisania portów zdalnego debugera)](../debugger/remote-debugger-port-assignments.md)
- [Zdalne debugowanie platformy ASP.NET na komputerze zdalnym usług IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)
- [Błędy związane z debugowaniem zdalnym i rozwiązywanie problemów](../debugger/remote-debugging-errors-and-troubleshooting.md)