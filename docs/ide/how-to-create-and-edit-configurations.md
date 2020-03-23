---
title: 'Jak: Tworzenie i edytowanie konfiguracji'
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 754d2ceef776ab0dea2d8d51151d4170839173b9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114703"
---
# <a name="how-to-create-and-edit-configurations"></a>Jak: Tworzenie i edytowanie konfiguracji

Można utworzyć kilka konfiguracji kompilacji dla rozwiązania. Na przykład można skonfigurować kompilacji debugowania, które testerów można użyć do znajdowania i rozwiązywania problemów i można skonfigurować różne rodzaje kompilacji, które można dystrybuować do różnych klientów.

> [!NOTE]
> W tym temacie stosuje się do programu Visual Studio w systemie Windows. W programie Visual Studio dla komputerów Mac zobacz [Tworzenie i edytowanie konfiguracji w programie Visual Studio dla komputerów Mac](/visualstudio/mac/create-and-edit-configurations).

## <a name="create-build-configurations"></a>Tworzenie konfiguracji kompilacji

Za pomocą okna dialogowego **Menedżer konfiguracji** można wybrać lub zmodyfikować istniejące konfiguracje kompilacji lub utworzyć nowe.

Aby otworzyć okno dialogowe **Menedżer konfiguracji,** w **Eksploratorze rozwiązań**otwórz menu skrótów dla rozwiązania, a następnie wybierz pozycję **Menedżer konfiguracji**.

> [!NOTE]
> Jeśli polecenie **Menedżer konfiguracji** nie pojawia się w menu skrótów, poszukaj w menu **Kompilacji** na pasku menu. Jeśli tam też nie jest wyświetlany, na pasku menu wybierz pozycję**Opcje** **narzędzi** > , a następnie w lewym okienku okna dialogowego **Opcje** rozwiń rozwiń pozycję Ogólne projekty **i rozwiązania** > **,** a następnie w prawym okienku zaznacz pole wyboru Pokaż zaawansowane **konfiguracje kompilacji.**

W oknie dialogowym **Menedżer konfiguracji** można użyć listy rozwijanej **Konfiguracja rozwiązania Active,** aby wybrać konfigurację kompilacji dla całego rozwiązania, zmodyfikować istniejącą lub utworzyć nową konfigurację. Można użyć listy rozwijanej **platformy aktywnego rozwiązania,** aby wybrać platformę, na której docelowych konfiguracji, zmodyfikować istniejącą lub dodać nową platformę. **Konteksty projektu** okienka wyświetla listę projektów w rozwiązaniu. Dla każdego projektu można wybrać konfigurację i platformę specyficzną dla projektu, zmodyfikować istniejące lub utworzyć nową konfigurację lub dodać nową platformę. Można również zaznaczyć pola wyboru, które wskazują, czy każdy projekt jest uwzględniony podczas tworzenia lub wdrażania rozwiązania za pomocą konfiguracji dla całego rozwiązania.

Po skonfigurowaniu żądanych konfiguracji można ustawić właściwości projektu, które są odpowiednie dla tych konfiguracji.

### <a name="set-properties-based-on-configurations"></a>Ustawianie właściwości na podstawie konfiguracji

Aby ustawić właściwości na podstawie konfiguracji, w **Eksploratorze rozwiązań**otwórz menu **skrótów**dla projektu, a następnie wybierz polecenie Właściwości . Można ustawić właściwości dla konfiguracji. Na przykład dla konfiguracji wersji można określić, że kod jest zoptymalizowany podczas tworzenia rozwiązania, a `DEBUG` dla konfiguracji debugowania można określić, że symbol kompilacji warunkowej jest uwzględniony.

Aby uzyskać więcej informacji na temat ustawień strony właściwości, zobacz [Zarządzanie właściwościami projektu i rozwiązania](../ide/managing-project-and-solution-properties.md).

## <a name="create-a-project-configuration"></a>Tworzenie konfiguracji projektu

1. Otwórz okno **dialogowe Menedżer konfiguracji.**

2. Wybierz projekt w kolumnie **Projekt.**

3. Z listy rozwijanej **Konfiguracja** dla tego projektu wybierz pozycję **Nowy**.

     Zostanie otwarte okno dialogowe **Nowa konfiguracja projektu.**

4. W polu **Nazwa** wprowadź nazwę nowej konfiguracji.

5. Aby użyć ustawień właściwości z istniejącej konfiguracji projektu, z listy rozwijanej **Kopiuj ustawienia z** wybierz konfigurację.

6. Aby jednocześnie utworzyć konfigurację dla całego rozwiązania, zaznacz pole wyboru **Utwórz nową konfigurację rozwiązania.**

## <a name="rename-a-project-configuration"></a>Zmienianie nazwy konfiguracji projektu

1. Otwórz okno **dialogowe Menedżer konfiguracji.**

2. W **project** kolumny wybierz projekt, który ma konfigurację projektu, którego nazwę chcesz zmienić.

3. Z listy rozwijanej **Konfiguracja** dla tego projektu wybierz pozycję **Edytuj**.

     Zostanie otwarte okno dialogowe **Edytowanie konfiguracji projektu.**

4. Wybierz nazwę konfiguracji projektu, którą chcesz zmienić.

5. Wybierz **pozycję Zmień nazwę**, a następnie wprowadź nową nazwę.

## <a name="create-and-modify-solution-wide-build-configurations"></a>Tworzenie i modyfikowanie konfiguracji kompilacji dla całego rozwiązania

### <a name="to-create-a-solution-wide-build-configuration"></a>Aby utworzyć konfigurację kompilacji dla całego rozwiązania

1. Otwórz okno **dialogowe Menedżer konfiguracji.**

2. Z listy rozwijanej **Konfiguracja rozwiązania Active** wybierz pozycję **Nowy**.

     Zostanie otwarte okno dialogowe **Nowa konfiguracja rozwiązania.**

3. W polu tekstowym **Nazwa** wprowadź nazwę nowej konfiguracji.

4. Aby użyć ustawień z istniejącej konfiguracji rozwiązania, z listy rozwijanej **Kopiuj ustawienia z** wybierz konfigurację.

5. Jeśli chcesz jednocześnie tworzyć konfiguracje projektu, zaznacz pole wyboru **Utwórz nowe konfiguracje projektu.**

### <a name="to-rename-a-solution-wide-build-configuration"></a>Aby zmienić nazwę konfiguracji kompilacji dla całego rozwiązania

1. Otwórz okno **dialogowe Menedżer konfiguracji.**

2. Z listy rozwijanej **Konfiguracja rozwiązania Active** wybierz pozycję **Edytuj**.

     Zostanie otwarte okno dialogowe **Edytowanie konfiguracji rozwiązania.**

3. Wybierz nazwę konfiguracji rozwiązania, którą chcesz zmienić.

4. Wybierz **pozycję Zmień nazwę**, a następnie wprowadź nową nazwę.

### <a name="to-modify-a-solution-wide-build-configuration"></a>Aby zmodyfikować konfigurację kompilacji dla całego rozwiązania

1. Otwórz okno **dialogowe Menedżer konfiguracji.**

2. Z listy rozwijanej **Konfiguracja rozwiązania Active** wybierz odpowiednią konfigurację.

3. W okienku **Konteksty projektu** dla każdego projektu wybierz **konfigurację** i **platformę,** którą chcesz i wybierz, czy go **utworzyć** i czy go **wdrożyć.**

## <a name="see-also"></a>Zobacz też

- [Opis konfiguracji kompilacji](../ide/understanding-build-configurations.md)
- [Twórz i twórz projekty i rozwiązania w programie Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
- [Zarządzanie właściwościami projektów i rozwiązań](managing-project-and-solution-properties.md)
- [Tworzenie i edytowanie konfiguracji (Visual Studio dla komputerów Mac)](/visualstudio/mac/create-and-edit-configurations)
