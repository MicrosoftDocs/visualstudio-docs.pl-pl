---
title: Opis konfiguracji kompilacji
ms.date: 01/20/2020
ms.technology: vs-ide-compile
ms.topic: conceptual
f1_keywords:
- SolutionProperties.ActiveConfig
- vs.build.newprojectconfiguration
- vc.proj.configurationsctrl.multipleconfigs
- vs.build.editsolutionconfigurations
- vs.build.editprojectconfigurations
- vs.multipleconfigurations
- vs.build.newsolutionconfiguration
- VS.ConfigurationManager
- VS.MultipleConfig
helpviewer_keywords:
- solution build configurations, about build configurations
- build configurations
- project build configurations
- build configurations, advanced
- projects [Visual Studio], build configuration
- solutions [Visual Studio], build configuration
ms.assetid: 934c727d-3a22-429c-bd13-3552cecf2e24
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a37d4fa5dc92253b94dc64590c9df5fec7703ceb
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77904168"
---
# <a name="understand-build-configurations"></a>Opis konfiguracji kompilacji

Musisz kompilacji konfiguracji, gdy trzeba tworzyć projekty z różnymi ustawieniami. Na przykład **debugowania** i **wydania** są konfiguracje i różne opcje kompilatora są używane odpowiednio podczas ich tworzenia.  Jedna konfiguracja jest aktywna i jest wskazywana na pasku poleceń w górnej części IDE.

![Aktywna konfiguracja](media/understanding-build-configurations/active-config.png)

> [!NOTE]
> W tym temacie stosuje się do programu Visual Studio w systemie Windows. W przypadku programu Visual Studio dla komputerów Mac zobacz [Tworzenie konfiguracji w programie Visual Studio dla komputerów Mac](/visualstudio/mac/configurations).

Konfiguracja i kontrola platformy, w której są przechowywane wbudowane pliki wyjściowe. Zwykle podczas tworzenia projektu w programie Visual Studio dane wyjściowe są umieszczane w podfolderze projektu o nazwie z aktywną konfiguracją (na przykład *bin/debug/x86),* ale można to zmienić.

Można utworzyć własne konfiguracje kompilacji na poziomie rozwiązania i projektu. Konfiguracja rozwiązania określa, które projekty są uwzględniane w kompilacji, gdy ta konfiguracja jest aktywna. Zostaną utworzone tylko projekty określone w konfiguracji aktywnego rozwiązania. Jeśli w programie Configuration Manager wybrano wiele platform docelowych, tworzone są wszystkie projekty, które mają zastosowanie do tej platformy. Konfiguracja projektu określa, jakie ustawienia kompilacji i opcje kompilatora są używane podczas tworzenia projektu.

Aby utworzyć, wybrać, zmodyfikować lub usunąć konfigurację, można użyć **programu Menedżer konfiguracji**. Aby go otworzyć, na pasku menu wybierz pozycję **Build** > **Configuration Manager**lub po prostu wpisz polecenie **Konfiguracja** w polu wyszukiwania. Można również użyć listy **Konfiguracje rozwiązań** na pasku narzędzi **Standardowy,** aby wybrać konfigurację lub otworzyć **menedżera konfiguracji**.

![Configuration Manager](media/understanding-build-configurations/config-manager.png)

> [!NOTE]
> Jeśli nie możesz znaleźć ustawień konfiguracji rozwiązania na pasku narzędzi i [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] nie możesz uzyskać dostępu do programu Menedżer **konfiguracji,** mogą zostać zastosowane ustawienia programistyczne. Aby uzyskać więcej informacji, zobacz [Jak: Zarządzanie konfiguracjami za pomocą zastosowanych ustawień dewelopera języka Visual Basic](../ide/how-to-manage-build-configurations-with-visual-basic-developer-settings-applied.md).

Domyślnie **debugowanie** i **release** konfiguracje są uwzględniane [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] w projektach, które są tworzone przy użyciu szablonów. Konfiguracja **debugowania** obsługuje debugowanie aplikacji, a **konfiguracja wydania** tworzy wersję aplikacji, którą można wdrożyć. Aby uzyskać więcej informacji, zobacz [Jak: Ustawianie konfiguracji debugowania i zwalniania](../debugger/how-to-set-debug-and-release-configurations.md). Można również tworzyć niestandardowe konfiguracje rozwiązań i konfiguracje projektu. Aby uzyskać więcej informacji, zobacz [Jak: Tworzenie i edytowanie konfiguracji](../ide/how-to-create-and-edit-configurations.md).

## <a name="solution-configurations"></a>Konfiguracje rozwiązań

Konfiguracja rozwiązania określa, jak projekty w rozwiązaniu mają być budowane i wdrażane. Aby zmodyfikować konfigurację rozwiązania lub zdefiniować nową, w **programie Menedżer konfiguracji**w obszarze **Konfiguracja rozwiązania active**wybierz pozycję **Edytuj** lub **Nowy**.

Każdy wpis w polu **Konteksty projektu** w konfiguracji rozwiązania reprezentuje projekt w rozwiązaniu. Dla każdej kombinacji **konfiguracji rozwiązania Active** i platformy rozwiązania **active**można ustawić sposób użycia każdego projektu. (Aby uzyskać więcej informacji na temat platform rozwiązań, zobacz [Zrozumieć platformy kompilacji](../ide/understanding-build-platforms.md).)

Po zdefiniowaniu nowej konfiguracji rozwiązania i zaznaczeniu pola [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wyboru **Utwórz nowe konfiguracje projektu,** automatycznie przypisujesz nową konfigurację do wszystkich projektów. Podobnie podczas definiowania nowej platformy rozwiązania i zaznaczania pola [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wyboru **Utwórz nowe platformy projektów,** automatycznie przypisuje nową platformę do wszystkich projektów. Ponadto jeśli dodasz projekt, który jest przeznaczony dla nowej platformy, Visual Studio dodaje tę platformę do listy platform rozwiązań i przypisuje ją do wszystkich projektów. Nadal można modyfikować ustawienia dla każdego projektu.

Konfiguracja aktywnego rozwiązania zapewnia również kontekst do IDE. Na przykład jeśli pracujesz nad projektem, a konfiguracja określa, że zostanie on utworzony dla urządzenia przenośnego, **przybornik** wyświetla tylko elementy, które mogą być używane w projekcie urządzenia przenośnego.

## <a name="project-configurations"></a>Konfiguracje projektu

Konfiguracja i platforma, które obiekty docelowe projektu są używane razem, aby określić ustawienia kompilacji i opcje kompilatora do użycia podczas jego tworzenia. Projekt może mieć różne ustawienia dla każdej kombinacji konfiguracji i platformy. Aby zmodyfikować właściwości projektu, otwórz menu skrótów dla projektu w **Eksploratorze rozwiązań,** a następnie wybierz polecenie **Właściwości**.  W górnej części karty **Kompilacja** projektanta projektu wybierz aktywną konfigurację, aby edytować jego ustawienia kompilacji.

![Konfiguracje projektanta projektów](media/understanding-build-configurations/project-designer-configuration.png)

## <a name="building-multiple-configurations"></a>Tworzenie wielu konfiguracji

Podczas tworzenia rozwiązania przy użyciu polecenia **Kompilacja** > **rozwiązania,** Visual Studio tworzy tylko aktywną konfigurację. Wszystkie projekty, które są określone w tej konfiguracji rozwiązania są tworzone, a tylko konfiguracja projektu, który jest zbudowany jest określony w konfiguracji aktywnego rozwiązania i platformy aktywnego rozwiązania, który jest wyświetlany na pasku narzędzi w programie Visual Studio. Na przykład **Debug** i **x86**. Inne zdefiniowane konfiguracje i platformy nie są budowane.

Jeśli chcesz utworzyć wiele konfiguracji i platform w jednej akcji, można użyć opcji**kompilacji wsadowej** **kompilacji w** > programie Visual Studio. Aby uzyskać dostęp do tej funkcji, naciśnij klawisz `Batch build` **Ctrl**+**Q,** aby otworzyć pole wyszukiwania, a następnie wprowadź . Kompilacja wsadowy nie jest dostępna dla wszystkich typów projektów. Zobacz [Jak: Tworzenie wielu konfiguracji jednocześnie](how-to-build-multiple-configurations-simultaneously.md).

## <a name="how-visual-studio-assigns-project-configurations"></a>Jak program Visual Studio przypisuje konfiguracje projektu

Podczas definiowania nowej konfiguracji rozwiązania i nie kopiować ustawienia z istniejącego, Visual Studio używa następujących kryteriów, aby przypisać domyślne konfiguracje projektu. Kryteria są oceniane w podanej kolejności.

1. Jeśli projekt ma nazwę konfiguracji*\<(nazwa konfiguracji \<> nazwa platformy>*), która dokładnie odpowiada nazwie nowej konfiguracji rozwiązania, ta konfiguracja jest przypisana. W nazwach konfiguracji nie rozróżniana jest wielkość liter.

1. Jeśli projekt ma nazwę konfiguracji, w której część nazwa konfiguracji pasuje do nowej konfiguracji rozwiązania, ta konfiguracja jest przypisana, czy część platformy jest zgodna, czy nie.

1. Jeśli nadal nie ma dopasowania, przypisana jest pierwsza konfiguracja wymieniona w projekcie.

## <a name="how-visual-studio-assigns-solution-configurations"></a>Jak program Visual Studio przypisuje konfiguracje rozwiązań

Podczas tworzenia konfiguracji projektu (w **menedżerze konfiguracji**, wybierając **pozycję Nowy** w menu rozwijanym w **kolumnie Konfiguracja** dla tego projektu) i zaznacz pole wyboru **Utwórz nowe konfiguracje rozwiązań,** program Visual Studio szuka konfiguracji rozwiązania o podobnej nazwie do tworzenia projektu na każdej platformie, którą obsługuje. W niektórych przypadkach visual studio zmienia nazwę istniejących konfiguracji rozwiązania lub definiuje nowe.

Visual Studio używa następujących kryteriów do przypisywania konfiguracji rozwiązania.

- Jeśli konfiguracja projektu nie określa platformy lub określa tylko jedną platformę, zostanie znaleziona lub dodana konfiguracja rozwiązania, której nazwa odpowiada nazwie nowej konfiguracji projektu. Domyślna nazwa tej konfiguracji rozwiązania nie zawiera nazwy platformy; przyjmuje nazwę * \<konfiguracji projektu *formularza>.

- Jeśli projekt obsługuje wiele platform, konfiguracja rozwiązania jest znajdowana lub dodawana dla każdej obsługiwanej platformy. Nazwa każdej konfiguracji rozwiązania zawiera zarówno nazwę konfiguracji projektu, jak i nazwę platformy i ma * \<nazwę konfiguracji projektu \< *formularza> nazwę platformy>.

## <a name="see-also"></a>Zobacz też

- [Przewodnik: kompilowanie aplikacji](../ide/walkthrough-building-an-application.md)
- [Kompilowanie i tworzenie kompilacji](../ide/compiling-and-building-in-visual-studio.md)
- [Rozwiązania i projekty](../ide/solutions-and-projects-in-visual-studio.md)
- [Dokumentacja kompilacji C/C++](/cpp/build/reference/c-cpp-building-reference)
- [Opis platform kompilacji](understanding-build-platforms.md)
- [Konfiguracje kompilacji (Visual Studio dla komputerów Mac)](/visualstudio/mac/configurations)
