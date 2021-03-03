---
title: Przygotowanie do debugowania projektów C++ | Microsoft Docs
description: Uzyskaj informacje na temat przygotowania do debugowania podstawowych typów projektów utworzonych przez szablony projektów Visual C++ w programie Visual Studio.
ms.custom: SEO-VS-2020, seodec18
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
ms.openlocfilehash: d91d18208a2d05fc4d4b60da98e3e3f8e3c0c835
ms.sourcegitcommit: 5654b7a57a9af111a6f29239212d76086bc745c9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/03/2021
ms.locfileid: "101683045"
---
# <a name="debugging-preparation-c-project-types"></a>Przygotowanie debugowania: typy projektów C++
W tej sekcji opisano sposób debugowania podstawowych typów projektów utworzonych przez [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] Szablony projektu.

 Należy zauważyć, że te typy projektów, które tworzą biblioteki DLL jako dane wyjściowe, zostały pogrupowane w celu [debugowania projektów DLL](../debugger/debugging-dll-projects.md) ze względu na typowe funkcje, które udostępniają.

## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a> W tym temacie
 [Zalecane ustawienia właściwości](#BKMK_Recommended_Property_Settings)

 [Projekty Win32](#BKMK_Win32_Projects)

- [Aby debugować aplikację systemu Win32 w języku C lub C++](#BKMK_To_debug_a_C_or_C___Win32_application)

- [Aby ręcznie ustawić konfigurację debugowania](#BKMK_To_manually_set_a_Debug_configuration)

## <a name="recommended-property-settings"></a><a name="BKMK_Recommended_Property_Settings"></a> Zalecane ustawienia właściwości
 Niektóre właściwości powinny być ustawiane w taki sam sposób dla wszystkich niezarządzanych scenariuszy debugowania. W poniższych tabelach są wyświetlane zalecane ustawienia właściwości. Ustawienia niewymienione w tym miejscu mogą się różnić w różnych niezarządzanych typach projektów. Aby uzyskać więcej informacji, zobacz [Ustawienia projektu dla konfiguracji debugowania języka C++](../debugger/project-settings-for-a-cpp-debug-configuration.md).

### <a name="configuration-properties-124-cc-124-optimization-node"></a>Właściwości konfiguracji &#124; węźle Optymalizacja &#124; C/C++

|Nazwa właściwości|Ustawienie|
|-------------------|-------------|
|**Optymalizacja**|Ustawienie **wyłączone (/0D).** Zoptymalizowany kod jest trudniejszy do debugowania, ponieważ wygenerowane instrukcje nie odpowiadają bezpośrednio na kod źródłowy. Jeśli okaże się, że program ma usterkę, która pojawia się tylko w zoptymalizowanym kodzie, można włączyć to ustawienie, ale należy pamiętać, że kod wyświetlany w oknie **demontażu** jest generowany na podstawie zoptymalizowanego źródła, które może być niezgodne z danymi wyświetlanymi w oknach źródłowych. Inne funkcje, takie jak Krokowe, mogą nie zachowywać się zgodnie z oczekiwaniami.|

### <a name="configuration-properties-124-linker-124-debugging-node"></a>Właściwości konfiguracji &#124; węzeł debugowania &#124; konsolidatora

|Nazwa właściwości|Ustawienie|
|-------------------|-------------|
|**Generuj informacje o debugowaniu**|Zawsze należy ustawić tę opcję na **wartość tak (/Debug)** , aby utworzyć symbole debugowania i pliki potrzebne do debugowania. Gdy aplikacja przechodzi do środowiska produkcyjnego, można ustawić ją na off.|

 [W tym temacie](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)

## <a name="win32-projects"></a><a name="BKMK_Win32_Projects"></a> Projekty Win32
 Aplikacje Win32 są tradycyjnymi programami systemu Windows, które są zapisywane w języku C lub C++. Debugowanie tego typu aplikacji w programie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] jest proste.

 Aplikacje Win32 zawierają aplikacje MFC i projekty ATL. Korzystają one z interfejsów API systemu Windows i mogą korzystać z MFC lub ATL, ale nie używają środowiska uruchomieniowego języka wspólnego (CLR). Mogą jednak wywołać kod zarządzany, który używa środowiska CLR.

 Poniższa procedura wyjaśnia, jak debugować projekt Win32 z poziomu programu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Innym sposobem na Debugowanie aplikacji Win32 jest uruchomienie aplikacji poza programem [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] i dołączenie do niej. Aby uzyskać więcej informacji, zobacz [dołączanie do uruchomionych procesów](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

### <a name="to-debug-a-c-or-c-win32-application"></a><a name="BKMK_To_debug_a_C_or_C___Win32_application"></a> Aby debugować aplikację systemu Win32 w języku C lub C++

1. Otwórz projekt w programie Visual Studio.

2. W menu **debugowanie** wybierz polecenie **Uruchom**.

3. Debuguj przy użyciu technik omówionych w [pierwszej kolejności w debugerze](../debugger/debugger-feature-tour.md).

### <a name="to-manually-set-a-debug-configuration"></a><a name="BKMK_To_manually_set_a_Debug_configuration"></a> Aby ręcznie ustawić konfigurację debugowania

1. W menu **Widok** kliknij polecenie **strony właściwości**.

2. Kliknij węzeł **Właściwości konfiguracji** , aby go otworzyć, jeśli nie jest jeszcze

3. Wybierz pozycję **Ogólne** i ustaw wartość wiersza **danych wyjściowych** na **Debuguj**.

4. Otwórz węzeł **C/C++** i wybierz pozycję **Ogólne**.

    W wierszu **debugowania** należy określić typ informacji o debugowaniu, które mają być generowane przez kompilator. Wartości, które można wybrać, zawierają **bazę danych programu (/ZI)** lub **bazę danych programu do edycji & Kontynuuj (/ZI)**.

5. Wybierz opcję **Optymalizacja**, a w wierszu **Optymalizacja** wybierz pozycję **wyłączone (/0D)** z listy rozwijanej.

    Zoptymalizowany kod jest trudniejszy do debugowania, ponieważ wygenerowane instrukcje nie odpowiadają bezpośrednio na kod źródłowy. Jeśli okaże się, że program ma usterkę, która pojawia się tylko w zoptymalizowanym kodzie, można włączyć to ustawienie, ale należy pamiętać, że kod wyświetlany w oknie demontażu jest generowany na podstawie zoptymalizowanego źródła, które może nie odpowiadać temu, co widzisz w oknach źródłowych. Funkcje, takie jak Krokowe, mogą pokazywać nieprawidłowe punkty przerwania i punkt wykonania.

6. Otwórz węzeł **konsolidatora** i wybierz pozycję **debugowanie**. W pierwszym **wygenerowanym** wierszu wybierz pozycję **tak (/Debug)** z listy rozwijanej. Zawsze ustawiaj ją podczas debugowania.

   Aby uzyskać więcej informacji, zobacz[Ustawienia projektu dla konfiguracji debugowania języka C++](../debugger/project-settings-for-a-cpp-debug-configuration.md).

   [W tym temacie](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)

## <a name="see-also"></a>Zobacz też
- [Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md)
- [Ustawienia projektu dla konfiguracji debugowania języka C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Dołączanie do uruchomionego programu lub wielu programów](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Konfiguracje debugowania i wydania](../debugger/how-to-set-debug-and-release-configurations.md)