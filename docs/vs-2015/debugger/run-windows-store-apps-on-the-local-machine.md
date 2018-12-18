---
title: Uruchom Windows Store apps na komputerze lokalnym | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: e42a21a8-6423-4caf-b4dc-72b263e76019
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 40fafcbdacac8a63a4aba70526a473d091b35de8
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51766839"
---
# <a name="run-windows-store-apps-on-the-local-machine"></a>Uruchom Windows Store apps na lokalnym komputerze
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dotyczy tylko Windows] (.. /Image/windows_only_content.png "windows_only_content")  
  
 Aby debugować, przetestować lub uruchomić analizy wydajności w aplikacji Windows Store, można uruchomić aplikacji na tym samym komputerze obsługującym program Visual Studio. W przypadku wyświetlania na urządzeniu z obsługą dotyku, możesz skorzystać pełnej funkcjonalności aplikacji; w przeciwnym razie będzie ograniczona do gesty myszy i klawiatury.  
  
##  <a name="BKMK_In_this_topic"></a> W tym temacie  
 Możesz dowiedzieć się:  
  
 [Jak uruchomić na komputerze lokalnym](#BKMK_How_to_run_on_a_local_machine)  
  
 [Jak przełączać się między aplikacji Windows Store i programu Visual Studio na pojedynczy monitor](#BKMK_How_to_switch_between_a_Windows_Store_app_and_Visual_Studio_on_a_single_monitor)  
  
##  <a name="BKMK_How_to_run_on_a_local_machine"></a> Jak uruchomić na komputerze lokalnym  
 Aby uruchomić aplikację na komputerze lokalnym, wybierz pozycję **komputera lokalnego** z listy rozwijanej obok przycisku Rozpocznij debugowanie debugera **standardowa** paska narzędzi.  
  
 ![Uruchom na lokalnym komputerze](../debugger/media/vsrun-f5-local.png "VSRUN_F5_Local")  
  
 Jeśli nie widzisz **standardowa** narzędzi, kliknij przycisk **widoku** menu, wskaż **paski narzędzi**, a następnie kliknij przycisk **standardowa**.  
  
 Dokonany wybór jest na liście rozwijanej są utrwalane w pliku właściwości projektu i staje się wartością domyślną, uruchom docelowego.  
  
 Można również ustawić element docelowy wykonywania bezpośrednio w pliku właściwości projektu. Kliknij prawym przyciskiem myszy nazwę projektu w **Eksploratora rozwiązań** , a następnie wybierz **właściwości**. Następnie wykonaj jedną z następujących czynności:  
  
-   W projektach C# i Visual Basic, kliknij przycisk **debugowania** , a następnie wybierz **komputera lokalnego** z **urządzenie docelowe** listy rozwijanej.  
  
     ![C&#35; i strony właściwości projektu Visual Basic](../debugger/media/vsrun-cs-vb-projprop-local.png "VSRUN_CS_VB_ProjProp_Local")  
  
-   W projektach C++ i JavaScript, rozwiń węzeł **właściwości konfiguracji** węzła, kliknij przycisk **debugowanie**, a następnie wybierz pozycję **debuger lokalny** z **debugera Aby uruchomić** listy.  
  
     ![C&#43; &#43; i strony właściwości projektu JavaScript](../debugger/media/vsrun-cpp-js-projprop-local.png "VSRUN_CPP_JS_ProjProp_Local")  
  
##  <a name="BKMK_How_to_switch_between_a_Windows_Store_app_and_Visual_Studio_on_a_single_monitor"></a> Jak przełączać się między aplikacji Windows Store i programu Visual Studio na pojedynczy monitor  
 **Aby przełączyć się z uruchomionego wystąpienia aplikacji Windows Store programu Visual Studio**  
  
 Po uruchomieniu aplikacji Windows Store na maszynie lokalnej i używać tylko jednego monitora, możesz chcieć przejdź z powrotem do programu Visual Studio przy równoczesnym zachowaniu jest uruchomiona aplikacja. Na przykład aplikacja może być w stanie, który nie może być osiągnięty przez punkt przerwania, takich jak oczekiwania na zdarzenie lub zablokował w długich lub nieskończonej pętli. Aby powrócić do programu Visual Studio, naciśnij klawisze ALT + TAB.



