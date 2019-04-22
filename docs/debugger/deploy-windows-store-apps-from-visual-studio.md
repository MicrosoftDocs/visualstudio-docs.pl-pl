---
title: Wdrażanie aplikacji platformy uniwersalnej systemu Windows | Dokumentacja firmy Microsoft
ms.custom: seodec18
ms.date: 01/16/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 63726f9f38cdede6c8a0525b74244baac9455aad
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58790384"
---
# <a name="deploy-uwp-apps-from-visual-studio"></a>Wdrażanie aplikacji platformy UWP przy użyciu programu Visual Studio

Funkcjonalność wdrożenia programu Visual Studio tworzy i rejestruje aplikacje platformy uniwersalnej systemu Windows, które są tworzone za pomocą programu Visual Studio na urządzeniu docelowym. Dokładnie, jak aplikacja jest zarejestrowana, zależy od tego, czy urządzenie docelowe jest lokalnym lub zdalnym:

- Gdy element docelowy jest komputera lokalnego programu Visual Studio, Visual Studio rejestruje aplikacji z poziomu folderu jego kompilacji.

- Gdy element docelowy jest urządzenie zdalne, Visual Studio kopiuje pliki wymagane do maszyny zdalnej i rejestruje aplikację na tym urządzeniu.

Wdrożenia jest automatycznie podczas debugowania aplikacji w programie Visual Studio przy użyciu **Rozpocznij debugowanie** opcji (klawiatury: F5) lub **Rozpocznij bez debugowania** opcji (klawiatury: CTRL + F5). Można także wdrożyć aplikację ręcznie. Ręczne wdrażanie jest przydatne w następujących scenariuszach:

- Ad hoc testów na komputerze lokalnym lub zdalnym.

- Wdrażanie aplikacji, która zostanie uruchomiona w innej aplikacji, który chcesz debugować.

- Wdrażanie aplikacji, która będzie debugowany, gdy jest ona uruchamiana przez inną aplikację lub metody.

##  <a name="BKMK_How_to_deploy_a_Windows_Store_app"></a> Jak wdrożyć aplikację platformy uniwersalnej systemu Windows
 Ręczne wdrażanie aplikacji jest prostym procesem:

1.  Jeśli są wdrażane na urządzeniu zdalnym, należy określić nazwę lub adres IP urządzenia na stronie właściwości projektu z projektu do uruchamiania aplikacji. (Kroki, aby zrobić to są wymienione dalszych szczegółów, w tym temacie).

2.  Na pasku narzędzi programu Visual Studio debugger wybierz cel wdrożenia z listy rozwijanej obok **Rozpocznij debugowanie** przycisku.

     ![Uruchom na lokalnym komputerze](../debugger/media/vsrun_f5_local.png "VSRUN_F5_Local")

3.  Na **kompilacji** menu, wybierz **wdrażania**

##  <a name="BKMK_How_to_specify_a_remote_device"></a> Jak określić urządzenie zdalne

**Wymagania wstępne**

Na urządzeniu zdalnym systemem Windows 10, należy włączyć [tryb dewelopera](/windows/uwp/get-started/enable-your-device-for-development). Na urządzeniach Windows 10 z aktualizacją Update twórcy lub później, zdalne narzędzia są instalowane automatycznie podczas wdrażania aplikacji. Aby uzyskać więcej informacji, zobacz [debugowanie zainstalowanego pakietu aplikacji](../debugger/debug-installed-app-package.md).

> [!NOTE]
> Na wstępnie twórcy wersje aktualizacji systemu Windows 10 Remote Tools for Visual Studio musi być zainstalowany na urządzeniu zdalnym i zdalny debuger musi być uruchomiona.

Wdrożenie używa zdalny debuger kanał sieciowy do wysyłania plików aplikacji na urządzeniu zdalnym.

#### <a name="to-specify-a-remote-device"></a>Aby określić urządzenie zdalne

1. Na stronie właściwości debugowania projektu startowego Określ nazwę lub adres IP elementu docelowego wdrażania zdalnego.

2. Aby otworzyć stronę właściwości debugowania, wybierz projekt w Eksploratorze rozwiązań, a następnie wybierz **właściwości** z menu skrótów.

3. Następnie wybierz **debugowania** węzła w oknie właściwości strony.

4. Aby uzyskać **urządzenie docelowe**, wybierz opcję **maszyny zdalnej**.

5. W obszarze **maszyny zdalnej**, kliknij przycisk **znaleźć**.

6. Możesz wpisać nazwę lub adres IP urządzenia zdalnego lub można wybrać urządzenie w **połączenia zdalnego** okno dialogowe.

    ![Okno dialogowe Wybierz połączenie ze zdalnym debugerem](../debugger/media/vsrun_selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")

    **Połączenia zdalnego** okno dialogowe wyświetla urządzenia w podsieci sieci lokalnej i dowolnego urządzenia podłączonego bezpośrednio do maszyny programu Visual Studio za pomocą kabla Ethernet.

   **Określanie urządzenie zdalne, na stronie projektu Visual C++**

   ![C&#43; &#43; właściwości dla zdalnego debugowania projektu](../debugger/media/vsrun_cpp_projprop_remote.png "VSRUN_CPP_ProjProp_Remote")

7. Wybierz **zdalny debuger** z **debuger do uruchomienia** listy.

8. Wprowadź nazwę sieciową urządzenia zdalnego w **NazwaKomputera** pole. Alternatywnie można wybrać strzałkę w dół w polu, aby wybrać urządzenie w oknie dialogowym Wybierz połączenie ze zdalnym debugerem.

   **Określanie urządzenie zdalne na stronie projektu Visual C# i Visual Basic**

   ![Właściwości projektu dla zdalnego debugowania zarządzane](../debugger/media/vsrun_managed_projprop_remote.png "VSRUN_Managed_ProjProp_Remote")

9. Wybierz **maszyny zdalnej** z **urządzenie docelowe** listy.

10. Wprowadź nazwę sieciową urządzenia zdalnego w **maszyny zdalnej** lub przycisk **znaleźć** do wyboru urządzenia z **wybierz połączenie ze zdalnym debugerem** okno dialogowe.

##  <a name="BKMK_Deployment_options"></a> Opcje wdrażania

Można ustawić następujące opcje wdrażania na stronie właściwości debugowania projektu startowego.

**Zezwalaj na sprzężenie zwrotne sieci**

Ze względów bezpieczeństwa, platformy uniwersalnej systemu Windows lub [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] aplikację, która jest zainstalowana w standardowy sposób wykonywania wywołań sieci na urządzeniu jest zainstalowany na jest niedozwolone. Domyślnie wdrożenie programu Visual Studio tworzy wyjątek od tej reguły dla wdrożonej aplikacji. To wykluczenie umożliwia przetestowanie procedur komunikacji na jednym komputerze. Przed przesłaniem aplikacji do [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)], należy przetestować aplikację bez zwolnienia.

Aby usunąć wykluczenie sprzężenie zwrotne sieci z poziomu aplikacji:

- Na C# i debugowania języka Visual Basic strony właściwości, wyczyść **Zezwalaj na sprzężenie zwrotne sieci** pole wyboru.

- Na stronie właściwości debugowania języka C++, należy ustawić **Zezwalaj na sprzężenie zwrotne sieci** wartość **nie**.

**Nie uruchamiaj, ale Debuguj kod przy rozpoczęciu (C# i Visual Basic) / uruchamianie aplikacji (C++)**

Aby skonfigurować wdrożenie, aby automatycznie uruchomić sesję debugowania, gdy aplikacja jest uruchamiana:

- Na C# i debugowania języka Visual Basic strony właściwości, sprawdź **nie uruchamiaj, ale Debuguj kod przy rozpoczęciu** pole wyboru.

- Na stronie właściwości debugowania języka C++, należy ustawić **Uruchom aplikację** wartość **tak**.

## <a name="see-also"></a>Zobacz też

- [Zaawansowane opcje zdalnego wdrażania](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options)
- [Debugowanie zainstalowanego pakietu aplikacji](../debugger/debug-installed-app-package.md)
- [Uruchamianie aplikacji w programie Visual Studio](/visualstudio/debugger/debugging-windows-store-and-windows-universal-apps)
