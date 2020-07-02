---
title: 'Projektant przepływu pracy — How to: dodawanie działań do przybornika'
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: b3a8a785-5928-457a-8a50-30267e29503d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0ebe3f4c3daf5ee3a0f64a0197967b6da62a467b
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85815828"
---
# <a name="how-to-add-activities-to-the-toolbox"></a>Instrukcje: Dodawanie działań do przybornika

Działania można dodawać do **przybornika** w rozwiązaniu na kilka różnych sposobów. Można je dodać z poziomu bieżącego projektu, odwoływać się do nich z innego projektu lub odwołać się do nich z innego zestawu.

## <a name="to-add-an-activity-from-within-your-current-project"></a>Aby dodać działanie z bieżącego projektu

1. Dodaj nowe niestandardowe działanie do bieżącego projektu przepływu pracy. Aby uzyskać więcej informacji na temat dodawania nowego niestandardowego działania do projektu, zobacz [How to: Add a New Item to a Workflow Project](../workflow-designer/how-to-add-a-new-item-to-a-workflow-project.md).

2. Dodaj logikę niestandardową do działania.

3. Skompiluj projekt. Jeśli kompilacja zakończyła się pomyślnie, zostanie wyświetlona nowa kategoria w **przyborniku** o nazwie " \<*project name*> " z niestandardowym działaniem zawartym w tej kategorii.

    > [!NOTE]
    > Jeśli Przybornik zostanie zresetowany, działania niestandardowe zostaną usunięte, nawet jeśli rozwiązanie zostanie skompilowane ponownie. Aby ponownie wypełnić Przybornik z działaniami niestandardowymi po jego zresetowaniu, uruchom program Visual Studio.

    > [!NOTE]
    > W przyborniku można wyświetlić tylko jedno działanie o danej nazwie. Jeśli dwie działania z różnych zestawów mają tę samą nazwę klasy, zostanie wyświetlona tylko jedna z nich.

    > [!NOTE]
    > Domena aplikacji jest współdzielona między wystąpieniami edytora; Jeśli zmienne statyczne są używane, będą również współużytkowane przez wystąpienia edytora. Jeśli nie jest to wymagane zachowanie, usługa powinna być używana do śledzenia wystąpień zmiennych. Informacje dotyczące korzystania z usług w projektancie można znaleźć w temacie [using the ModelItem Editing Context](/dotnet/framework/windows-workflow-foundation/using-the-modelitem-editing-context) .

## <a name="to-add-an-activity-from-within-a-different-project"></a>Aby dodać działanie z w innym projekcie

1. Otwórz rozwiązanie, które zawiera co najmniej jeden projekt przepływu pracy i niestandardowy projekt biblioteki działań lub inny projekt przepływu pracy, który definiuje działanie niestandardowe.

2. Kompiluj oba projekty. Jeśli kompilacja zakończyła się pomyślnie, zostanie wyświetlona nowa kategoria w **przyborniku** o nazwie " \<*project name*> " z niestandardowym działaniem zawartym w tej kategorii.

## <a name="to-add-an-activity-to-the-toolbox-from-an-assembly"></a>Aby dodać działanie do przybornika z zestawu

1. Otwórz rozwiązanie przepływu pracy.

2. W menu **Narzędzia** wybierz pozycję **Wybierz elementy przybornika**.

3. W oknie dialogowym **Wybierz elementy przybornika** wybierz kartę **składniki system. działania** , a następnie kliknij przycisk **Przeglądaj** , aby przejść do zestawu zawierającego niestandardowe działanie, które chcesz dodać.

4. Wybierz zestaw, a następnie kliknij przycisk **OK**. Niestandardowy składnik działania jest dodawany do listy składników i jest wybierany automatycznie.

    1. Kliknij przycisk **OK** , aby zamknąć okno dialogowe.

5. Aby wyświetlić przybornik, wybierz pozycję **Przybornik** z menu **Widok** .

6. Działanie niestandardowe pojawia się w **przyborniku** w kategorii, która była skoncentrowana przed dodaniem elementu. Na przykład jeśli Kategoria **Ogólne** została wybrana w **przyborniku** przed dodaniem elementu przybornika, działanie zostanie wyświetlone w kategorii **Ogólne** .

## <a name="see-also"></a>Zobacz także

- [Używanie projektanta przepływu pracy](developing-applications-with-the-workflow-designer.md)
