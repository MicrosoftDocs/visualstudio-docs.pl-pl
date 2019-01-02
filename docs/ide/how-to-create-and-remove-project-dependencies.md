---
title: 'Instrukcje: Tworzenie i usuwanie zależności projektu'
ms.date: 06/21/2017
ms.prod: visual-studio-dev15
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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 24f44545ebc591a8e3b1a8359e0d7db8dddbb5d5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53925699"
---
# <a name="how-to-create-and-remove-project-dependencies"></a>Instrukcje: Tworzenie i usuwanie zależności projektu

Podczas kompilowania rozwiązania, które zawiera wiele projektów, może być konieczne do tworzenia niektórych projektów najpierw, aby wygenerować kod używany przez inne projekty. Gdy projekt korzysta z kodu wykonywalnego, generowane przez inny projekt, projekt, który generuje kod nazywa się zależności projektu, projektu, który wykorzystuje kod. Takie relacji zależności można zdefiniować w **zależności projektu** okno dialogowe.

## <a name="to-assign-dependencies-to-projects"></a>Aby przypisać zależności do projektów

1. W **Eksploratora rozwiązań**, wybierz projekt.

2. Na **projektu** menu, wybierz **zależności projektu**.

    **Zależności projektu** zostanie otwarte okno dialogowe.

   > [!NOTE]
   > **Zależności projektu** opcja jest dostępna tylko w rozwiązaniu z więcej niż jeden projekt.

3. Na **zależności** , a następnie wybierz projekt z **projektu** menu rozwijanego.

4. W **zależy od** pól, zaznacz pole wyboru w innych projektów, które należy utworzyć przed tego projektu.

   Rozwiązanie musi składać się z więcej niż jeden projekt, aby można było utworzyć zależności projektu.

## <a name="to-remove-dependencies-from-projects"></a>Aby usunąć zależności z projektów

1.  W **Eksploratora rozwiązań**, wybierz projekt.

2.  Na **projektu** menu, wybierz **zależności projektu**.

     **Zależności projektu** zostanie otwarte okno dialogowe.

    > [!NOTE]
    > **Zależności projektu** opcja jest dostępna tylko w rozwiązaniu z więcej niż jeden projekt.

3.  Na **zależności** , a następnie wybierz projekt z **projektu** menu rozwijanego.

4.  W **zależy od** pola, wyczyść pole wyboru obok pozycji inne projekty, które nie są już zależności dla tego projektu.

## <a name="see-also"></a>Zobacz także

- [Kompilowanie i czyszczenie projektów i rozwiązań w programie Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
- [Kompilowanie i tworzenie kompilacji](../ide/compiling-and-building-in-visual-studio.md)
- [O konfiguracjach kompilacji](../ide/understanding-build-configurations.md)
- [Zarządzanie właściwościami projektów i rozwiązań](managing-project-and-solution-properties.md)