---
title: 'Instrukcje: Tworzenie i edytowanie konfiguracji'
ms.date: 06/21/2017
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- solution build configurations, editing
- build configurations, creating
- solution build configurations, creating
- build configurations, editing
- builds [Visual Studio], setting up
- property pages
- Configuration Manager
- project build configurations, creating
- project build configurations, editing
ms.assetid: 19be121c-148e-4ece-bbfc-d20b08cfc3f7
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bb47a1b136f4f1e584b9b1b6f99fde7008ecc902
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595296"
---
# <a name="how-to-create-and-edit-configurations"></a>Instrukcje: Tworzenie i edytowanie konfiguracji

Można utworzyć kilka konfiguracji kompilacji dla rozwiązania. Można na przykład skonfigurować kompilację debugowania, która może być używana przez testerów do znajdowania i rozwiązywania problemów, a także skonfigurować różne rodzaje kompilacji, które można dystrybuować do różnych klientów.

> [!NOTE]
> Ten temat dotyczy programu Visual Studio w Windows. Aby uzyskać Visual Studio dla komputerów Mac, zobacz [Tworzenie i edytowanie konfiguracji w Visual Studio dla komputerów Mac](/visualstudio/mac/create-and-edit-configurations).

## <a name="create-build-configurations"></a>Utwórz konfiguracje kompilacji

Można użyć okna dialogowego **Configuration Manager** , aby wybrać lub zmodyfikować istniejące konfiguracje kompilacji lub utworzyć nowe.

Aby otworzyć okno dialogowe **Configuration Manager** , w **Eksplorator rozwiązań**Otwórz menu skrótów dla rozwiązania, a następnie wybierz **Configuration Manager**.

> [!NOTE]
> Jeśli polecenie **Configuration Manager** nie pojawia się w menu skrótów, poszukaj w menu **kompilacja** na pasku menu. Jeśli nie pojawia się na pasku menu, wybierz pozycję **narzędzia** > **Opcje**, a następnie w lewym okienku okna dialogowego **Opcje** rozwiń węzeł **projekty i rozwiązania** > **Ogólne**, a następnie w okienku po prawej stronie zaznacz pole wyboru **Pokaż zaawansowane konfiguracje kompilacji** .

W oknie dialogowym **Configuration Manager** można użyć listy rozwijanej **aktywna Konfiguracja rozwiązania** , aby wybrać konfigurację kompilacji obejmującą całe rozwiązanie, zmodyfikować istniejącą lub utworzyć nową konfigurację. Możesz użyć listy rozwijanej **Active Solution platform** , aby wybrać platformę, do której należy konfiguracja, zmodyfikować istniejącą lub dodać nową platformę. W okienku **konteksty projektu** wyświetlane są projekty w rozwiązaniu. Dla każdego projektu można wybrać konfigurację i platformę specyficzną dla projektu, zmodyfikować istniejące lub utworzyć nową konfigurację lub dodać nową platformę. Możesz również zaznaczyć pola wyboru wskazujące, czy każdy projekt jest uwzględniany w przypadku używania konfiguracji całego rozwiązania do kompilowania lub wdrażania rozwiązania.

Po skonfigurowaniu żądanych konfiguracji można ustawić właściwości projektu, które są odpowiednie dla tych konfiguracji.

### <a name="set-properties-based-on-configurations"></a>Ustawianie właściwości na podstawie konfiguracji

Aby ustawić właściwości na podstawie konfiguracji, w **Eksplorator rozwiązań**Otwórz menu skrótów dla projektu, a następnie wybierz **Właściwości**. Można ustawić właściwości dla konfiguracji. Na przykład w przypadku konfiguracji wydania można określić, że kod jest zoptymalizowany, gdy rozwiązanie jest skompilowane, a w przypadku konfiguracji debugowania można określić, że `DEBUG` symbol kompilacji warunkowej jest włączony.

Aby uzyskać więcej informacji na temat ustawień strony właściwości, zobacz [Zarządzanie właściwościami projektu i rozwiązania](../ide/managing-project-and-solution-properties.md).

## <a name="create-a-project-configuration"></a>Utwórz konfigurację projektu

1. Otwórz okno dialogowe **Configuration Manager** .

2. Wybierz projekt w kolumnie **projekt** .

3. Na liście rozwijanej **Konfiguracja** dla tego projektu wybierz pozycję **Nowy**.

     Zostanie otwarte okno dialogowe **Nowa konfiguracja projektu** .

4. W polu **Nazwa** wprowadź nazwę nowej konfiguracji.

5. Aby użyć ustawień właściwości z istniejącej konfiguracji projektu, na liście rozwijanej **Kopiuj ustawienia z** wybierz konfigurację.

6. Aby utworzyć konfigurację całego rozwiązania w tym samym czasie, zaznacz pole wyboru **Utwórz nową konfigurację rozwiązania** .

## <a name="rename-a-project-configuration"></a>Zmień nazwę konfiguracji projektu

1. Otwórz okno dialogowe **Configuration Manager** .

2. W kolumnie **projekt** wybierz projekt, który ma konfigurację projektu, której nazwę chcesz zmienić.

3. Na liście rozwijanej **Konfiguracja** dla tego projektu wybierz pozycję **Edytuj**.

     **Edytuj konfiguracje projektu** zostanie otwarte okno dialogowe.

4. Wybierz nazwę konfiguracji projektu, którą chcesz zmienić.

5. Wybierz pozycję **Zmień nazwę**, a następnie wprowadź nową nazwę.

## <a name="create-and-modify-solution-wide-build-configurations"></a>Tworzenie i modyfikowanie konfiguracji kompilacji dla całego rozwiązania

### <a name="to-create-a-solution-wide-build-configuration"></a>Aby utworzyć konfigurację kompilacji obejmującą wiele rozwiązań

1. Otwórz okno dialogowe **Configuration Manager** .

2. Z listy rozwijanej **aktywna Konfiguracja rozwiązania** wybierz pozycję **Nowy**.

     Zostanie otwarte okno dialogowe **Nowa konfiguracja rozwiązania** .

3. W polu tekstowym **Nazwa** wprowadź nazwę nowej konfiguracji.

4. Aby użyć ustawień z istniejącej konfiguracji rozwiązania, na liście rozwijanej **Kopiuj ustawienia z** wybierz konfigurację.

5. Jeśli chcesz utworzyć konfiguracje projektu w tym samym czasie, zaznacz pole wyboru **Utwórz nowe konfiguracje projektu** .

### <a name="to-rename-a-solution-wide-build-configuration"></a>Aby zmienić nazwę konfiguracji kompilacji dla całego rozwiązania

1. Otwórz okno dialogowe **Configuration Manager** .

2. Z listy rozwijanej **aktywna Konfiguracja rozwiązania** wybierz pozycję **Edytuj**.

     **Edytuj konfiguracje rozwiązania** zostanie otwarte okno dialogowe.

3. Wybierz nazwę konfiguracji rozwiązania, którą chcesz zmienić.

4. Wybierz pozycję **Zmień nazwę**, a następnie wprowadź nową nazwę.

### <a name="to-modify-a-solution-wide-build-configuration"></a>Aby zmodyfikować konfigurację kompilacji dla całego rozwiązania

1. Otwórz okno dialogowe **Configuration Manager** .

2. Z listy rozwijanej **aktywna Konfiguracja rozwiązania** wybierz żądaną konfigurację.

3. W okienku **konteksty projektu** dla każdego projektu wybierz żądaną **konfigurację** i **platformę** , a następnie wybierz, czy chcesz ją **skompilować** i czy **wdrożyć** .

## <a name="see-also"></a>Zobacz także

- [O konfiguracjach kompilacji](../ide/understanding-build-configurations.md)
- [Twórz i czyść projekty i rozwiązania w programie Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
- [Zarządzanie właściwościami projektów i rozwiązań](managing-project-and-solution-properties.md)
- [Tworzenie i edytowanie konfiguracji (Visual Studio dla komputerów Mac)](/visualstudio/mac/create-and-edit-configurations)
