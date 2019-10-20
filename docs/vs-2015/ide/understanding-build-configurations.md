---
title: Informacje o konfiguracjach kompilacji | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
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
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a7e7c184fd150c46b3a8be0ec583d4223487ad32
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672769"
---
# <a name="understanding-build-configurations"></a>Ogólne informacje o konfiguracjach kompilacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można przechowywać różne konfiguracje rozwiązań i właściwości projektu do użycia w różnych rodzajach kompilacji. Aby utworzyć, wybrać, zmodyfikować lub usunąć konfigurację, można użyć **Configuration Manager**. Aby go otworzyć, na pasku menu wybierz pozycję **kompilacja**, **Configuration Manager**lub po prostu wpisz **Konfiguracja** w polu **Szybkie uruchamianie** . Możesz również użyć listy **konfiguracje rozwiązania** na pasku narzędzi **Standardowy** , aby wybrać konfigurację lub otworzyć **Configuration Manager**.

> [!NOTE]
> Jeśli nie możesz znaleźć ustawień konfiguracji rozwiązania na pasku narzędzi i nie można uzyskać dostępu do **Configuration Manager**, [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] można zastosować ustawienia deweloperskie. Aby uzyskać więcej informacji, zobacz [How to: Manage Configurations with Visual Basic Settings Developer](../ide/how-to-manage-build-configurations-with-visual-basic-developer-settings-applied.md).

 Domyślnie konfiguracje debugowania i wydawania są zawarte w projektach, które są tworzone za pomocą szablonów [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Konfiguracja debugowania obsługuje debugowanie aplikacji, a konfiguracja wydania kompiluje wersję aplikacji, którą można wdrożyć. Aby uzyskać więcej informacji, zobacz [How to: Set Debug and Release Configurations](../debugger/how-to-set-debug-and-release-configurations.md). Można również tworzyć niestandardowe konfiguracje rozwiązań i konfiguracje projektu. Aby uzyskać więcej informacji, zobacz [How to: Create and Edit Configurations](../ide/how-to-create-and-edit-configurations.md).

## <a name="solution-configurations"></a>Konfiguracje rozwiązania
 Konfiguracja rozwiązania określa sposób kompilowania i wdrażania projektów w rozwiązaniu. Aby zmodyfikować konfigurację rozwiązania lub zdefiniować nową, w **Configuration Manager**w obszarze **Konfiguracja aktywnego rozwiązania**wybierz pozycję **Edytuj** lub **Nowy**.

 Każdy wpis w polu **konteksty projektu** w konfiguracji rozwiązania reprezentuje projekt w rozwiązaniu. Dla każdej kombinacji **aktywnej konfiguracji rozwiązania** i **aktywnej platformy rozwiązania**można ustawić, jak każdy projekt jest używany. (Aby uzyskać więcej informacji na temat platform rozwiązań, zobacz [Opis platform kompilacji](../ide/understanding-build-platforms.md)).

> [!NOTE]
> Podczas definiowania nowej konfiguracji rozwiązania i zaznacz pole wyboru **Utwórz nowe konfiguracje projektu** , [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] automatycznie przypisuje nową konfigurację do wszystkich projektów. Podobnie podczas definiowania nowej platformy rozwiązań i zaznacz pole wyboru **Utwórz nowe platformy projektu** , [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] automatycznie przypisze nową platformę do wszystkich projektów. Ponadto, jeśli dodasz projekt, który jest przeznaczony dla nowej platformy, program Visual Studio doda tę platformę do listy platform rozwiązań i przypisze ją do wszystkich projektów.
>
> Można nadal modyfikować ustawienia dla każdego projektu.

 Aktywna Konfiguracja rozwiązania zapewnia również kontekst dla środowiska IDE. Na przykład jeśli pracujesz nad projektem i konfiguracja określa, że zostanie on skompilowany dla urządzenia przenośnego, w **przyborniku** zostaną wyświetlone tylko elementy, które mogą być używane w projekcie urządzenia przenośnego.

## <a name="project-configurations"></a>Konfiguracje projektu
 Konfiguracja i platforma, do których elementy docelowe projektu są używane razem, aby określić właściwości, które mają być używane podczas kompilowania. Projekt może mieć inny zestaw definicji właściwości dla każdej kombinacji konfiguracji i platformy. Aby zmodyfikować właściwości projektu, można użyć jego stron właściwości. (W **Eksplorator rozwiązań**Otwórz menu skrótów dla projektu, a następnie wybierz polecenie **Właściwości**.)

 Dla każdej konfiguracji projektu, w razie potrzeby, można zdefiniować zależne od konfiguracji właściwości. Na przykład dla konkretnej kompilacji można określić, które elementy projektu zostaną uwzględnione i jakie pliki wyjściowe zostaną utworzone, gdzie zostaną umieszczone i jak zostaną one zoptymalizowane.

 Konfiguracje projektu mogą się różnić znacznie. Na przykład właściwości jednej konfiguracji mogą określać, że jej plik wyjściowy ma być zoptymalizowany pod kątem minimalnej ilości miejsca, podczas gdy inna konfiguracja może określać, że jej pliki wykonywalne są uruchamiane z maksymalną szybkością.

 Konfiguracje projektu są przechowywane przez rozwiązanie — nie przez użytkownika, tak aby mogły być współużytkowane przez zespół.

 Chociaż zależności projektu są niezależne od konfiguracji, zostaną skompilowane tylko projekty, które są określone w aktywnej konfiguracji rozwiązania.

## <a name="how-visual-studio-assigns-project-configurations"></a>Jak program Visual Studio przypisuje konfiguracje projektu
 Podczas definiowania nowej konfiguracji rozwiązania i kopiowania ustawień z istniejącej usługi program Visual Studio używa następujących kryteriów do przypisywania domyślnych konfiguracji projektu. Kryteria są oceniane w podanej kolejności.

1. Jeśli projekt ma nazwę konfiguracji ( *\<configuration nazwę > \<platform >* ), która dokładnie odpowiada nazwie nowej konfiguracji rozwiązania, ta konfiguracja zostanie przypisana. W nazwach konfiguracji nie jest rozróżniana wielkość liter.

2. Jeśli projekt ma nazwę konfiguracji, w której część nazwy konfiguracji jest zgodna z nową konfiguracją rozwiązania, ta konfiguracja jest przypisana, niezależnie od tego, czy część platformy jest zgodna.

3. Jeśli nadal nie ma dopasowania, pierwsza konfiguracja wymieniona w projekcie jest przypisana.

## <a name="how-visual-studio-assigns-solution-configurations"></a>Jak program Visual Studio przypisuje konfiguracje rozwiązań
 Podczas tworzenia konfiguracji projektu (w **Configuration Manager**, wybierając pozycję **Nowy** w menu rozwijanym w kolumnie **Konfiguracja** dla tego projektu), a następnie zaznacz pole wyboru **Utwórz nowe konfiguracje rozwiązania** , Wizualizacja Studio szuka konfiguracji rozwiązania podobnej do kompilacji, aby skompilować projekt na każdej platformie, którą obsługuje. W niektórych przypadkach program Visual Studio zmienia nazwy istniejących konfiguracji rozwiązania lub definiuje nowe.

 Program Visual Studio używa następujących kryteriów do przypisywania konfiguracji rozwiązań.

- Jeśli konfiguracja projektu nie określa platformy lub określa tylko jedną platformę, wówczas zostanie znaleziona lub dodana konfiguracja rozwiązania, której nazwa jest zgodna z nową konfiguracją projektu. Domyślna nazwa tego rozwiązania nie zawiera nazwy platformy; przyjmuje formularz *\<project nazwy konfiguracji >* .

- Jeśli projekt obsługuje wiele platform, zostanie znaleziona lub dodana konfiguracja rozwiązania dla każdej z obsługiwanych platform. Nazwa każdej konfiguracji rozwiązania obejmuje zarówno nazwę konfiguracji projektu, jak i nazwę platformy i ma postać *\<project nazwa konfiguracji > \<platform >* .

## <a name="see-also"></a>Zobacz też
 [Przewodnik: kompilowanie](../ide/walkthrough-building-an-application.md) [kompilowania aplikacji i](../ide/compiling-and-building-in-visual-studio.md) Kompilowanie [rozwiązań i projektów](../ide/solutions-and-projects-in-visual-studio.md) [C/C++ ](https://msdn.microsoft.com/library/100b4ccf-572c-4d1f-970c-fa0bc0cc0d2d) [devenv](../ide/reference/devenv-command-line-switches.md) Reference
