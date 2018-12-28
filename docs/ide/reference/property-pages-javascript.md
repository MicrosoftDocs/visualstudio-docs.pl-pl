---
title: Strony właściwości, JavaScript
ms.date: 06/21/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- javascript.project.property.debugging.debuggertype
- javascript.project.property.debugging.requireauthentication
- javascript.project.property.outputpath
- javascript.project.property.debugging.launchapplication
- javascript.project.property.defaultlanguage
- javascript.project.property.debugging.machinename
- javascript.project.property.debugging.allowlocalnetworkloopback
ms.assetid: a05ab01f-3d5d-4675-a845-eab51807d3a3
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: eabc82926c821fb5a8d83637fb9118bc25df82bc
ms.sourcegitcommit: 935e341a02dba1c2aa3b6e89469388aa6e626f7f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2018
ms.locfileid: "53684996"
---
# <a name="property-pages-javascript"></a>Strony właściwości, JavaScript
**Stron właściwości** zapewnia dostęp do ustawień projektu. Można użyć stron, które pojawiają się w **stron właściwości** można zmienić właściwości projektu.

Aby uzyskać dostęp do właściwości projektu, wybierz węzeł projektu w **Eksploratora rozwiązań**. Na **projektu** menu, kliknij przycisk **właściwości**.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

Następujące strony i opcje są wyświetlane w **stron właściwości**.

## <a name="configuration-and-platform-page"></a>Konfiguracja i strona platformy
 Użyj następujących opcji, aby wybrać konfigurację i platformę do wyświetlenia lub zmodyfikowania.

 **Konfiguracja**

 Określa ustawienia konfiguracji do wyświetlenia lub zmodyfikowania. Ustawienia są **debugowania** (ustawienie domyślne), **wersji**, **wszystkie konfiguracje**, lub Konfiguracja zdefiniowana przez użytkownika. Aby uzyskać więcej informacji, zobacz [jak: Zestaw debugowania i zwalniania konfiguracji w programie Visual Studio](../../debugger/how-to-set-debug-and-release-configurations.md).

 **Platforma**

 Określa ustawienia platformy do wyświetlenia lub zmodyfikowania. Ustawienia są **dowolny Procesor** (domyślne dla [!INCLUDE[win8_appname_long](../../debugger/includes/win8_appname_long_md.md)] aplikacji), **x64**, **ARM**, **x86**, lub platforma zdefiniowana przez użytkownika. Aby uzyskać więcej informacji, zobacz [jak: Zestaw debugowania i zwalniania konfiguracji w programie Visual Studio](../../debugger/how-to-set-debug-and-release-configurations.md).

## <a name="general-page"></a>Strona ogólna
 Następujące opcje służą do ustawiania właściwości ogólnych projektu.

> [!NOTE]
> Niektóre opcje są dostępne tylko w aplikacjach platformy uniwersalnej systemu Windows.


 **Ścieżka wyjściowa**

 Określa położenie plików wyjściowych dla tej konfiguracji projektu. Ścieżka jest względna; Jeśli wprowadzasz ścieżkę bezwzględną, ścieżka bezwzględna jest zapisywana w projekcie. Domyślna ścieżka to bin\Debug.

 Korzystając z uproszczonych konfiguracjach kompilacji system projektu określa, czy do kompilacji debugowania lub wydania wersji. Po kliknięciu **debugowania**, **Rozpocznij debugowanie** (lub naciśnij klawisz F5) kompilacja jest umieszczany w lokalizacji debugowania bez względu na to **ścieżkę wyjściową** określisz. Jednak **Kompiluj rozwiązanie** polecenie **kompilacji** menu umieszcza go w miejscu określonym przez użytkownika. Aby włączyć zaawansowane konfiguracje kompilacji, na pasku menu wybierz **narzędzia**, **opcje**. W **opcje** okna dialogowego rozwiń **projekty i rozwiązania**, wybierz opcję **ogólne**, a następnie wyczyść **Pokaż zaawansowane konfiguracjekompilacji**pole wyboru. Daje to ręczne sterowanie wszystkimi wartościami konfiguracji i czy jest wbudowana wersja debugowania lub publikacji.

 **Język domyślny**

 Określa język domyślny dla projektu. Opcja języka wybranego w **zegar, język i Region** w Panelu sterowania określa język preferowany przez użytkownika. Określając język domyślny dla projektu, należy upewnić się, że zasoby określonego domyślnego języka są używane, jeśli język preferowany przez użytkownika nie jest zgodny z zasobami językowymi aplikacji.

## <a name="debug-page"></a>Strona debugowania
 Aby ustawić właściwości do debugowania zachowania w projekcie, należy użyć następujących opcji.

> [!NOTE]
> Niektóre opcje są dostępne tylko w aplikacjach platformy uniwersalnej systemu Windows.


 **Debuger do uruchomienia**

 Określa host domyślny dla debugera.

-   Wybierz **komputera lokalnego** Aby uruchomić aplikację na komputerze-hoście programu Visual Studio. Aby uzyskać więcej informacji, zobacz [uruchamianie aplikacji na komputerze lokalnym](../../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md).

-   Wybierz **symulator** Aby uruchomić aplikację w symulatorze. Aby uzyskać więcej informacji, zobacz [uruchamiania aplikacji w symulatorze](../../debugger/run-windows-store-apps-in-the-simulator.md).

-   Wybierz **maszyny zdalnej** Aby uruchomić aplikację na komputerze zdalnym. Aby uzyskać więcej informacji na temat debugowania zdalnego, zobacz [uruchamianie aplikacji na komputerze zdalnym](../../debugger/run-windows-store-apps-on-a-remote-machine.md).

**Uruchamianie aplikacji**

Określa, czy uruchomić aplikację po naciśnięciu klawisza F5 lub kliknij przycisk **debugowania**, **Rozpocznij debugowanie**. Wybierz **tak** do uruchamiania aplikacji; w przeciwnym razie wybierz **nie**. Jeśli wybierzesz **nie**, nadal można debugować aplikację, jeśli używasz innej metody jej uruchomienia.

**Typ debugera**

Określa typy kodu do debugowania. Wybierz **tylko skrypt** do debugowania kodu JavaScript. Wybierz **tylko zarządzane** do debugowania kodu, który jest zarządzany przez środowisko uruchomieniowe języka wspólnego. Wybierz **tylko natywny** do debugowania kodu C++. Wybierz **natywny ze skryptem** debugowania C++ i JavaScript. Wybierz **mieszany (zarządzany i natywny)** do debugowania zarządzanego, jak i kodu w języku C++.

**Zezwalaj na sprzężenie zwrotne sieci lokalnej**

Określa, czy adres IP sprzężenia zwrotnego jest dostęp do testowania aplikacji. Wybierz **tak** Aby zezwolić na użycie adresu sprzężenia zwrotnego Jeśli aplikacja klienta znajduje się na tym samym komputerze, gdzie aplikacja serwera jest uruchomiona; w przeciwnym razie, wybierz **nie**. Ta właściwość jest dostępna tylko wtedy, gdy **debuger do uruchomienia** właściwość jest ustawiona na **maszyny zdalnej**.

**Nazwa maszyny**

Określa nazwę komputera zdalnego hostującego debuger. Ta właściwość jest dostępna tylko wtedy, gdy **debuger do uruchomienia** ustawiono **maszyny zdalnej**.

**Wymagaj uwierzytelniania**

Określa, czy komputer zdalny wymaga uwierzytelniania. Ta właściwość jest dostępna tylko wtedy, gdy **debuger do uruchomienia** ustawiono **maszyny zdalnej**.
