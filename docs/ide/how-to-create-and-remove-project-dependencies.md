---
title: 'Instrukcje: Tworzenie i usuwanie zależności projektu'
ms.date: 06/21/2017
ms.topic: how-to
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
ms.openlocfilehash: ad21aeae2d348f56cb722365cd1e2ded249bbefe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85284467"
---
# <a name="how-to-create-and-remove-project-dependencies"></a>Instrukcje: Tworzenie i usuwanie zależności projektu

Podczas kompilowania rozwiązania, które zawiera wiele projektów, może być konieczne najpierw skompilowanie niektórych projektów w celu wygenerowania kodu używanego przez inne projekty. Gdy projekt zużywa kod wykonywalny wygenerowany przez inny projekt, projekt, który generuje kod, jest określany jako zależność projektu projektu, który zużywa kod. Takie relacje zależności można definiować w oknie dialogowym **zależności projektu** .

## <a name="to-assign-dependencies-to-projects"></a>Aby przypisać zależności do projektów

1. W **Eksplorator rozwiązań**wybierz projekt.

2. W menu **projekt** wybierz pozycję **zależności projektu**.

    Zostanie otwarte okno dialogowe **zależności projektu** .

   > [!NOTE]
   > Opcja **zależności projektu** jest dostępna tylko w rozwiązaniu z więcej niż jednym projektem.

3. Na karcie **zależności** wybierz projekt z menu rozwijanego **projekt** .

4. W polu **zależności od** zaznacz pole wyboru dowolnego innego projektu, który musi zostać skompilowany przed wykonaniem tego projektu.

   Aby można było utworzyć zależności projektu, Twoje rozwiązanie musi zawierać więcej niż jeden projekt.

## <a name="to-remove-dependencies-from-projects"></a>Aby usunąć zależności z projektów

1. W **Eksplorator rozwiązań**wybierz projekt.

2. W menu **projekt** wybierz pozycję **zależności projektu**.

     Zostanie otwarte okno dialogowe **zależności projektu** .

    > [!NOTE]
    > Opcja **zależności projektu** jest dostępna tylko w rozwiązaniu z więcej niż jednym projektem.

3. Na karcie **zależności** wybierz projekt z menu rozwijanego **projekt** .

4. W polu **zależności od** należy wyczyścić pola wyboru obok innych projektów, które nie są już zależnościami tego projektu.

## <a name="see-also"></a>Zobacz też

- [Twórz i czyść projekty i rozwiązania w programie Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
- [Kompilowanie i tworzenie kompilacji](../ide/compiling-and-building-in-visual-studio.md)
- [Opis konfiguracji kompilacji](../ide/understanding-build-configurations.md)
- [Zarządzanie właściwościami projektów i rozwiązań](managing-project-and-solution-properties.md)
