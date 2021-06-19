---
title: Przygotowanie do debugowania projektów w języku C++ | Microsoft Docs
description: Uzyskaj informacje na temat przygotowywania do debugowania podstawowych typów projektów utworzonych przez Visual C++ szablonów projektów w Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- project templates, debugging
- C++ projects, debugging
- debug builds, project settings
- debugging [C++]
ms.assetid: 912b4ba2-7719-43d5-b087-db33e3f9329a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- cplusplus
ms.openlocfilehash: 258671ca0426cb877d7cdf4bfc0b0f8f6095253c
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387843"
---
# <a name="debugging-preparation-c-project-types"></a>Przygotowanie debugowania: Typy projektów C++
W tej sekcji opisano sposób debugowania podstawowych typów projektów utworzonych przez [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] szablony projektów.

 Należy pamiętać, że te typy projektów, które tworzą biblioteki DLL jako dane wyjściowe, zostały zgrupowane w debugowanie projektów [DLL](../debugger/debugging-dll-projects.md) ze względu na wspólne funkcje, które współdzielą.

## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a> W tym temacie
 [Zalecane ustawienia właściwości](#BKMK_Recommended_Property_Settings)

 [Projekty Win32](#BKMK_Win32_Projects)

- [Aby debugować aplikację Win32 w języku C lub C++](#BKMK_To_debug_a_C_or_C___Win32_application)

- [Aby ręcznie ustawić konfigurację debugowania](#BKMK_To_manually_set_a_Debug_configuration)

## <a name="recommended-property-settings"></a><a name="BKMK_Recommended_Property_Settings"></a> Zalecane ustawienia właściwości
 Niektóre właściwości należy ustawić w taki sam sposób dla wszystkich scenariuszy debugowania nieza pomocą narzędzia do debugowania. W poniższych tabelach przedstawiono zalecane ustawienia właściwości. Ustawienia, których nie wymieniono w tym miejscu, mogą się różnić w zależności od typu projektu nieza zarządzaniem. Aby uzyskać więcej informacji, zobacz Project Settings for a C++ Debug Configuration (Ustawienia [projektu dla konfiguracji debugowania w języku C++).](../debugger/project-settings-for-a-cpp-debug-configuration.md)

### <a name="configuration-properties-124-cc-124-optimization-node"></a>Właściwości konfiguracji &#124; C/C++ &#124; optymalizacji

|Nazwa właściwości|Ustawienie|
|-------------------|-------------|
|**Optymalizacja**|Ustawiono **wartość Wyłączone (/0d).** Zoptymalizowany kod jest trudniejszy do debugowania, ponieważ wygenerowane instrukcje nie odpowiadają bezpośrednio kodowi źródłowemu. Jeśli okaże się, że program ma usterkę, która pojawia się tylko w zoptymalizowanym  kodzie, możesz włączyć to ustawienie, ale pamiętaj, że kod wyświetlany w oknie Dekompełowanie jest generowany ze zoptymalizowanego źródła, które może nie odpowiadać temu, co widzisz w oknach źródłowych. Inne funkcje, takie jak krokowe, mogą nie zachowywać się zgodnie z oczekiwaniami.|

### <a name="configuration-properties-124-linker-124-debugging-node"></a>Właściwości konfiguracji &#124; w węźle &#124; debugowania

|Nazwa właściwości|Ustawienie|
|-------------------|-------------|
|**Generowanie informacji o debugowaniu**|Zawsze należy ustawić tę opcję na **wartość Tak (/DEBUG),** aby tworzyć symbole debugowania i pliki potrzebne do debugowania. Gdy aplikacja przejdzie do produkcji, możesz ją wyłączyć.|

 [W tym temacie](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)

## <a name="win32-projects"></a><a name="BKMK_Win32_Projects"></a> Projekty Win32
 Aplikacje Win32 to tradycyjne programy systemu Windows napisane w języku C lub C++. Debugowanie tego typu aplikacji w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] programie jest proste.

 Aplikacje Win32 obejmują aplikacje MFC i projekty ATL. Używają interfejsów API systemu Windows i mogą używać MFC lub ATL, ale nie używają środowiska uruchomieniowego języka wspólnego (CLR). Mogą jednak wywołać kod zarządzany, który używa clr.

 W poniższej procedurze wyjaśniono, jak debugować projekt Win32 z poziomu programu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Innym sposobem debugowania aplikacji Win32 jest uruchomienie aplikacji poza aplikacją [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] i dołączenie do jej. Aby uzyskać więcej informacji, zobacz [Attach to Running Processes (Dołączanie do uruchomionych procesów).](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)

### <a name="to-debug-a-c-or-c-win32-application"></a><a name="BKMK_To_debug_a_C_or_C___Win32_application"></a> Aby debugować aplikację Win32 w języku C lub C++

1. Otwórz projekt w programie Visual Studio.

2. W menu **Debugowanie** wybierz pozycję **Uruchom.**

3. Debuguj przy użyciu technik omówiowanych w [artykule Pierwsze spojrzenie na debuger](../debugger/debugger-feature-tour.md).

### <a name="to-manually-set-a-debug-configuration"></a><a name="BKMK_To_manually_set_a_Debug_configuration"></a> Aby ręcznie ustawić konfigurację debugowania

1. W menu **Widok** kliknij pozycję **Strony właściwości.**

2. Kliknij węzeł **Właściwości konfiguracji,** aby otworzyć go, jeśli jeszcze go nie ma

3. Wybierz **pozycję Ogólne** i ustaw wartość wiersza Danych **wyjściowych** na **Debuguj.**

4. Otwórz węzeł **C/C++** i wybierz pozycję **Ogólne.**

    W **wierszu** Debugowanie określ typ informacji debugowania, które mają być generowane przez kompilator. Wartości, które można wybrać, to Baza danych **programu (/Zi)** lub Baza danych programu na & **Kontynuuj (/ZI).**

5. Wybierz **pozycję Optymalizacja** i **w** wierszu Optymalizacja wybierz pozycję **Wyłączone (/0d)** z listy rozwijanej.

    Zoptymalizowany kod jest trudniejszy do debugowania, ponieważ wygenerowane instrukcje nie odpowiadają bezpośrednio kodowi źródłowemu. Jeśli okaże się, że program ma usterkę, która pojawia się tylko w zoptymalizowanym kodzie, możesz włączyć to ustawienie, ale pamiętaj, że kod wyświetlany w oknie Dekompełowanie jest generowany ze zoptymalizowanego źródła, które może nie odpowiadać temu, co widzisz w oknach źródłowych. Funkcje, takie jak krokowe, prawdopodobnie będą niepoprawnie pokazywać punkty przerwania i punkt wykonywania.

6. Otwórz węzeł **Linker** i wybierz pozycję **Debugowanie.** W pierwszym **wierszu Generowanie** wybierz pozycję **Tak (/DEBUGUJ)** z listy rozwijanej. Zawsze ustawiaj tę wartość podczas debugowania.

   Aby uzyskać więcej informacji, zobacz Project Settings for a C++ Debug Configuration (Ustawienia[projektu dla konfiguracji debugowania w języku C++).](../debugger/project-settings-for-a-cpp-debug-configuration.md)

   [W tym temacie](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)

## <a name="see-also"></a>Zobacz też
- [Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md)
- [Ustawienia projektu dla konfiguracji debugowania w języku C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Dołączanie do uruchomionego programu lub wielu programów](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Konfiguracje debugowania i wydania](../debugger/how-to-set-debug-and-release-configurations.md)