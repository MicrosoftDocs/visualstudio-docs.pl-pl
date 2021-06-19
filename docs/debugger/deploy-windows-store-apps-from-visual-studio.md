---
title: Wdrażanie aplikacji platformy UWP | Microsoft Docs
description: Wdrażanie platforma uniwersalna systemu Windows (UWP) z Visual Studio. Określ lokalne lub zdalne urządzenie docelowe do wdrożenia. Opis opcji wdrażania.
ms.custom: SEO-VS-2020
ms.date: 01/16/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- uwp
ms.openlocfilehash: 0a1c1802d92beb436bbd2ac87bd1e7a39f6086f1
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387869"
---
# <a name="deploy-uwp-apps-from-visual-studio"></a>Wdrażanie aplikacji platformy UWP przy użyciu programu Visual Studio

Funkcja Visual Studio tworzy i rejestruje aplikacje platformy UWP, które są tworzone za Visual Studio na urządzeniu docelowym. Dokładnie sposób rejestrowania aplikacji zależy od tego, czy urządzenie docelowe jest lokalne, czy zdalne:

- Gdy obiektem docelowym jest maszyna Visual Studio lokalna, Visual Studio aplikację z folderu kompilacji.

- Jeśli element docelowy jest urządzeniem zdalnym, program Visual Studio wymagane pliki na maszynę zdalną i rejestruje aplikację na tym urządzeniu.

Wdrażanie jest automatyczne podczas debugowania aplikacji z programu  Visual Studio przy użyciu opcji Rozpocznij  debugowanie (Klawiatura: F5) lub Uruchom bez debugowania (Klawiatura: CTRL + F5). Możesz również wdrożyć aplikację ręcznie. Wdrożenie ręczne jest przydatne w następujących scenariuszach:

- Testowanie ad hoc na komputerze lokalnym lub zdalnym.

- Wdrażanie aplikacji, która będzie uruchamiać inną aplikację do debugowania.

- Wdrażanie aplikacji, która będzie debugowana po jej wdrożeniu przez inną aplikację lub metodę.

## <a name="how-to-deploy-a-uwp-app"></a><a name="BKMK_How_to_deploy_a_Windows_Store_app"></a> Jak wdrożyć aplikację platformy UWP
 Ręczne wdrażanie aplikacji jest prostym procesem:

1. W przypadku wdrażania na urządzeniu zdalnym określ nazwę lub adres IP urządzenia na stronie projektu właściwości projektu uruchamiania aplikacji. (Kroki, które należy wykonać, zostały opisane w dalszej kolejności w tym temacie).

2. Na pasku narzędzi Visual Studio wybierz element docelowy wdrożenia z listy rozwijanej obok **przycisku Rozpocznij debugowanie.**

     ![Uruchamianie na maszynie lokalnej](../debugger/media/vsrun_f5_local.png "VSRUN_F5_Local")

3. W menu **Kompilacja** wybierz pozycję **Wd wdrażaj**

## <a name="how-to-specify-a-remote-device"></a><a name="BKMK_How_to_specify_a_remote_device"></a> Jak określić urządzenie zdalne

**Wymagania wstępne**

Na urządzeniu Windows 10 należy włączyć tryb [dewelopera](/windows/uwp/get-started/enable-your-device-for-development). Na Windows 10 z aktualizacją twórcy lub nowszym narzędzia zdalne są automatycznie instalowane podczas wdrażania aplikacji. Aby uzyskać więcej informacji, zobacz [Debugowanie zainstalowanego pakietu aplikacji.](../debugger/debug-installed-app-package.md)

> [!NOTE]
> W wersjach aktualizacji systemu Windows 10 przez twórcę na urządzeniu zdalnym musi Remote Tools for Visual Studio, a zdalny debuger musi być uruchomiony.

Wdrożenie używa kanału sieciowego zdalnego debugera do wysyłania plików aplikacji do urządzenia zdalnego.

#### <a name="to-specify-a-remote-device"></a>Aby określić urządzenie zdalne

1. Na stronie Właściwości debugowania projektu startowego określ nazwę lub adres IP zdalnego celu wdrożenia.

2. Aby otworzyć stronę Właściwości debugowania, wybierz projekt w Eksplorator rozwiązań a następnie wybierz pozycję **Właściwości** z menu skrótów.

3. Następnie wybierz węzeł **Debugowanie** w oknie strony właściwości.

4. W **przypadku urządzenia docelowego** wybierz **pozycję Maszyna zdalna.**

5. W **obszarze Maszyna zdalna** kliknij pozycję **Znajdź**.

6. Możesz wpisać nazwę lub adres IP urządzenia zdalnego lub wybrać urządzenie  w oknie dialogowym Połączenie zdalne.

    ![Okno dialogowe Wybieranie połączenia zdalnego debugera](../debugger/media/vsrun_selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")

    W **oknie dialogowym** Podłączanie zdalne są wyświetlane urządzenia w podsieci sieci lokalnej i dowolne urządzenie podłączone bezpośrednio do maszyny Visual Studio za pomocą kabla Ethernet.

   **Określanie urządzenia zdalnego na stronie projektu języka C++**

   ![C&#43;&#43; projektu na potrzeby debugowania zdalnego](../debugger/media/vsrun_cpp_projprop_remote.png "VSRUN_CPP_ProjProp_Remote")

7. Wybierz **pozycję Debuger zdalny** z **debugera, aby uruchomić** listę.

8. Wprowadź nazwę sieciową urządzenia zdalnego w **polu Nazwa** komputera. Możesz też wybrać strzałkę w dół w polu, aby wybrać urządzenie w oknie dialogowym Wybieranie połączenia zdalnego debugera.

   **Określanie urządzenia zdalnego w języku Visual C# i Visual Basic stronie projektu**

   ![Właściwości zarządzanego projektu na potrzeby debugowania zdalnego](../debugger/media/vsrun_managed_projprop_remote.png "VSRUN_Managed_ProjProp_Remote")

9. Wybierz **pozycję Maszyna zdalna** z **listy Urządzenie** docelowe.

10. Wprowadź nazwę sieciową urządzenia zdalnego  w polu  Maszyna zdalna lub kliknij przycisk Znajdź, aby wybrać urządzenie w oknie dialogowym Wybieranie połączenia **zdalnego debugera.**

## <a name="deployment-options"></a><a name="BKMK_Deployment_options"></a> Opcje wdrażania

Następujące opcje wdrażania można ustawić na stronie właściwości Debugowanie projektu startowego.

**Zezwalaj na sprzężenia zwrotne sieci**

Ze względów bezpieczeństwa system UWP lub aplikacja zainstalowana w standardowy sposób nie może wykonać wywołań sieciowych do urządzenia, [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] na których jest zainstalowana. Domyślnie wdrożenie Visual Studio tworzy wyjątek od tej reguły dla wdrożonej aplikacji. To wyłączenie umożliwia testowanie procedur komunikacji na jednym komputerze. Przed przesłaniem aplikacji do usługi należy ją [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)] przetestować bez zwolnienia.

Aby usunąć wyjątek sprzężenia zwrotnego sieci z aplikacji:

- Na stronie właściwości Debugowanie Visual Basic C# wyczyść pole wyboru Zezwalaj na **sprzężenia zwrotne sieci.**

- Na stronie właściwości Debugowanie języka C++ ustaw wartość Zezwalaj na **sprzężenia zwrotne sieci** na **wartość Nie.**

**Nie uruchamiaj, ale debuguj mój kod po uruchomieniu (C# i Visual Basic) / Launch Application (C++)**

Aby skonfigurować wdrożenie do automatycznego uruchamiania sesji debugowania po uruchomieniu aplikacji:

- Na stronie właściwości Debugowanie Visual Basic C# zaznacz pole wyboru Nie uruchamiaj, ale debuguj mój kod po **uruchomieniu.**

- Na stronie właściwości Debugowanie języka C++ ustaw wartość Tak dla ustawienia **Uruchom** **aplikację.**

## <a name="see-also"></a>Zobacz też

- [Zaawansowane opcje wdrażania zdalnego](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options)
- [Debugowanie zainstalowanego pakietu aplikacji](../debugger/debug-installed-app-package.md)
- [Uruchamianie aplikacji w programie Visual Studio](debugging-windows-store-and-windows-universal-apps.md)
