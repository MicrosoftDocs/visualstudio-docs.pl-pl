---
title: Debuguj aplikacje platformy UWP na komputerach zdalnych | Microsoft Docs
description: Zapoznaj się z tematem jak używać programu Visual Studio do uruchamiania, debugowania, profilowania i testowania aplikacji platforma uniwersalna systemu Windows (platformy UWP) zdalnie na innym komputerze lub urządzeniu.
ms.custom: SEO-VS-2020
ms.date: 10/05/2018
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 0f6814d6-cd0d-49f3-b501-dea8c094b8ef
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: a28769237f0c1b0078e9c9c117695e68e5b521ac
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2021
ms.locfileid: "98204959"
---
# <a name="debug-uwp-apps-on-remote-machines-from-visual-studio"></a>Debuguj aplikacje platformy UWP na maszynach zdalnych z programu Visual Studio

Program Visual Studio umożliwia uruchamianie, debugowanie, profilowanie i testowanie aplikacji platforma uniwersalna systemu Windows (platformy UWP) na innym komputerze lub urządzeniu. Uruchamianie aplikacji platformy UWP na maszynie zdalnej jest szczególnie przydatne, gdy komputer z programem Visual Studio nie obsługuje funkcji specyficznych dla platformy UWP, takich jak Touch, lokalizacja geograficzna czy orientacja fizyczna.

## <a name="prerequisites"></a><a name="BKMK_Prerequisites"></a> Wymagany

Aby debugować aplikację platformy UWP na urządzeniu zdalnym z programu Visual Studio:

- Projekt programu Visual Studio musi być skonfigurowany pod kątem zdalnego debugowania.
- Maszyna zdalna i komputer z programu Visual Studio muszą być połączone przez sieć lub podłączone bezpośrednio za pośrednictwem kabla USB lub Ethernet. Debugowanie przez Internet nie jest obsługiwane.
- [Tryb dewelopera należy włączyć](/windows/uwp/get-started/enable-your-device-for-development) zarówno na komputerze z programem Visual Studio, jak i na komputerze zdalnym.
- Komputery zdalne muszą mieć uruchomioną Remote Tools for Visual Studio.
  - Niektóre wersje systemu Windows 10 uruchamiają i automatycznie uruchamiają narzędzia zdalne. W przeciwnym razie [Zainstaluj i uruchom Remote Tools for Visual Studio](#BKMK_download).
  - Urządzenia z systemem Windows Mobile 10 nie wymagają ani nie obsługują narzędzi zdalnych.

## <a name="configure-a-visual-studio-project-for-remote-debugging"></a><a name="BKMK_ConnectVS"></a> Konfigurowanie projektu programu Visual Studio na potrzeby zdalnego debugowania
<a name="BKMK_DirectConnect"></a> Za pomocą **Właściwości** projektu można określić urządzenie zdalne, z którym ma zostać nawiązane połączenie. Ustawienia różnią się w zależności od języka programowania.

> [!CAUTION]
> Domyślnie strona właściwości ustawia **uniwersalną (niezaszyfrowany protokół)** jako **Typ uwierzytelniania** dla połączeń zdalnych systemu Windows 10. Może być konieczne ustawienie opcji **Brak uwierzytelniania** w celu nawiązania połączenia ze zdalnym debugerem. **Uniwersalne (niezaszyfrowany protokół)** i **bez protokołów uwierzytelniania** nie ma zabezpieczeń sieci, dlatego dane przesyłane między maszynami deweloperskimi i zdalnymi są zagrożone. Te typy uwierzytelniania należy wybrać tylko w przypadku zaufanych sieci, na których masz pewność, że nie są narażone przed złośliwym lub zagrożonym ruchem.
>
>W przypadku wybrania opcji **uwierzytelnianie systemu Windows** dla **typu uwierzytelniania** należy zalogować się do maszyny zdalnej podczas debugowania. Zdalny debuger musi być również uruchomiony w trybie **uwierzytelniania systemu Windows** , przy użyciu tego samego konta użytkownika jak na komputerze z programem Visual Studio.

### <a name="configure-a-c-or-visual-basic-project-for-remote-debugging"></a><a name="BKMK_Choosing_the_remote_device_for_C__and_Visual_Basic_projects"></a> Konfigurowanie projektu C# lub Visual Basic na potrzeby debugowania zdalnego

1. Wybierz projekt C# lub Visual Basic w programie Visual Studio **Eksplorator rozwiązań** i wybierz ikonę **Właściwości** , naciśnij klawisz **Alt** + **Enter** lub kliknij prawym przyciskiem myszy i wybierz polecenie **Właściwości**.

1. Wybierz kartę **debugowanie** .

1. W obszarze **urządzenie docelowe** wybierz pozycję **maszyna zdalna** dla komputera zdalnego lub **urządzenie** dla bezpośrednio podłączonego urządzenia z systemem Windows Mobile 10.

1. W przypadku maszyny zdalnej wprowadź nazwę sieci lub adres IP w polu **maszyna zdalna** lub wybierz pozycję **Znajdź** , aby wyszukać urządzenie w [oknie dialogowym połączenia zdalne](#remote-connections).

    ![Zarządzane właściwości projektu dla zdalnego debugowania](../debugger/media/vsrun_managed_projprop_remote.png "Właściwości zarządzanego projektu debugowania")

### <a name="configure-a-c-project-for-remote-debugging"></a><a name="BKMK_Choosing_the_remote_device_for_JavaScript_and_C___projects"></a> Konfigurowanie projektu C++ na potrzeby debugowania zdalnego

1. Wybierz projekt C++ w programie Visual Studio **Eksplorator rozwiązań** i wybierz ikonę **Właściwości** , naciśnij klawisz **Alt** + **Enter** lub kliknij prawym przyciskiem myszy i wybierz polecenie **Właściwości**.

1. Wybierz kartę **debugowanie** .

3. W obszarze **debuger do uruchomienia** wybierz pozycję **maszyna zdalna** dla komputera zdalnego lub **urządzenie** dla bezpośrednio podłączonego urządzenia z systemem Windows Mobile 10.

1. W przypadku maszyny zdalnej wprowadź lub wybierz nazwę sieci lub adres IP w polu **Nazwa komputera** lub listę rozwijaną, a następnie wybierz pozycję **Znajdź** , aby wyszukać urządzenie w [oknie dialogowym połączenia zdalne](#remote-connections).

    ![Właściwości projektu C++ do zdalnego debugowania](../debugger/media/vsrun_cpp_projprop_remote.png "Debugowanie języka C++ — właściwości projektu")

### <a name="use-the-remote-connections-dialog-box"></a><a name="remote-connections"></a> Korzystanie z okna dialogowego połączenia zdalne

W oknie dialogowym **połączenia zdalne** można wyszukać konkretną nazwę lub adres IP komputera zdalnego lub automatycznie wykryć połączenia, wybierając ikonę odświeżania strzałki w dół. W oknie dialogowym są przeszukiwane tylko urządzenia w podsieci lokalnej, na których jest aktualnie uruchomiony zdalny debuger. Nie wszystkie urządzenia można wykryć w oknie dialogowym **połączenia zdalne** .

 ![Okno dialogowe połączenie zdalne](../debugger/media/vsrun_selectremotedebuggerdlg.png "Okno dialogowe połączeń zdalnych")

>[!TIP]
>Jeśli nie możesz połączyć się z urządzeniem zdalnym według nazwy, spróbuj użyć jego adresu IP. Aby określić adres IP na urządzeniu zdalnym, w oknie wiersza polecenia wpisz polecenie **ipconfig** . Adres IP jest wyświetlany jako **adres IPv4**.

## <a name="download-and-install-the-remote-tools-for-visual-studio"></a><a name="BKMK_download"></a> Pobierz i zainstaluj Remote Tools for Visual Studio

Aby program Visual Studio mógł debugować aplikacje na komputerze zdalnym, na komputerze zdalnym musi być uruchomiony Remote Tools for Visual Studio.

- Urządzenia z systemem Windows Mobile 10 nie wymagają ani nie obsługują narzędzi zdalnych.
- Komputery z systemem Windows 10 z uruchomioną aktualizacją dla twórców (wersja 1703) i nowsze, urządzenia z systemem Windows 10 Xbox, IoT i HoloLens instalują narzędzia zdalne automatycznie podczas wdrażania aplikacji.
- Na komputerach z systemem Windows 10 z aktualizacją przed twórcą należy ręcznie pobrać, zainstalować i uruchomić narzędzia zdalne na komputerze zdalnym przed rozpoczęciem debugowania.

**Aby pobrać i zainstalować narzędzia zdalne:**

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

### <a name="configure-the-remote-tools"></a><a name="BKMK_setup"></a> Konfigurowanie narzędzi zdalnych

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

## <a name="debug-uwp-apps-remotely"></a><a name="BKMK_RunRemoteDebug"></a> Zdalne debugowanie aplikacji platformy UWP

Debugowanie zdalne działa tak samo jak debugowanie lokalne.

1. Upewnij się, że na urządzeniu zdalnym jest uruchomiona *msvsmon.exe* Monitor zdalnego debugowania w wersji Update systemu Windows 10.

1. Na komputerze programu Visual Studio upewnij się, że obok zielonej strzałki na pasku narzędzi pojawia się prawidłowy cel debugowania (**maszyna zdalna** lub **urządzenie**).

1. Rozpocznij debugowanie, wybierając pozycję **Debuguj**  >  **Rozpocznij debugowanie**, naciśnij klawisz **F5** lub wybierz zieloną strzałkę na pasku narzędzi.

   Projekt zostanie ponownie skompilowany, a następnie wdrożony i uruchomiony na urządzeniu zdalnym. Debuger wstrzymuje wykonywanie w punktach przerwania i można przechodzić do, przekroczyć i z kodu.

1. W razie potrzeby wybierz kolejno opcje **Debuguj**  >  **Zatrzymaj debugowanie** lub naciśnij klawisz **SHIFT** + **F5** , aby zatrzymać debugowanie i zamknąć aplikację zdalną.

## <a name="see-also"></a>Zobacz też
- [Zaawansowane opcje zdalnego wdrażania](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options)
- [Testowanie aplikacji platformy UWP za pomocą programu Visual Studio](../test/unit-test-your-code.md)
- [Debugowanie aplikacji platformy UWP w programie Visual Studio](debugging-windows-store-and-windows-universal-apps.md)
