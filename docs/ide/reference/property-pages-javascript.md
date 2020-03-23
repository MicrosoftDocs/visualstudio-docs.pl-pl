---
title: Strony właściwości, JavaScript
ms.date: 06/21/2017
ms.technology: vs-javascript
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6883e556cd70adddd45fd442d338e10d1cafa1e2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "68926195"
---
# <a name="property-pages-javascript"></a>Strony właściwości, JavaScript

**Strony właściwości** zapewniają dostęp do ustawień projektu. Za pomocą stron wyświetlanych na **stronach właściwości** można zmieniać właściwości projektu.

Aby uzyskać dostęp do właściwości projektu, wybierz węzeł projektu w **Eksploratorze rozwiązań**. W menu **Projekt** kliknij polecenie **Właściwości**.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

Na **stronach właściwości**pojawią się następujące strony i opcje .

## <a name="configuration-and-platform-page"></a>Konfiguracja i strona platformy

Użyj następujących opcji, aby wybrać konfigurację i platformę do wyświetlenia lub zmodyfikowania.

 **Konfiguracja**

Określa ustawienia konfiguracji do wyświetlenia lub zmodyfikowania. Ustawienia to **Debug** (domyślnie), **Zwolnij,** **Wszystkie konfiguracje**lub konfiguracja zdefiniowana przez użytkownika. Aby uzyskać więcej informacji, zobacz [Jak: Ustawianie konfiguracji debugowania i zwalniania w programie Visual Studio](../../debugger/how-to-set-debug-and-release-configurations.md).

 **Platforma**

Określa ustawienia platformy do wyświetlenia lub zmodyfikowania. Ustawienia to Dowolny procesor [!INCLUDE[win8_appname_long](../../debugger/includes/win8_appname_long_md.md)] **(domyślny** dla aplikacji), **x64**, **ARM,** **x86**lub platforma zdefiniowana przez użytkownika. Aby uzyskać więcej informacji, zobacz [Jak: Ustawianie konfiguracji debugowania i zwalniania w programie Visual Studio](../../debugger/how-to-set-debug-and-release-configurations.md).

## <a name="general-page"></a>Strona ogólna

Aby ustawić ogólne właściwości projektu, należy użyć następujących opcji.

> [!NOTE]
> Niektóre opcje są dostępne tylko w aplikacjach platformy uniwersalnej systemu Windows.

 **Ścieżka wyjściowa**

Określa lokalizację plików wyjściowych dla konfiguracji projektu. Ścieżka jest względna; jeśli wprowadzisz ścieżkę bezwzględną, ścieżka bezwzględna zostanie zapisana w projekcie. Domyślną ścieżką jest bin\Debug.

W przypadku korzystania z uproszczonych konfiguracji kompilacji system projektu określa, czy utworzyć wersję debugowania lub wersji. Po kliknięciu **debugowania** > **start debugowania** (lub naciśnij **klawisz F5),** kompilacja jest umieszczana w lokalizacji debugowania, niezależnie od ścieżki **wyjściowej,** którą określisz. Jednak polecenie **Build Solution** w menu **Kompilacja** umieszcza go w określonej lokalizacji. Aby włączyć zaawansowane konfiguracje kompilacji, na pasku menu wybierz pozycję**Opcje** **narzędzi** > . W oknie dialogowym **Opcje** rozwiń pozycję **Projekty i rozwiązania**, wybierz pozycję **Ogólne**, a następnie wyczyść pole wyboru Pokaż **zaawansowane konfiguracje kompilacji.** Zapewnia to ręczną kontrolę nad wszystkimi wartościami konfiguracji i czy jest zbudowana wersja debugowania lub wersji.

 **Język domyślny**

Określa domyślny język projektu. Opcja języka wybrana w **panelu Zegar, Język i Region** w Panelu sterowania określa preferowany język użytkownika. Określając domyślny język dla projektu, upewnij się, że określone domyślne zasoby języka są używane, jeśli preferowany język użytkownika nie jest zgodny z zasobami językowymi podanymi w aplikacji.

## <a name="debug-page"></a>Strona debugowania

Użyj następujących opcji, aby ustawić właściwości debugowania zachowanie w projekcie.

> [!NOTE]
> Niektóre opcje są dostępne tylko w aplikacjach platformy uniwersalnej systemu Windows.

 **Debuger do uruchomienia**

Określa domyślny host debugera.

- Wybierz **opcję Komputer lokalny,** aby uruchomić aplikację na komputerze-hoście programu Visual Studio. Aby uzyskać więcej informacji, zobacz [Uruchamianie aplikacji na komputerze lokalnym](../../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md).

- Wybierz **opcję Symulator,** aby uruchomić aplikację w symulatorze. Aby uzyskać więcej informacji, zobacz [Uruchamianie aplikacji w symulatorze](../../debugger/run-windows-store-apps-in-the-simulator.md).

- Wybierz **opcję Komputer zdalny,** aby uruchomić aplikację na komputerze zdalnym. Aby uzyskać więcej informacji na temat zdalnego debugowania, zobacz [Uruchamianie aplikacji na komputerze zdalnym](../../debugger/run-windows-store-apps-on-a-remote-machine.md).

**Uruchom aplikację**

Określa, czy aplikacja ma być uruchamiana po naciśnięciu **klawisza F5,** czy kliknięciu przycisku **Debugowanie** > **rozpocznij debugowania**. Wybierz **opcję Tak,** aby uruchomić aplikację; w przeciwnym razie wybierz **opcję Nie**. Jeśli wybierzesz **nie**, nadal można debugować aplikację, jeśli używasz innej metody, aby ją uruchomić.

**Typ debugera**

Określa typy kodu do debugowania. Wybierz **opcję Tylko skrypt,** aby debugować kod JavaScript. Wybierz **opcję Zarządzana tylko** do debugowania kodu zarządzanego przez środowisko uruchomieniowe języka wspólnego. Wybierz **opcję Tylko natywne,** aby debugować kod C++. Wybierz **opcję Natywny ze skryptem,** aby debugować c++ i javascript. Wybierz **opcję Mieszane (zarządzane i natywne),** aby debugować kod zarządzany i c++.

**Zezwalaj na sprzężenie zwrotne sieci lokalnej**

Określa, czy dostęp do adresu sprzężenia zwrotnego ip jest dozwolony do testowania aplikacji. Wybierz **opcję Tak,** aby zezwolić na użycie adresu sprzężenia zwrotnego, jeśli aplikacja kliencka znajduje się na tym samym komputerze, na którym jest uruchomiona aplikacja serwera; w przeciwnym razie wybierz **opcję Nie**. Ta właściwość jest dostępna tylko wtedy, gdy **debuger do uruchomienia** właściwość jest **ustawiona**na Remote Machine .

**Nazwa maszyny**

Określa nazwę komputera zdalnego do obsługi debugera. Ta właściwość jest dostępna tylko wtedy, **gdy debuger do uruchomienia** jest ustawiony na Komputer **zdalny**.

**Wymagaj uwierzytelniania**

Określa, czy komputer zdalny wymaga uwierzytelniania. Ta właściwość jest dostępna tylko wtedy, **gdy debuger do uruchomienia** jest ustawiony na Komputer **zdalny**.
