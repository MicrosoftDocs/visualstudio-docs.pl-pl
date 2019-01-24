---
title: 'Przygotowanie debugowania: Typy projektów Visual C++ | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- project templates, debugging
- Visual C++ projects, debugging
- debug builds, project settings
- debugging [C++]
ms.assetid: 912b4ba2-7719-43d5-b087-db33e3f9329a
caps.latest.revision: 27
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 59c7e42e005e423a27adc7676a05ebc03cd068d3
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54761110"
---
# <a name="debugging-preparation-visual-c-project-types"></a>Przygotowanie debugowania: Typy projektów Visual C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tej sekcji opisano sposób debugowania projektu podstawowych typów utworzonych przez [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] szablony projektów.  
  
 Należy zauważyć, że tych typów projektów, które tworzenia bibliotek DLL jako dane wyjściowe, zostały zgrupowane jako [debugowanie projektów DLL](../debugger/debugging-dll-projects.md) z powodu typowe funkcje, które współużytkują one.  
  
##  <a name="BKMK_In_this_topic"></a> W tym temacie  
 [Zalecane ustawienia właściwości](#BKMK_Recommended_Property_Settings)  
  
 [Projekty Win32](#BKMK_Win32_Projects)  
  
- [Aby debugować aplikację C lub C++ Win32](#BKMK_To_debug_a_C_or_C___Win32_application)  
  
- [Aby ręcznie ustawić konfiguracji debugowania](#BKMK_To_manually_set_a_Debug_configuration)  
  
  [Aplikacje Windows Forms (.NET)](#BKMK_Windows_Forms_Applications___NET_)  
  
##  <a name="BKMK_Recommended_Property_Settings"></a> Zalecane ustawienia właściwości  
 Taki sam sposób dla wszystkich niezarządzanych scenariuszy debugowania można ustawić niektórych właściwości. Poniższe tabele zawierają zalecane ustawienia właściwości. Ustawienia niewymienione w tym miejscu mogą się różnić między typami inny projekt niezarządzanych. Aby uzyskać więcej informacji, zobacz [ustawienia projektu dla konfiguracji debugowania języka C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)  
  
### <a name="configuration-properties-124-cc-124-optimization-node"></a>Właściwości konfiguracji &#124; C/C++ &#124; węzła optymalizacji  
  
|Nazwa właściwości|Ustawienie|  
|-------------------|-------------|  
|**Optymalizacja**|Ustaw **wyłączony (/ 0 d).** Zoptymalizowany kod jest trudniejszy do debugowania, ponieważ wygenerowane instrukcje nie odpowiadają bezpośrednio kodowi źródłowemu. Jeśli okaże się, że program ma błąd, który pojawia się tylko w zoptymalizowanym kodzie, można włączyć to ustawienie, ale należy pamiętać, że kod w **dezasemblacji** okna jest generowany na podstawie zoptymalizowane źródła, które może nie odpowiadać, zostanie wyświetlony w źródle dla systemu Windows. Inne funkcje, takie jak przechodzenie krok po kroku, mogą nie zachowywać się zgodnie z oczekiwaniami.|  
  
### <a name="configuration-properties-124-linker-124-debugging-node"></a>Właściwości konfiguracji &#124; konsolidatora &#124; debugowanie węzła  
  
|Nazwa właściwości|Ustawienie|  
|-------------------|-------------|  
|**Generuj informacje debugowania**|Zawsze należy ustawić tę opcję, **tak (/ DEBUG)** do tworzenia, debugowania symboli i plików potrzebnych do debugowania. Gdy aplikacja przejdzie do środowiska produkcyjnego, można ustawić go na wyłączone.|  
  
 [W tym temacie](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)  
  
##  <a name="BKMK_Win32_Projects"></a> Projekty Win32  
 Win32 — aplikacje są tradycyjne programy Windows w języku C lub C++. Debugowanie tego typu aplikacji w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] jest bardzo proste.  
  
 Win32 — aplikacje obejmują aplikacje MFC i ATL projektów. Korzystanie z interfejsów API Windows i może używać MFC i ATL, ale nie należy używać środowisko uruchomieniowe języka wspólnego (CLR). Jednakże wywołując ich kodu zarządzanego, który używa środowiska CLR.  
  
 Poniższa procedura wyjaśnia, jak można debugować projekt systemu Win32, z poziomu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Innym sposobem debugowania aplikacji systemu Win32 jest uruchomienie aplikacji poza [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] i dołączyć do niego. Aby uzyskać więcej informacji, zobacz [dołączenia do uruchamiania procesów](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
###  <a name="BKMK_To_debug_a_C_or_C___Win32_application"></a> Aby debugować aplikację C lub C++ Win32  
  
1.  Otwórz projekt w programie Visual Studio.  
  
2.  Na **debugowania** menu, wybierz **Start**.  
  
3.  Debugowanie za pomocą techniki opisane w [podstawy debugera](../debugger/debugger-basics.md).  
  
###  <a name="BKMK_To_manually_set_a_Debug_configuration"></a> Aby ręcznie ustawić konfiguracji debugowania  
  
1. Na **widoku** menu, kliknij przycisk **stron właściwości**.  
  
2. Kliknij przycisk **właściwości konfiguracji** węzeł, aby go otworzyć, jeśli nie jest jeszcze  
  
3. Wybierz **ogólne**i ustaw wartość **dane wyjściowe** wiersz do **debugowania**.  
  
4. Otwórz **C/C++** , a następnie wybierz węzeł **ogólne**.  
  
    W **debugowania** wiersza, określ typ debugowania generowanych przez kompilator informacji. Można wybrać wartości obejmują **bazy danych programu (/Zi)** lub **bazy danych programu dla Edytuj i Kontynuuj (/ZI)**.  
  
5. Wybierz **optymalizacji**, a następnie w **optymalizacji** wiersz, wybierz opcję **wyłączony (/ 0d)** z listy rozwijanej.  
  
    Zoptymalizowany kod jest trudniejszy do debugowania, ponieważ wygenerowane instrukcje nie odpowiadają bezpośrednio kodowi źródłowemu. Jeśli okaże się, że program ma błąd, który pojawia się tylko w zoptymalizowanym kodzie, można włączyć to ustawienie, ale należy pamiętać, że kod przedstawiony w oknie demontażu jest generowany na podstawie zoptymalizowane źródła, które może nie odpowiadać, zostanie wyświetlony w oknach źródłowych. Funkcje, takie jak przechodzenie krok po kroku prawdopodobnie pokazać, że punkty przerwania i wykonywania punktu niepoprawnie.  
  
6. Otwórz **konsolidatora** , a następnie wybierz węzeł **debugowanie**. W pierwszym **Generuj** wiersz, wybierz opcję **tak (/ DEBUG)** z listy rozwijanej. Zawsze ustawiaj podczas debugowania.  
  
   Aby uzyskać więcej informacji, zobacz[ustawienia projektu dla konfiguracji debugowania języka C++](../debugger/project-settings-for-a-cpp-debug-configuration.md).  
  
   [W tym temacie](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)  
  
##  <a name="BKMK_Windows_Forms_Applications___NET_"></a> Aplikacje Windows Forms (.NET)  
 **Windows Forms aplikacji (.NET)** szablon umożliwia utworzenie [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] aplikacji Windows Forms. Aby uzyskać więcej informacji, zobacz [jak: Utwórz projekt aplikacji Windows](http://msdn.microsoft.com/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
 Debugowanie tego typu aplikacji w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] jest podobny, jak w zarządzanych aplikacjach Windows Forms.  
  
 Po utworzeniu projektu Windows Forms przy użyciu szablonu projektu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] automatycznie tworzy wymagane ustawienia konfiguracji Debug i Release. Jeśli to konieczne, możesz zmienić te ustawienia w  **\<Nazwa projektu > Właściwości strony** okno dialogowe. Aby uzyskać więcej informacji, zobacz [konfiguracji Debug i Release](../debugger/how-to-set-debug-and-release-configurations.md).  
  
 Aby uzyskać więcej informacji, zobacz [ustawienia projektu dla konfiguracji debugowania języka C++](../debugger/project-settings-for-a-cpp-debug-configuration.md).  
  
 Innym sposobem debugowania aplikacji Windows Forms jest uruchomienie aplikacji poza [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] i dołączyć do niego. Aby uzyskać więcej informacji, zobacz [dołączanie do uruchamiania programu lub wielu programów](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
 [W tym temacie](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)  
  
## <a name="see-also"></a>Zobacz też  
 [Podstawowe informacje o debugerze](../debugger/debugger-basics.md)   
 [Ustawienia projektu dla konfiguracji debugowania języka C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Dołączanie do programu uruchomione lub wielu programów](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Konfiguracji Debug i Release](../debugger/how-to-set-debug-and-release-configurations.md)   
 [Instrukcje: Utwórz projekt aplikacji Windows](http://msdn.microsoft.com/b2f93fed-c635-4705-8d0e-cf079a264efa)
