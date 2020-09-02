---
title: 'Instrukcje: dodawanie działań do przybornika | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: b3a8a785-5928-457a-8a50-30267e29503d
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8fc2af704ab587480913c51cdbc593e6cc0f483a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663466"
---
# <a name="how-to-add-activities-to-the-toolbox"></a>Instrukcje: Dodawanie działań do przybornika
Działania można dodawać do **przybornika** w rozwiązaniu na kilka różnych sposobów. Można je dodać z poziomu bieżącego projektu, odwoływać się do nich z innego projektu lub odwołać się do nich z innego zestawu.

### <a name="to-add-an-activity-from-within-your-current-project"></a>Aby dodać działanie z bieżącego projektu

1. Dodaj nowe niestandardowe działanie do bieżącego projektu przepływu pracy. [!INCLUDE[crabout](../includes/crabout-md.md)] Dodawanie nowego niestandardowego działania do projektu, zobacz [jak: Dodawanie nowego elementu do projektu przepływu pracy](../workflow-designer/how-to-add-a-new-item-to-a-workflow-project.md).

2. Dodaj logikę niestandardową do działania.

3. Skompiluj projekt. Jeśli kompilacja zakończyła się pomyślnie, zostanie wyświetlona nowa kategoria w **przyborniku** o nazwie " \<*project name*> " z niestandardowym działaniem zawartym w tej kategorii.

    > [!NOTE]
    > Jeśli Przybornik zostanie zresetowany, działania niestandardowe zostaną usunięte, nawet jeśli rozwiązanie zostanie skompilowane ponownie. Aby ponownie wypełnić Przybornik z działaniami niestandardowymi po jego zresetowaniu, należy uruchomić polecenie restart [!INCLUDE[vs2010](../includes/vs2010-md.md)] .

    > [!NOTE]
    > W przyborniku można wyświetlić tylko jedno działanie o danej nazwie. Jeśli dwie działania z różnych zestawów mają tę samą nazwę klasy, zostanie wyświetlona tylko jedna z nich.

    > [!NOTE]
    > Domena aplikacji jest współdzielona między wystąpieniami edytora; Jeśli zmienne statyczne są używane, będą również współużytkowane przez wystąpienia edytora. Jeśli nie jest to wymagane zachowanie, usługa powinna być używana do śledzenia wystąpień zmiennych. Informacje dotyczące korzystania z usług w projektancie można znaleźć w temacie [using the ModelItem Editing Context](https://msdn.microsoft.com/library/7f9f1ea5-0147-4079-8eca-be94f00d3aa1) .

### <a name="to-add-an-activity-from-within-a-different-project"></a>Aby dodać działanie z w innym projekcie

1. Otwórz rozwiązanie, które zawiera co najmniej jeden projekt przepływu pracy i niestandardowy projekt biblioteki działań lub inny projekt przepływu pracy, który definiuje działanie niestandardowe.

2. Kompiluj oba projekty. Jeśli kompilacja zakończyła się pomyślnie, zostanie wyświetlona nowa kategoria w **przyborniku** o nazwie " \<*project name*> " z niestandardowym działaniem zawartym w tej kategorii.

### <a name="to-add-an-activity-to-the-toolbox-from-an-assembly"></a>Aby dodać działanie do przybornika z zestawu

1. Otwórz rozwiązanie przepływu pracy.

2. W menu **Narzędzia** wybierz pozycję **Wybierz elementy przybornika.**...

3. W oknie dialogowym **Wybierz elementy przybornika** wybierz kartę **składniki system. działania** , a następnie kliknij przycisk **Przeglądaj...** , aby przejść do zestawu, który zawiera niestandardowe działanie, które chcesz dodać.

4. Wybierz zestaw, a następnie kliknij przycisk **OK**. Niestandardowy składnik działania jest dodawany do listy składników i jest wybierany automatycznie.

    1. Kliknij przycisk **OK** , aby zamknąć okno dialogowe.

5. Aby wyświetlić przybornik, wybierz pozycję **Przybornik** z menu **Widok** .

6. Działanie niestandardowe pojawia się w **przyborniku** w kategorii, która była skoncentrowana przed dodaniem elementu. Na przykład jeśli Kategoria **Ogólne** została wybrana w **przyborniku** przed dodaniem elementu przybornika, działanie zostanie wyświetlone w kategorii **Ogólne** .

## <a name="see-also"></a>Zobacz też
 [Używanie projektanta przepływu pracy](../workflow-designer/using-the-workflow-designer.md)