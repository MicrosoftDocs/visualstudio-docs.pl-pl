---
title: Przygotowywanie do C++ debugowania projektów | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- project templates, debugging
- C++ projects, debugging
- debug builds, project settings
- debugging [C++]
ms.assetid: 912b4ba2-7719-43d5-b087-db33e3f9329a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 9c7d223b9ea542177176045c9abd103958e5ae33
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738111"
---
# <a name="debugging-preparation-c-project-types"></a>Przygotowanie debugowania: C++ typy projektów
W tej sekcji opisano sposób debugowania podstawowych typów projektów utworzonych przez [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] szablonów projektu.

 Należy zauważyć, że te typy projektów, które tworzą biblioteki DLL jako dane wyjściowe, zostały pogrupowane w celu [debugowania projektów DLL](../debugger/debugging-dll-projects.md) ze względu na typowe funkcje, które udostępniają.

## <a name="BKMK_In_this_topic"></a>W tym temacie
 [Zalecane ustawienia właściwości](#BKMK_Recommended_Property_Settings)

 [Projekty Win32](#BKMK_Win32_Projects)

- [Aby debugować aplikację C lub C++ Win32](#BKMK_To_debug_a_C_or_C___Win32_application)

- [Aby ręcznie ustawić konfigurację debugowania](#BKMK_To_manually_set_a_Debug_configuration)

  [Aplikacje Windows Forms (.NET)](#BKMK_Windows_Forms_Applications___NET_)

## <a name="BKMK_Recommended_Property_Settings"></a>Zalecane ustawienia właściwości
 Niektóre właściwości powinny być ustawiane w taki sam sposób dla wszystkich niezarządzanych scenariuszy debugowania. W poniższych tabelach są wyświetlane zalecane ustawienia właściwości. Ustawienia niewymienione w tym miejscu mogą się różnić w różnych niezarządzanych typach projektów. Aby uzyskać więcej informacji, zobacz [Ustawienia projektu dla C++ konfiguracji debugowania](../debugger/project-settings-for-a-cpp-debug-configuration.md).

### <a name="configuration-properties-124-cc-124-optimization-node"></a>Właściwości &#124; konfiguracji — węzełC++ &#124; C/Optymalizacja

|Nazwa właściwości|Ustawienie|
|-------------------|-------------|
|**Optymalizacja**|Ustawienie **wyłączone (/0D).** Zoptymalizowany kod jest trudniejszy do debugowania, ponieważ wygenerowane instrukcje nie odpowiadają bezpośrednio na kod źródłowy. Jeśli okaże się, że program ma usterkę, która pojawia się tylko w zoptymalizowanym kodzie, można włączyć to ustawienie, ale należy pamiętać, że kod wyświetlany w oknie **demontażu** jest generowany na podstawie zoptymalizowanego źródła, które może być niezgodne z danymi wyświetlanymi w oknach źródłowych. Inne funkcje, takie jak Krokowe, mogą nie zachowywać się zgodnie z oczekiwaniami.|

### <a name="configuration-properties-124-linker-124-debugging-node"></a>Właściwości &#124; konfiguracji węzeł &#124; debugowania konsolidatora

|Nazwa właściwości|Ustawienie|
|-------------------|-------------|
|**Generuj informacje o debugowaniu**|Zawsze należy ustawić tę opcję na **wartość tak (/Debug)** , aby utworzyć symbole debugowania i pliki potrzebne do debugowania. Gdy aplikacja przechodzi do środowiska produkcyjnego, można ustawić ją na off.|

 [W tym temacie](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)

## <a name="BKMK_Win32_Projects"></a>Projekty Win32
 Aplikacje Win32 są tradycyjnymi programami systemu Windows, które C++są zapisywane w języku C lub. Debugowanie tego typu aplikacji w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] jest proste.

 Aplikacje Win32 zawierają aplikacje MFC i projekty ATL. Korzystają one z interfejsów API systemu Windows i mogą korzystać z MFC lub ATL, ale nie używają środowiska uruchomieniowego języka wspólnego (CLR). Mogą jednak wywołać kod zarządzany, który używa środowiska CLR.

 Poniższa procedura wyjaśnia, jak debugować projekt Win32 z poziomu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Innym sposobem debugowania aplikacji Win32 jest uruchomienie aplikacji poza [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] i dołączenie do niej. Aby uzyskać więcej informacji, zobacz [dołączanie do uruchomionych procesów](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

### <a name="BKMK_To_debug_a_C_or_C___Win32_application"></a>Aby debugować aplikację C lub C++ Win32

1. Otwórz projekt w programie Visual Studio.

2. W menu **debugowanie** wybierz polecenie **Uruchom**.

3. Debuguj przy użyciu technik omówionych w [pierwszej kolejności w debugerze](../debugger/debugger-feature-tour.md).

### <a name="BKMK_To_manually_set_a_Debug_configuration"></a>Aby ręcznie ustawić konfigurację debugowania

1. W menu **Widok** kliknij polecenie **strony właściwości**.

2. Kliknij węzeł **Właściwości konfiguracji** , aby go otworzyć, jeśli nie jest jeszcze

3. Wybierz pozycję **Ogólne**i ustaw wartość wiersza **danych wyjściowych** na **Debuguj**.

4. Otwórz węzeł **C/C++**  , a następnie wybierz pozycję **Ogólne**.

    W wierszu **debugowania** należy określić typ informacji o debugowaniu, które mają być generowane przez kompilator. Wartości, które można wybrać, zawierają **bazę danych programu (/ZI)** lub **bazę danych programu do edycji & Kontynuuj (/ZI)** .

5. Wybierz opcję **Optymalizacja**, a w wierszu **Optymalizacja** wybierz pozycję **wyłączone (/0D)** z listy rozwijanej.

    Zoptymalizowany kod jest trudniejszy do debugowania, ponieważ wygenerowane instrukcje nie odpowiadają bezpośrednio na kod źródłowy. Jeśli okaże się, że program ma usterkę, która pojawia się tylko w zoptymalizowanym kodzie, można włączyć to ustawienie, ale należy pamiętać, że kod wyświetlany w oknie demontażu jest generowany na podstawie zoptymalizowanego źródła, które może nie odpowiadać temu, co widzisz w oknach źródłowych. Funkcje, takie jak Krokowe, mogą pokazywać nieprawidłowe punkty przerwania i punkt wykonania.

6. Otwórz węzeł **konsolidatora** i wybierz pozycję **debugowanie**. W pierwszym **wygenerowanym** wierszu wybierz pozycję **tak (/Debug)** z listy rozwijanej. Zawsze ustawiaj ją podczas debugowania.

   Aby uzyskać więcej informacji, zobacz[Ustawienia projektu dla C++ konfiguracji debugowania](../debugger/project-settings-for-a-cpp-debug-configuration.md).

   [W tym temacie](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)

## <a name="BKMK_Windows_Forms_Applications___NET_"></a>Aplikacje Windows Forms (.NET)
 Szablon **aplikacji Windows Forms (.NET)** tworzy [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] aplikacji Windows Forms. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie projektu aplikacji systemu Windows](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/42wc9kk5(v=vs.100)).

 Debugowanie tego typu aplikacji w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] jest podobne do programu w zarządzanych Windows Forms aplikacjach.

 Podczas tworzenia projektu Windows Forms przy użyciu szablonu projektu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] automatycznie tworzy wymagane ustawienia dla konfiguracji debugowania i wydania. W razie potrzeby możesz zmienić te ustawienia w oknie dialogowym **\<project nazwa > strony właściwości** . Aby uzyskać więcej informacji, zobacz [debugowanie i wydawanie konfiguracji](../debugger/how-to-set-debug-and-release-configurations.md).

 Aby uzyskać więcej informacji, zobacz [Ustawienia projektu dla C++ konfiguracji debugowania](../debugger/project-settings-for-a-cpp-debug-configuration.md).

 Innym sposobem na Debugowanie aplikacji Windows Forms jest uruchomienie aplikacji poza [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] i dołączenie do niej. Aby uzyskać więcej informacji, zobacz [dołączanie do działającego programu lub wielu programów](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

 [W tym temacie](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)

## <a name="see-also"></a>Zobacz także
- [Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md)
- [Ustawienia projektu dla konfiguracji debugowania w języku C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Dołączanie do uruchomionego programu lub wielu programów](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Konfiguracje debugowania i wydania](../debugger/how-to-set-debug-and-release-configurations.md)
- [Instrukcje: Tworzenie projektu aplikacji systemu Windows](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/42wc9kk5(v=vs.100))