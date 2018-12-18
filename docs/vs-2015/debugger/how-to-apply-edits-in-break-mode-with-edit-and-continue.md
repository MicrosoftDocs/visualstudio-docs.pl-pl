---
title: 'Porady: stosowanie edycji w trybie przerwania za pomocą edycji i kontynuowania | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.variables.failededit
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
helpviewer_keywords:
- Edit and Continue [Visual Basic], applying edits in break mode
- break mode, applying code changes
- Edit and Continue, applying edits in break mode
- editing, break mode
- coding, editing in break mode
- code, editing in break mode
ms.assetid: 1eef7498-6a1f-4fba-8146-510adc6375c9
caps.latest.revision: 33
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5f6024d0c00e492110d7d34172cf225e4712f213
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51807507"
---
# <a name="how-to-apply-edits-in-break-mode-with-edit-and-continue"></a>Porady: stosowanie edycji w trybie przerwania za pomocą pleceń Edytuj i Kontynuuj
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Edytuj i Kontynuuj umożliwia edytowanie kodu w trybie przerwania, a następnie kontynuuj bez zatrzymywania i ponownego uruchamiania wykonywania.  
  
 Edytuj i Kontynuuj nie jest dostępna w następujących scenariuszach debugowania:  
  
-   Debugowanie trybu mieszanego (natywnego/zarządzanego).  
  
-   Debugowanie SQL.  
  
-   Debugowanie odzyskiwania po awarii. Zrzut programu Watson.  
  
-   Edytowanie kodu po wystąpieniu nieobsługiwanego wyjątku, gdy **Unwind na stosie wywołań dotycząca nieobsłużonych wyjątków** nie wybrano opcji.  
  
-   Debugowanie aplikacji osadzonego środowiska uruchomieniowego.  
  
-   Debugowanie aplikacji przy użyciu **dołączyć do** zamiast uruchamiania aplikacji przy użyciu **Start** z **debugowania** menu.  
  
-   Debugowanie zoptymalizowanego kodu.  
  
-   Debugowanie kodu zarządzanego, gdy obiektem docelowym jest aplikacją 64-bitową. Jeśli chcesz Użyj funkcji Edytuj i Kontynuuj, należy ustawić element docelowy x86. (_Projektu_**właściwości**, **skompilować** karcie **zaawansowane kompilatora** ustawienie.).  
  
-   Debugowanie starą wersję kodu po nowej wersji nie powiodło się skompilowanie z powodu błędów kompilacji.  
  
### <a name="to-edit-code-in-break-mode"></a>Do edycji kodu w trybie przerwania  
  
1.  Tryb przerwania, wykonując jedną z następujących czynności:  
  
    -   Ustaw punkt przerwania w kodzie, a następnie wybierz **Rozpocznij debugowanie** z **debugowania** menu i zaczekaj, aż ją w dotarciu do punktu przerwania.  
  
         — lub —  
  
    -   Rozpocznij debugowanie, a następnie wybierz **Przerwij wszystko** z **debugowania** menu.  
  
         — lub —  
  
    -   Gdy wystąpi wyjątek, wybierz pozycję **Włącz edytowanie** na**Asystenta wyjątków**.  
  
2.  Wprowadź wszelkie zmiany kodu żądaną i prawne.  
  
     Aby uzyskać więcej informacji, zobacz [nieobsługiwane zmiany w programie Visual Basic, Edytuj i Kontynuuj](../debugger/unsupported-edits-in-visual-basic-edit-and-continue.md).  
  
    > [!NOTE]
    >  Jeśli spróbujesz kodu, zmiany, które nie jest dozwolona przez Edytuj i Kontynuuj, zmiany będą podkreślone purpurowa linia falista i zadania pojawi się na liście zadań. Nie można kontynuować wykonywania kodu, chyba że można cofnąć zmiany kodu niedozwolony.  
  
3.  Na **debugowania** menu, kliknij przycisk **Kontynuuj** można wznowić wykonywania.  
  
     Kod wykonuje teraz stosowane edycji włączone do projektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Nieobsługiwane edycje w języku Visual Basic, Edytuj i Kontynuuj](../debugger/unsupported-edits-in-visual-basic-edit-and-continue.md)   
 [Edytuj i kontynuuj (Visual Basic)](../debugger/edit-and-continue-visual-basic.md)



