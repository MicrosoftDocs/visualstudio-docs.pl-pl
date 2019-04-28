---
title: 'Instrukcje: Tworzenie i usuwanie zależności projektu | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.ProjectDependenciesDlg
helpviewer_keywords:
- vs.build.projectdependencies
- project dependencies
- builds [Visual Studio], setting up
- project build configurations, dependencies
- dependencies, project
- projects [Visual Studio], dependencies
ms.assetid: e2a0a8ff-dae7-40a8-b774-b88aa5235183
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 539b27c914555dad88442fd4d65e1bf8416dae3c
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63422891"
---
# <a name="how-to-create-and-remove-project-dependencies"></a>Instrukcje: Tworzenie i usuwanie zależności projektu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podczas kompilowania rozwiązania, które zawiera wiele projektów, może być konieczne do tworzenia niektórych projektów najpierw, aby wygenerować kod używany przez inne projekty. Gdy projekt korzysta z kodu wykonywalnego, generowane przez inny projekt, projekt, który generuje kod nazywa się zależności projektu, projektu, który wykorzystuje kod. Takie relacji zależności można zdefiniować w **zależności projektu** okno dialogowe.  
  
### <a name="to-assign-dependencies-to-projects"></a>Aby przypisać zależności do projektów  
  
1. W Eksploratorze rozwiązań wybierz projekt.  
  
2. Na **projektu** menu, wybierz **zależności projektu**.  
  
    **Zależności projektu** zostanie otwarte okno dialogowe.  
  
   > [!NOTE]
   > **Zależności projektu** opcja jest dostępna tylko w rozwiązaniu z więcej niż jeden projekt.  
  
3. Na **zależności** , a następnie wybierz projekt z **projektu** menu rozwijanego.  
  
4. W **zależy od** pól, zaznacz pole wyboru w innych projektów, które należy utworzyć przed tego projektu.  
  
   Rozwiązanie musi składać się z więcej niż jeden projekt, aby można było utworzyć zależności projektu.  
  
### <a name="to-remove-dependencies-from-projects"></a>Aby usunąć zależności z projektów  
  
1. W Eksploratorze rozwiązań wybierz projekt.  
  
2. Na **projektu** menu, wybierz **zależności projektu**.  
  
     **Zależności projektu** zostanie otwarte okno dialogowe.  
  
    > [!NOTE]
    > **Zależności projektu** opcja jest dostępna tylko w rozwiązaniu z więcej niż jeden projekt.  
  
3. Na **zależności** , a następnie wybierz projekt z **projektu** menu rozwijanego.  
  
4. W **zależy od** pola, wyczyść pole wyboru obok pozycji inne projekty, które nie są już zależności dla tego projektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilowanie oraz Oczyszczanie projektów i rozwiązań w programie Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)   
 [Kompilowanie i tworzenie](../ide/compiling-and-building-in-visual-studio.md)   
 [Ogólne informacje o konfiguracjach kompilacji](../ide/understanding-build-configurations.md)   
 [NIB jak: Modyfikowanie właściwości projektu i ustawień konfiguracji](http://msdn.microsoft.com/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)
