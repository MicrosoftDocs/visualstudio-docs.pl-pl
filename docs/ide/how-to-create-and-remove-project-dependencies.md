---
title: 'Jak: Tworzenie i usuwanie zależności projektu'
ms.date: 06/21/2017
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
ms.technology: vs-ide-compile
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0a286a84d01c6a49b32445106488688ba5b489be
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114542"
---
# <a name="how-to-create-and-remove-project-dependencies"></a>Jak: Tworzenie i usuwanie zależności projektu

Podczas tworzenia rozwiązania, które zawiera wiele projektów, może być konieczne najpierw utworzyć niektóre projekty, aby wygenerować kod używany przez inne projekty. Gdy projekt zużywa kod wykonywalny generowany przez inny projekt, projekt, który generuje kod jest określany jako zależność projektu, który zużywa kod. Takie relacje zależności można zdefiniować w oknie dialogowym **Zależności projektu.**

## <a name="to-assign-dependencies-to-projects"></a>Aby przypisać zależności do projektów

1. W **Eksploratorze rozwiązań**wybierz projekt.

2. W menu **Projekt** wybierz polecenie **Zależności projektu**.

    Zostanie otwarte okno dialogowe **Zależności projektu.**

   > [!NOTE]
   > Opcja **Zależności projektu** jest dostępna tylko w rozwiązaniu z więcej niż jednym projektem.

3. Na karcie **Zależności** wybierz projekt z menu rozwijanego **Projekt.**

4. W polu **Zależy od** zaznacz pole wyboru dowolnego innego projektu, który musi zostać skompilowy przed rozpoczęciem realizacji tego projektu.

   Rozwiązanie musi składać się z więcej niż jednego projektu, zanim będzie można utworzyć zależności projektu.

## <a name="to-remove-dependencies-from-projects"></a>Aby usunąć zależności z projektów

1. W **Eksploratorze rozwiązań**wybierz projekt.

2. W menu **Projekt** wybierz polecenie **Zależności projektu**.

     Zostanie otwarte okno dialogowe **Zależności projektu.**

    > [!NOTE]
    > Opcja **Zależności projektu** jest dostępna tylko w rozwiązaniu z więcej niż jednym projektem.

3. Na karcie **Zależności** wybierz projekt z menu rozwijanego **Projekt.**

4. W **polu Zależy od** pola wyczyść pola wyboru obok innych projektów, które nie są już zależnościami tego projektu.

## <a name="see-also"></a>Zobacz też

- [Twórz i twórz projekty i rozwiązania w programie Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
- [Kompilowanie i tworzenie kompilacji](../ide/compiling-and-building-in-visual-studio.md)
- [Opis konfiguracji kompilacji](../ide/understanding-build-configurations.md)
- [Zarządzanie właściwościami projektów i rozwiązań](managing-project-and-solution-properties.md)
