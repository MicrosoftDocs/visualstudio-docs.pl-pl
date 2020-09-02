---
title: Wdrażanie aplikacji platformy UWP | Microsoft Docs
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
ms.openlocfilehash: 4c58dbb32ef0a476ac7e22a840e27e389c710f97
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "73188280"
---
# <a name="deploy-uwp-apps-from-visual-studio"></a>Wdrażanie aplikacji platformy UWP przy użyciu programu Visual Studio

Funkcja wdrażania programu Visual Studio kompiluje i rejestruje aplikacje platformy UWP utworzone za pomocą programu Visual Studio na urządzeniu docelowym. Dokładnie sposób rejestracji aplikacji zależy od tego, czy urządzenie docelowe jest lokalne, czy zdalne:

- Gdy obiektem docelowym jest lokalna maszyna programu Visual Studio, program Visual Studio rejestruje aplikację z folderu Build.

- Gdy obiektem docelowym jest urządzenie zdalne, program Visual Studio kopiuje wymagane pliki na maszynę zdalną i rejestruje aplikację na tym urządzeniu.

Wdrożenie jest automatyczne podczas debugowania aplikacji z programu Visual Studio przy użyciu opcji **Rozpocznij debugowanie** (klawiatura: F5) lub opcji **Rozpocznij bez debugowania** (klawiatura: CTRL + F5). Aplikację można również wdrożyć ręcznie. Ręczne wdrażanie jest przydatne w następujących scenariuszach:

- Testowanie ad hoc na komputerze lokalnym lub zdalnym.

- Wdrażanie aplikacji, która będzie uruchamiać inną aplikację, którą chcesz debugować.

- Wdrażanie aplikacji, która będzie debugowana, gdy zostanie uruchomiona przez inną aplikację lub metodę.

## <a name="how-to-deploy-a-uwp-app"></a><a name="BKMK_How_to_deploy_a_Windows_Store_app"></a> Jak wdrożyć aplikację platformy UWP
 Ręczne wdrażanie aplikacji to prosty proces:

1. W przypadku wdrażania na urządzeniu zdalnym należy określić nazwę lub adres IP urządzenia na stronie projekt właściwości projektu startowego aplikacji. (Kroki, które należy wykonać, przedstawiono w dalszej części tego tematu).

2. Na pasku narzędzi debugera programu Visual Studio wybierz element docelowy wdrożenia z listy rozwijanej obok przycisku **Rozpocznij debugowanie** .

     ![Uruchom na komputerze lokalnym](../debugger/media/vsrun_f5_local.png "VSRUN_F5_Local")

3. W menu **kompilacja** wybierz polecenie **Wdróż** .

## <a name="how-to-specify-a-remote-device"></a><a name="BKMK_How_to_specify_a_remote_device"></a> Jak określić urządzenie zdalne

**Wymagania wstępne**

Na urządzeniu zdalnym z systemem Windows 10 należy włączyć [Tryb dewelopera](/windows/uwp/get-started/enable-your-device-for-development). Na urządzeniach z systemem Windows 10 z uruchomioną aktualizacją lub nowszą wersją kreatora narzędzia zdalne są instalowane automatycznie podczas wdrażania aplikacji. Aby uzyskać więcej informacji, zobacz [debugowanie zainstalowanego pakietu aplikacji](../debugger/debug-installed-app-package.md).

> [!NOTE]
> W wersjach systemu Windows 10 z aktualizacją przed twórcą należy zainstalować Remote Tools for Visual Studio na urządzeniu zdalnym, a zdalny debuger musi być uruchomiony.

Wdrożenie używa kanału sieciowego debugera zdalnego do wysyłania plików aplikacji do zdalnego urządzenia.

#### <a name="to-specify-a-remote-device"></a>Aby określić urządzenie zdalne

1. Na stronie właściwości debugowania projektu startowego Określ nazwę lub adres IP miejsca docelowego wdrożenia zdalnego.

2. Aby otworzyć stronę właściwości debugowania, wybierz projekt w Eksplorator rozwiązań a następnie wybierz **Właściwości** z menu skrótów.

3. Następnie wybierz węzeł **debugowanie** w oknie strony właściwości.

4. W przypadku **urządzenia docelowego**wybierz pozycję **maszyna zdalna**.

5. W obszarze **maszyna zdalna**kliknij przycisk **Znajdź**.

6. Można wpisać nazwę lub adres IP urządzenia zdalnego lub wybrać urządzenie z okna dialogowego **połączenie zdalne** .

    ![Okno dialogowe Wybieranie połączenia zdalnego debugera](../debugger/media/vsrun_selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")

    W oknie dialogowym **połączenie zdalne** są wyświetlane urządzenia w podsieci sieci lokalnej i każde urządzenie połączone bezpośrednio z maszyną programu Visual Studio za pomocą kabla Ethernet.

   **Określanie urządzenia zdalnego na stronie projektu języka C++**

   ![C&#43;&#43; właściwości projektu dla zdalnego debugowania](../debugger/media/vsrun_cpp_projprop_remote.png "VSRUN_CPP_ProjProp_Remote")

7. Wybierz **zdalny debuger** z listy **debuger do uruchomienia** .

8. Wprowadź nazwę sieciową urządzenia zdalnego w polu **Nazwa komputera** . Możesz też wybrać strzałkę w dół w polu, aby wybrać urządzenie w oknie dialogowym Wybierz połączenie ze zdalnym debugerem.

   **Określanie urządzenia zdalnego w Visual C# i Visual Basic stronie projektu**

   ![Zarządzane właściwości projektu dla zdalnego debugowania](../debugger/media/vsrun_managed_projprop_remote.png "VSRUN_Managed_ProjProp_Remote")

9. Wybierz pozycję **maszyna zdalna** z listy **urządzeń docelowych** .

10. Wprowadź nazwę sieciową urządzenia zdalnego w polu **maszyna zdalna** lub kliknij przycisk **Znajdź** , aby wybrać urządzenie w oknie dialogowym **Wybierz połączenie ze zdalnym debugerem** .

## <a name="deployment-options"></a><a name="BKMK_Deployment_options"></a> Opcje wdrażania

Można ustawić następujące opcje wdrażania na stronie właściwości debugowania projektu startowego.

**Zezwalaj na sprzężenie zwrotne sieci**

Ze względów bezpieczeństwa platformy UWP lub [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] aplikacja, która jest zainstalowana w standardowym sposobie, nie może wykonywać wywołań sieciowych na urządzeniu, na którym jest ono zainstalowane. Domyślnie wdrożenie programu Visual Studio tworzy wykluczenie z tej reguły dla wdrożonej aplikacji. To wykluczenie umożliwia testowanie procedur komunikacji na pojedynczym komputerze. Przed przesłaniem aplikacji do programu należy [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)] przetestować aplikację bez wykluczania.

Aby usunąć wykluczenie sprzężenia zwrotnego sieci z aplikacji:

- Na stronie właściwości debugowania C# i Visual Basic wyczyść pole wyboru **Zezwalaj na sprzężenie zwrotne sieci** .

- Na stronie właściwości debugowania C++ ustaw wartość ustawienia **Zezwalaj na sprzężenie zwrotne sieci** na **nie**.

**Nie uruchamiaj, ale Debuguj mój kod podczas uruchamiania (C# i Visual Basic)/Uruchom aplikację (C++)**

Aby skonfigurować wdrożenie w celu automatycznego uruchamiania sesji debugowania podczas uruchamiania aplikacji:

- Na stronie właściwości debugowania C# i Visual Basic zaznacz pole wyboru nie **uruchamiaj, ale Debuguj mój kod podczas uruchamiania** .

- Na stronie właściwości debugowania C++ ustaw wartość opcji **Uruchom aplikację** na **tak**.

## <a name="see-also"></a>Zobacz też

- [Zaawansowane opcje zdalnego wdrażania](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options)
- [Debugowanie zainstalowanego pakietu aplikacji](../debugger/debug-installed-app-package.md)
- [Uruchamianie aplikacji w programie Visual Studio](debugging-windows-store-and-windows-universal-apps.md)
