---
title: Zdalne debugowanie projektu Visual C++ | Dokumentacja firmy Microsoft
ms.custom: remotedebugging
ms.date: 08/14/2017
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
ms.openlocfilehash: 88deb9957766b4e4e0802a1eded352a6ccb04f98
ms.sourcegitcommit: a916ce1eec19d49f060146f7dd5b65f3925158dd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2019
ms.locfileid: "55231574"
---
# <a name="remote-debugging-a-visual-c-project-in-visual-studio"></a>Zdalne debugowanie projektu Visual C++ w programie Visual Studio
Debugowanie aplikacji Visual Studio na innym komputerze, zainstalować i uruchomić narzędzia zdalne na komputerze, w którym wdrożysz swoją aplikację, należy skonfigurować projekt, aby połączyć się z komputerem zdalnym z programu Visual Studio, a następnie wdrożyć i uruchomić aplikację.

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

## <a name="remote_cplusplus"></a> Debugowanie zdalne projektu Visual C++  
 W poniższej procedurze nazwa i ścieżka projektu jest C:\remotetemp\MyMfc, a nazwa komputera zdalnego jest **MJO DL**.  
  
1. Tworzenie aplikacji MFC o nazwie **mymfc.**  
  
2. Ustaw punkt przerwania gdzieś w aplikacji, które łatwo zostanie osiągnięty, na przykład w **MainFrm.cpp**, na początku `CMainFrame::OnCreate`.  
  
3. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz pozycję **właściwości**. Otwórz **debugowanie** kartę.  
  
4. Ustaw **debuger do uruchomienia** do **zdalny debuger Windows**.  
  
    ![RemoteDebuggingCPlus](../debugger/media/remotedebuggingcplus.png "RemoteDebuggingCPlus")  
  
5. Do właściwości, należy wprowadzić następujące zmiany:  
  
   |Ustawienie|Wartość|
   |-|-|  
   |Polecenie zdalne|C:\remotetemp\mymfc.exe|  
   |Katalog roboczy|C:\remotetemp|  
   |Nazwa serwera zdalnego|Listy Dystrybucyjnej MJO:*numer_portu*|  
   |Połączenie|Zdalny z uwierzytelnianiem Windows|  
   |Typ debugera|Tylko w trybie macierzystym|  
   |Katalog wdrażania|C:\remotetemp.|  
   |Dodatkowe pliki do wdrożenia|C:\data\mymfcdata.txt.|  
  
    Jeśli wdrożono dodatkowe pliki (opcjonalnie), folder musi istnieć na obu komputerach.  
  
6. W Eksploratorze rozwiązań kliknij rozwiązanie prawym przyciskiem myszy i wybierz polecenie **programu Configuration Manager**.  
  
7. Aby uzyskać **debugowania** konfigurację, kliknij przycisk **Wdróż** pole wyboru.  
  
    ![RemoteDebugCplusDeploy](../debugger/media/remotedebugcplusdeploy.png "RemoteDebugCplusDeploy")  
  
8. Rozpocznij debugowanie (**Debuguj > Rozpocznij debugowanie**, lub **F5**).  
  
9. Plik wykonywalny jest automatycznie wdrażane na komputerze zdalnym.  
  
10. Po wyświetleniu monitu wprowadź poświadczenia sieci, aby nawiązać połączenie z komputerem zdalnym.  
  
     Wymagane poświadczenia są specyficzne dla konfiguracji zabezpieczeń w sieci. Na przykład na komputerze domeny, możesz wybrać certyfikat zabezpieczeń, lub wprowadź nazwę domeny i hasło. Na komputerze nienależących do domeny, wprowadzić nazwę komputera i prawidłową nazwę konta użytkownika, takie jak <strong>MJO-DL\name@something.com</strong>, oraz prawidłowe hasło.  
  
11. Na komputerze programu Visual Studio powinien zostać wyświetlony, że wykonanie zostanie zatrzymana w punkcie przerwania.  
  
    > [!TIP]
    > Alternatywnie można rozłożyć pliki w osobnym kroku. W **Eksploratora rozwiązań** kliknij prawym przyciskiem myszy **mymfc** węzeł, a następnie wybierz **Wdróż**.
  
    Jeśli masz pliki niezawierające kodu, które są wymagane przez aplikację, można określić je w **dodatkowe pliki do wdrażania** na **zdalny debuger Windows** strony.

    Alternatywnie można dołączyć pliki w projekcie i ustaw **zawartości** właściwości **tak** w **właściwości** strony dla każdego pliku. Te pliki są kopiowane do **katalogu wdrażania** określono na **zdalny debuger Windows** strony. Możesz również zmienić **typu elementu** do **kopiowania pliku** i określić dodatkowe właściwości istnieje, jeśli potrzebne pliki będą kopiowane do podfolderu **katalogu wdrażania**.
  
## <a name="set-up-debugging-with-remote-symbols"></a>Konfigurowanie debugowania przy użyciu zdalnego symboli 

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)] 
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie w programie Visual Studio](../debugger/index.md)  
 [Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md)   
 [Skonfiguruj zaporę Windows do zdalnego debugowania](../debugger/configure-the-windows-firewall-for-remote-debugging.md)   
 [Przypisania portów debugera zdalnego](../debugger/remote-debugger-port-assignments.md)   
 [Zdalne debugowanie platformy ASP.NET na komputerze zdalnym usług IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)  
 [Błędy związane z debugowaniem zdalnym i rozwiązywanie problemów](../debugger/remote-debugging-errors-and-troubleshooting.md)