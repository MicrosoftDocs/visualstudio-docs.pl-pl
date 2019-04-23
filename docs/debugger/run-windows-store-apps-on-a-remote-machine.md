---
title: Debugowanie aplikacji platformy uniwersalnej systemu Windows na komputerach zdalnych | Dokumentacja firmy Microsoft
ms.date: 10/05/2018
ms.topic: conceptual
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
ms.openlocfilehash: 50d307cd65bfdf534b6ca3586e69bbc27be25e36
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60055388"
---
# <a name="debug-uwp-apps-on-remote-machines-from-visual-studio"></a>Debugowanie aplikacji platformy uniwersalnej systemu Windows na komputerach zdalnych z programu Visual Studio

Visual Studio umożliwia uruchamianie, debugowanie, profilowanie i testowanie aplikacji platformy uniwersalnej Windows (UWP), na innym komputerze lub urządzeniu. Uruchamianie aplikacji platformy uniwersalnej systemu Windows na komputerze zdalnym jest szczególnie przydatne w przypadku, gdy komputer z programem Visual Studio nie obsługuje funkcji specyficznych dla platformy uniwersalnej systemu Windows, takich jak dotyk, lokalizacji geograficznej lub fizycznych orientacji.

## <a name="BKMK_Prerequisites"></a> Wymagania wstępne

Aby debugować aplikację platformy UWP na urządzeniu zdalnym z programu Visual Studio:

- Projekt programu Visual Studio musi być skonfigurowany dla zdalnego debugowania.
- Komputer zdalny i komputer z programem Visual Studio muszą być połączone przez sieć lub podłączone bezpośrednio za pomocą kabla USB lub sieci Ethernet. Debugowanie przez Internet nie jest obsługiwane.
- Należy najpierw [włączyć tryb dewelopera](/windows/uwp/get-started/enable-your-device-for-development) na komputerze programu Visual Studio oraz maszynę zdalną.
- Komputer zdalny musi być uruchomiona Remote Tools for Visual Studio.
  - Niektóre wersje systemu Windows 10, uruchom i automatycznie uruchomić narzędzia zdalne. W przeciwnym razie [zainstalować i uruchomić narzędzia zdalne dla Visual Studio](#BKMK_download).
  - Urządzenia Windows Mobile 10 nie wymagają lub obsługi narzędzi zdalnych.

## <a name="BKMK_ConnectVS"></a> Konfigurowanie projektu programu Visual Studio dla zdalnego debugowania
<a name="BKMK_DirectConnect"></a> Użyj projektu **właściwości** określić urządzenie zdalne, aby nawiązać połączenie. Ustawienia różnią się w zależności od języka programowania.

> [!CAUTION]
> Domyślnie ustawia się na stronie właściwości **uniwersalny (protokół niezaszyfrowanym)** jako **typ uwierzytelniania** dla połączeń zdalnych z systemem Windows 10. Może być konieczne ustawienie **bez uwierzytelniania** nawiązywania połączenia ze zdalnym debugerem. **Uniwersalny (protokół niezaszyfrowanym)** i **bez uwierzytelniania** protokołów mają żadnych zabezpieczeń sieci, więc stanowi zagrożenie dla danych przekazywane między środowiskami deweloperskim i komputerów zdalnych. Wybierz te typy uwierzytelniania tylko dla zaufanych sieci, które możesz się, że nie są zagrożone przez złośliwe lub wrogie działania.
>
>Jeśli wybierzesz **uwierzytelniania Windows** dla **typ uwierzytelniania**, należy zalogować się do maszyny zdalnej podczas debugowania. Zdalny debuger musi również działać w ramach **uwierzytelniania Windows** tryb, z tym samym kontem użytkownika na komputerze programu Visual Studio.

### <a name="BKMK_Choosing_the_remote_device_for_C__and_Visual_Basic_projects"></a> Konfigurowanie C# lub projekcie Visual Basic dla zdalnego debugowania

1. Wybierz C# lub projekcie Visual Basic w programie Visual Studio **Eksploratora rozwiązań** i wybierz **właściwości** ikonę, naciśnij klawisz **Alt** +  **Wprowadź**, lub kliknij prawym przyciskiem myszy i wybierz pozycję **właściwości**.

1. Wybierz **debugowania** kartę.

1. W obszarze **urządzenie docelowe**, wybierz opcję **maszyny zdalnej** na komputerze zdalnym, lub **urządzenia** urządzenia Windows Mobile 10 połączone bezpośrednio.

1. Na komputerze zdalnym, wprowadź nazwę sieci lub adresu IP w **maszyny zdalnej** pola, lub wybierz opcję **znaleźć** wyszukiwania dla urządzenia w [połączeń zdalnych, okno dialogowe](#remote-connections).

    ![Właściwości projektu dla zdalnego debugowania zarządzane](../debugger/media/vsrun_managed_projprop_remote.png "zarządzanego debugowania właściwości projektu")

### <a name="BKMK_Choosing_the_remote_device_for_JavaScript_and_C___projects"></a> Konfigurowanie projektu dla zdalnego debugowania w języku C++

1. Wybierz projekt C++ w programie Visual Studio **Eksploratora rozwiązań** i wybierz **właściwości** ikonę, naciśnij klawisz **Alt**+**Enter**, lub kliknij prawym przyciskiem myszy i wybierz pozycję **właściwości**.

1. Wybierz **debugowanie** kartę.

3. W obszarze **debuger do uruchomienia**, wybierz opcję **maszyny zdalnej** na komputerze zdalnym, lub **urządzenia** urządzenia Windows Mobile 10 połączone bezpośrednio.

1. Na komputerze zdalnym, wprowadź lub wybierz nazwę sieci lub adresu IP w **NazwaKomputera** pola lub listy w dół i wybierz **zlokalizuj** wyszukiwania dla urządzenia w [połączeń zdalnych, okno dialogowe ](#remote-connections).

    ![Właściwości projektu C++ dla zdalnego debugowania](../debugger/media/vsrun_cpp_projprop_remote.png "debugowanie C++ właściwości projektu")

### <a name="remote-connections"></a> Użyj okna dialogowego połączenia zdalne

W **połączeń zdalnych** okno dialogowe, możesz wyszukać nazwę określonego komputera zdalnego lub adres IP lub automatyczne wykrywanie połączeń, wybierając ikonę strzałki zaokrąglone odświeżania. Okno dialogowe przeszukuje tylko te urządzenia w podsieci lokalnej, które są aktualnie uruchomione zdalnego debugera. Nie wszystkie urządzenia można wykryć w **połączeń zdalnych** okno dialogowe.

 ![Zdalne połączenie — okno dialogowe](../debugger/media/vsrun_selectremotedebuggerdlg.png "oknie dialogowym połączeń zdalnych")

>[!TIP]
>Jeśli nie możesz połączyć z urządzeniem zdalnym według nazwy, spróbuj użyć adresu IP. Aby określić adres IP, na urządzeniu zdalnym, wprowadź **ipconfig** w oknie poleceń. Adres IP będzie widoczny jako **adres IPv4**.

## <a name="BKMK_download"></a> Pobieranie i instalowanie narzędzi Remote Tools for Visual Studio

Dla programu Visual Studio do debugowania aplikacji na komputerze zdalnym komputer zdalny musi działać Remote Tools for Visual Studio.

- Urządzenia Windows Mobile 10 nie wymagają ani nie obsługują narzędzi zdalnych.
- Komputerami z systemem Windows 10 jest uruchomiona twórcy aktualizacji (wersja 1703) i później, urządzeń z systemem Windows 10 z konsoli Xbox, IoT i HoloLens Instalowanie narzędzi zdalnych automatycznie podczas wdrażania aplikacji.
- Wstępnie twórcy Update 10 komputery z systemem Windows należy ręcznie Pobierz, zainstaluj i być uruchomione narzędzia zdalne na komputerze docelowym, przed rozpoczęciem debugowania.

**Aby pobrać i zainstalować narzędzia zdalne:**

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

### <a name="BKMK_setup"></a> Konfigurowanie narzędzi zdalnych

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

## <a name="BKMK_RunRemoteDebug"></a> Zdalne debugowanie aplikacji platformy UWP

Zdalne debugowanie działa tak samo, jak debugowanie lokalne.

1. Na wstępnie twórcy wersje aktualizacji systemu Windows 10, upewnij się, Monitor zdalnego debugowania (*msvsmon.exe*) jest uruchomiona na urządzeniu zdalnym.

1. Na komputerze programu Visual Studio, upewnij się, poprawny docelowy debugowania (**maszyny zdalnej** lub **urządzenia**) pojawia się obok zieloną strzałkę na pasku narzędzi.

1. Rozpocznij debugowanie wybierając **debugowania** > **Rozpocznij debugowanie**, naciskając klawisz **F5**, lub wybierając zieloną strzałkę na pasku narzędzi.

   Projekt następuje rekompilacja, a następnie wdraża i rozpoczyna się na urządzeniu zdalnym. Debuger zawiesza wykonywanie w punktach przerwania, a użytkownik może przechodzić do ciągu i z kodu.

1. W razie potrzeby zaznacz **debugowania** > **Zatrzymaj debugowanie** lub naciśnij **Shift**+**F5** Aby zatrzymać debugowanie i zamknąć zdalną aplikację.

## <a name="see-also"></a>Zobacz także
- [Zaawansowane opcje zdalnego wdrażania](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options)
- [Testowanie aplikacji platformy UWP za pomocą programu Visual Studio](/visualstudio/test/create-and-run-unit-tests-for-a-store-app-in-visual-studio/)
- [Debugowanie aplikacji platformy UWP w programie Visual Studio](debugging-windows-store-and-windows-universal-apps.md)
