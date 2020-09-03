---
title: Uruchamianie aplikacji ze sklepu Windows na komputerze lokalnym | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: e42a21a8-6423-4caf-b4dc-72b263e76019
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 031d764b95aa0f292702dde6167e0be9826270bf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196325"
---
# <a name="run-windows-store-apps-on-the-local-machine"></a>Uruchamianie aplikacji ze Sklepu Windows na maszynie lokalnej
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dotyczy tylko systemu Windows] (.. /Image/windows_only_content.png "windows_only_content")  
  
 Aby debugować, testować lub uruchamiać analizę wydajności w aplikacji ze sklepu Windows, możesz uruchomić aplikację na tym samym komputerze, na którym znajduje się program Visual Studio. Jeśli na urządzeniu jest włączona funkcja dotyku, możesz korzystać z pełnej funkcjonalności aplikacji. w przeciwnym razie będziesz mieć ograniczone gesty myszy i klawiatury.  
  
## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a> W tym temacie  
 Możesz dowiedzieć się:  
  
 [Jak uruchomić na komputerze lokalnym](#BKMK_How_to_run_on_a_local_machine)  
  
 [Jak przełączać się między aplikacją ze sklepu Windows i programem Visual Studio na jednym monitorze](#BKMK_How_to_switch_between_a_Windows_Store_app_and_Visual_Studio_on_a_single_monitor)  
  
## <a name="how-to-run-on-a-local-machine"></a><a name="BKMK_How_to_run_on_a_local_machine"></a> Jak uruchomić na komputerze lokalnym  
 Aby uruchomić aplikację na komputerze lokalnym, wybierz pozycję **komputer lokalny** z listy rozwijanej obok przycisku Rozpocznij debugowanie na pasku narzędzi **Standardowy** debuger.  
  
 ![Uruchom na komputerze lokalnym](../debugger/media/vsrun-f5-local.png "VSRUN_F5_Local")  
  
 Jeśli nie widzisz **standardowego** paska narzędzi, kliknij menu **Widok** , wskaż polecenie **paski narzędzi**, a następnie kliknij pozycję **Standardowy**.  
  
 Wybór dokonany na liście rozwijanej jest utrwalany w pliku właściwości projektu i stał się domyślnym miejscem docelowym przebiegu.  
  
 Możesz również ustawić cel przebiegu bezpośrednio w pliku właściwości projektu. Kliknij prawym przyciskiem myszy nazwę projektu w **Eksplorator rozwiązań** a następnie wybierz polecenie **Właściwości**. Następnie wykonaj jedną z następujących czynności:  
  
- W obszarze projekty C# i Visual Basic kliknij pozycję **Debuguj** , a następnie wybierz pozycję **komputer lokalny** z listy rozwijanej **urządzenie docelowe** .  
  
     ![Strona właściwości projektu C&#35; i Visual Basic](../debugger/media/vsrun-cs-vb-projprop-local.png "VSRUN_CS_VB_ProjProp_Local")  
  
- W projektach C++ i JavaScript rozwiń węzeł **Właściwości konfiguracji** , kliknij przycisk **debugowanie**, a następnie wybierz pozycję **debuger lokalny** z listy **debuger do uruchomienia** .  
  
     ![Strona właściwości projektu języka C&#43;&#43; i JavaScript](../debugger/media/vsrun-cpp-js-projprop-local.png "VSRUN_CPP_JS_ProjProp_Local")  
  
## <a name="how-to-switch-between-a-windows-store-app-and-visual-studio-on-a-single-monitor"></a><a name="BKMK_How_to_switch_between_a_Windows_Store_app_and_Visual_Studio_on_a_single_monitor"></a> Jak przełączać się między aplikacją ze sklepu Windows i programem Visual Studio na jednym monitorze  
 **Aby przełączyć się z działającego wystąpienia aplikacji ze sklepu Windows do programu Visual Studio**  
  
 Gdy uruchamiasz aplikację ze sklepu Windows na komputerze lokalnym i korzystasz tylko z jednego monitora, możesz chcieć przełączyć się z powrotem do programu Visual Studio, pozostawiając aplikację uruchomioną. Na przykład aplikacja może znajdować się w stanie, który nie może zostać osiągnięty przez punkt przerwania, taki jak oczekiwanie na zdarzenie lub zalewki w pętli długiej lub nieskończonej. Aby powrócić do programu Visual Studio, naciśnij klawisze ALT + TAB.
