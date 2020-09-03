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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "77904168"
---
# <a name="understand-build-configurations"></a>Opis konfiguracji kompilacji

Konfiguracje kompilacji muszą być potrzebne do kompilowania projektów przy użyciu różnych ustawień. Na przykład **debugowanie** i **wydanie** to konfiguracje i różne opcje kompilatora są używane odpowiednio podczas kompilowania.  Jedna konfiguracja jest aktywna i jest wskazywana na pasku poleceń u góry IDE.

![Aktywna konfiguracja](media/understanding-build-configurations/active-config.png)

> [!NOTE]
> Ten temat ma zastosowanie do programu Visual Studio w systemie Windows. Aby uzyskać Visual Studio dla komputerów Mac, zobacz [Konfiguracje kompilacji w programie Visual Studio dla komputerów Mac](/visualstudio/mac/configurations).

Konfiguracja i sterowanie platformą, w której są przechowywane skompilowane pliki wyjściowe. Zwykle, gdy program Visual Studio kompiluje projekt, dane wyjściowe są umieszczane w podfolderze projektu o nazwie z aktywną konfiguracją (na przykład *bin/debug/x86*), ale można to zmienić.

Możesz tworzyć własne konfiguracje kompilacji na poziomie rozwiązania i projektu. Konfiguracja rozwiązania określa, które projekty są uwzględniane w kompilacji, gdy ta konfiguracja jest aktywna. Zostaną skompilowane tylko projekty określone w aktywnej konfiguracji rozwiązania. Jeśli w Configuration Manager wybrano wiele platform docelowych, tworzone są wszystkie projekty, które są stosowane do danej platformy. Konfiguracja projektu określa, jakie ustawienia kompilacji i opcje kompilatora są używane podczas kompilowania projektu.

Aby utworzyć, wybrać, zmodyfikować lub usunąć konfigurację, można użyć **Configuration Manager**. Aby go otworzyć, na pasku menu wybierz opcję **Kompiluj**  >  **Configuration Manager**lub po prostu wpisz **konfigurację** w polu wyszukiwania. Możesz również użyć listy **konfiguracje rozwiązania** na pasku narzędzi **Standardowy** , aby wybrać konfigurację lub otworzyć **Configuration Manager**.

![Configuration Manager](media/understanding-build-configurations/config-manager.png)

> [!NOTE]
> Jeśli nie możesz znaleźć ustawień konfiguracji rozwiązania na pasku narzędzi i nie można uzyskać dostępu do **Configuration Manager**, można [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] zastosować ustawienia tworzenia. Aby uzyskać więcej informacji, zobacz [How to: Manage Configurations with Visual Basic Settings Developer](../ide/how-to-manage-build-configurations-with-visual-basic-developer-settings-applied.md).

Domyślnie konfiguracje **debugowania** i wydawania są zawarte w **projektach, które** są tworzone za pomocą [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] szablonów. Konfiguracja **debugowania** obsługuje debugowanie aplikacji, a konfiguracja **wydania** kompiluje wersję aplikacji, którą można wdrożyć. Aby uzyskać więcej informacji, zobacz [How to: Set Debug and Release Configurations](../debugger/how-to-set-debug-and-release-configurations.md). Można również tworzyć niestandardowe konfiguracje rozwiązań i konfiguracje projektu. Aby uzyskać więcej informacji, zobacz [How to: Create and Edit Configurations](../ide/how-to-create-and-edit-configurations.md).

## <a name="solution-configurations"></a>Konfiguracje rozwiązania

Konfiguracja rozwiązania określa sposób kompilowania i wdrażania projektów w rozwiązaniu. Aby zmodyfikować konfigurację rozwiązania lub zdefiniować nową, w **Configuration Manager**w obszarze **Konfiguracja aktywnego rozwiązania**wybierz pozycję **Edytuj** lub **Nowy**.

Każdy wpis w polu **konteksty projektu** w konfiguracji rozwiązania reprezentuje projekt w rozwiązaniu. Dla każdej kombinacji **aktywnej konfiguracji rozwiązania** i **aktywnej platformy rozwiązania**można ustawić, jak każdy projekt jest używany. (Aby uzyskać więcej informacji na temat platform rozwiązań, zobacz [Omówienie platform kompilacji](../ide/understanding-build-platforms.md)).

Podczas definiowania nowej konfiguracji rozwiązania i zaznacz pole wyboru **Utwórz nowe konfiguracje projektu** , program [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] automatycznie przypisze nową konfigurację do wszystkich projektów. Podobnie podczas definiowania nowej platformy rozwiązań i zaznacz pole wyboru **Utwórz nowe platformy projektu** , program [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] automatycznie przypisze nową platformę do wszystkich projektów. Ponadto, jeśli dodasz projekt, który jest przeznaczony dla nowej platformy, program Visual Studio doda tę platformę do listy platform rozwiązań i przypisze ją do wszystkich projektów. Można nadal modyfikować ustawienia dla każdego projektu.

Aktywna Konfiguracja rozwiązania zapewnia również kontekst dla środowiska IDE. Na przykład jeśli pracujesz nad projektem i konfiguracja określa, że zostanie on skompilowany dla urządzenia przenośnego, w **przyborniku** zostaną wyświetlone tylko elementy, które mogą być używane w projekcie urządzenia przenośnego.

## <a name="project-configurations"></a>Konfiguracje projektu

Konfiguracja i platforma, do których elementy docelowe projektu są używane razem, do określania ustawień kompilacji i opcji kompilatora, które mają być używane podczas kompilowania. Projekt może mieć różne ustawienia dla każdej kombinacji konfiguracji i platformy. Aby zmodyfikować właściwości projektu, otwórz menu skrótów dla projektu w **Eksplorator rozwiązań**, a następnie wybierz **Właściwości**.  W górnej części karty **kompilacja** projektanta projektu wybierz aktywną konfigurację, aby edytować jej ustawienia kompilacji.

![Konfiguracje projektanta projektu](media/understanding-build-configurations/project-designer-configuration.png)

## <a name="building-multiple-configurations"></a>Kompilowanie wielu konfiguracji

W przypadku kompilowania rozwiązania przy użyciu polecenia **Kompiluj**  >  **kompilację rozwiązania** program Visual Studio kompiluje tylko aktywną konfigurację. Wszystkie projekty, które są określone w tej konfiguracji rozwiązania, są kompilowane i jedyną utworzoną konfiguracją projektu jest ta, która jest określona w aktywnej konfiguracji rozwiązania i aktywnej platformie rozwiązania, która jest wyświetlana na pasku narzędzi w programie Visual Studio. Na przykład **debugowanie** i **x86**. Inne zdefiniowane konfiguracje i platformy nie są kompilowane.

Jeśli chcesz skompilować wiele konfiguracji i platform w jednej akcji, możesz użyć opcji **Kompiluj**  >  **kompilację wsadową** w programie Visual Studio. Aby uzyskać dostęp do tej funkcji, naciśnij klawisz **Ctrl** + **Q** , aby otworzyć pole wyszukiwania, a następnie wprowadź ciąg `Batch build` . Kompilacja wsadowa nie jest dostępna dla wszystkich typów projektów. Zobacz [jak: kompilowanie wielu konfiguracji jednocześnie](how-to-build-multiple-configurations-simultaneously.md).

## <a name="how-visual-studio-assigns-project-configurations"></a>Jak program Visual Studio przypisuje konfiguracje projektu

Podczas definiowania nowej konfiguracji rozwiązania i kopiowania ustawień z istniejącej usługi program Visual Studio używa następujących kryteriów do przypisywania domyślnych konfiguracji projektu. Kryteria są oceniane w podanej kolejności.

1. Jeśli projekt ma nazwę konfiguracji (* \<configuration name> \<platform name> *), która dokładnie odpowiada nazwie nowej konfiguracji rozwiązania, ta konfiguracja zostanie przypisana. W nazwach konfiguracji nie jest rozróżniana wielkość liter.

1. Jeśli projekt ma nazwę konfiguracji, w której część nazwy konfiguracji jest zgodna z nową konfiguracją rozwiązania, ta konfiguracja jest przypisana, niezależnie od tego, czy część platformy jest zgodna.

1. Jeśli nadal nie ma dopasowania, pierwsza konfiguracja wymieniona w projekcie jest przypisana.

## <a name="how-visual-studio-assigns-solution-configurations"></a>Jak program Visual Studio przypisuje konfiguracje rozwiązań

Podczas tworzenia konfiguracji projektu (w **Configuration Manager**, wybierając pozycję **Nowy** w menu rozwijanym w kolumnie **Konfiguracja** dla tego projektu) i zaznaczając pole wyboru **Utwórz nowe konfiguracje rozwiązania** , program Visual Studio szuka konfiguracji rozwiązania podobnej do skompilowania projektu na każdej platformie, którą obsługuje. W niektórych przypadkach program Visual Studio zmienia nazwy istniejących konfiguracji rozwiązania lub definiuje nowe.

Program Visual Studio używa następujących kryteriów do przypisywania konfiguracji rozwiązań.

- Jeśli konfiguracja projektu nie określa platformy lub określa tylko jedną platformę, wówczas zostanie znaleziona lub dodana konfiguracja rozwiązania, której nazwa jest zgodna z nową konfiguracją projektu. Domyślna nazwa tego rozwiązania nie zawiera nazwy platformy; formularz *\<project configuration name>* .

- Jeśli projekt obsługuje wiele platform, zostanie znaleziona lub dodana konfiguracja rozwiązania dla każdej z obsługiwanych platform. Nazwa każdej konfiguracji rozwiązania obejmuje zarówno nazwę konfiguracji projektu, jak i nazwę platformy i ma postać * \<project configuration name> \<platform name> *.

## <a name="see-also"></a>Zobacz też

- [Przewodnik: kompilowanie aplikacji](../ide/walkthrough-building-an-application.md)
- [Kompilowanie i tworzenie kompilacji](../ide/compiling-and-building-in-visual-studio.md)
- [Rozwiązania i projekty](../ide/solutions-and-projects-in-visual-studio.md)
- [Dokumentacja kompilacji C/C++](/cpp/build/reference/c-cpp-building-reference)
- [Informacje o platformach kompilacji](understanding-build-platforms.md)
- [Konfiguracje kompilacji (Visual Studio dla komputerów Mac)](/visualstudio/mac/configurations)
