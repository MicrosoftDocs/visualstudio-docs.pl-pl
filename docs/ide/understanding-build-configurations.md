---
title: O konfiguracjach kompilacji
ms.date: 11/04/2016
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 15de24a35e410bec38e5b70813285440aaa05de4
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55914974"
---
# <a name="understand-build-configurations"></a>O konfiguracjach kompilacji

Można przechowywać różne konfiguracje rozwiązania i projektu właściwości mają zostać użyte w różne rodzaje kompilacji. Tworzenie, wybierz, zmodyfikować lub usunąć konfigurację, można użyć **programu Configuration Manager**. Aby otworzyć go na pasku menu, wybierz **kompilacji** > **programu Configuration Manager**, lub po prostu wpisz **konfiguracji** w **Szybkie uruchamianie**pole. Można również użyć **konfiguracje rozwiązania** listy na **standardowa** narzędzi, aby wybrać konfigurację, lub otworzyć **programu Configuration Manager**.

> [!NOTE]
> Ten temat dotyczy programu Visual Studio w Windows. Dla programu Visual Studio dla komputerów Mac, zobacz [kompilowanie konfiguracji w programie Visual Studio dla komputerów Mac](/visualstudio/mac/configurations).

> [!NOTE]
> Jeśli nie można znaleźć rozwiązania ustawień konfiguracji na pasku narzędzi, a nie ma dostępu do **programu Configuration Manager**, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] mogą być stosowane ustawienia środowiska deweloperskiego. Aby uzyskać więcej informacji, zobacz [jak: Zarządzanie konfiguracjami z zastosowaniem ustawień dewelopera Visual Basic](../ide/how-to-manage-build-configurations-with-visual-basic-developer-settings-applied.md).

Domyślnie, debugowania i konfiguracje wydania znajdują się w projektach, które są tworzone za pomocą [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] szablonów. Konfiguracja debugowania obsługuje debugowanie aplikacji, a konfiguracja wydania tworzy wersję aplikacji, które można wdrożyć. Aby uzyskać więcej informacji, zobacz [jak: Zestaw debugowania i zwalniania konfiguracji](../debugger/how-to-set-debug-and-release-configurations.md). Można również utworzyć niestandardowe rozwiązanie konfiguracji i konfiguracje projektu. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie i edytowanie konfiguracji](../ide/how-to-create-and-edit-configurations.md).

## <a name="solution-configurations"></a>Konfiguracje rozwiązania

Konfiguracja rozwiązania określa, jak projekty w rozwiązaniu są kompilowane i wdrażane. Do modyfikowania konfiguracji rozwiązania lub zdefiniuj nowe, w **programu Configuration Manager**w obszarze **Konfiguracja rozwiązania aktywnego**, wybierz **Edytuj** lub **New** .

Każdy wpis **projektu kontekstów** pole w konfiguracji rozwiązania reprezentuje projektu w rozwiązaniu. Dla każdej kombinacji **Konfiguracja rozwiązania aktywnego** i **aktywną platformą rozwiązania**, można ustawić sposób użycia każdego projektu. (Aby uzyskać więcej informacji na temat platformy rozwiązania, zobacz [omówienie platformy kompilacji](../ide/understanding-build-platforms.md).)

> [!NOTE]
> Po zdefiniowaniu nowa konfiguracja rozwiązania i wybierz **Utwórz nowe konfiguracje projektu** pole wyboru [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] automatycznie przypisuje nowej konfiguracji do wszystkich projektów. Podobnie, kiedy należy zdefiniować nowa platforma rozwiązania i wybrać **Utwórz nowe platformy projektu** pole wyboru [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] automatycznie przypisuje nową platformę do wszystkich projektów. Jeśli dodasz projekt, który jest przeznaczony dla nowych platform, Visual Studio dodaje również tej platformy do listy platformy rozwiązania oraz przypisuje go do wszystkich projektów.
>
> Nadal można zmodyfikować ustawienia dla każdego projektu.

Konfiguracja rozwiązania aktywnego także kontekst środowiska IDE. Na przykład, jeśli pracujesz nad projektem i konfiguracją Określa, że będzie on kompilowany do urządzenia przenośnego, **przybornika** wyświetla tylko te elementy, których można użyć w projekcie urządzenia przenośnego.

## <a name="project-configurations"></a>Konfiguracje projektu
 Konfiguracja i platforma projekt jest ukierunkowany używanych ze sobą, aby określić właściwości do użycia, gdy jest on oparty. Projekt może mieć inny zestaw definicji właściwości dla każdej kombinacji konfiguracji i platformy. Aby zmodyfikować właściwości projektu, można użyć stron jej właściwości. (W **Eksploratora rozwiązań**, otwórz menu skrótów dla projektu, a następnie wybierz **właściwości**.)

 Dla każdej konfiguracji projektu można zdefiniować właściwości zależne od konfiguracji, zgodnie z potrzebami. Na przykład dla konkretnej kompilacji, można ustawić elementy projektu, które zostaną dołączone i jakie dane wyjściowe pliki zostaną utworzone, gdzie będzie umieścić i jak będzie optymalizowany.

 Konfiguracje projektu mogą się znacznie różnić. Właściwości w jednej konfiguracji może na przykład określić, że jego plik wyjściowy można zoptymalizować zajmować minimalna ilość miejsca, podczas gdy innej konfiguracji może określić, że jego plik wykonywalny zostanie uruchomiona przy maksymalnej prędkości.

 Konfiguracje projektu są przechowywane przez rozwiązanie — nie przez użytkownika, dzięki czemu mogą być współużytkowane przez zespół.

 Mimo że zależności projektu są niezależne od konfiguracji, zostanie utworzona tylko projekty, które są określone w aktywnej konfiguracji rozwiązania.

## <a name="how-visual-studio-assigns-project-configurations"></a>Jak przypisuje konfiguracje projektu w programie Visual Studio
 Podczas definiowania nowa konfiguracja rozwiązania i nie Kopiuj ustawień z istniejącego programu Visual Studio przypisuje domyślne konfiguracje projektu przy użyciu następujących kryteriów. Kryteria są obliczane w podanej kolejności.

1.  Jeśli projekt ma nazwę konfiguracji (*\<Nazwa konfiguracji > \<nazwa platformy >*) czy dokładnie pasuje nazwę Nowa konfiguracja rozwiązania tej konfiguracji jest przypisany. Nazwy konfiguracji nie jest rozróżniana wielkość liter.

2.  Jeśli projekt zawiera nazwy konfiguracji, w której części nazwy konfiguracji odpowiada nowa konfiguracja rozwiązania, tej konfiguracji jest przypisany, czy część platformy jest zgodny, czy nie.

3.  Jeśli nadal nie ma dopasowania, pierwsza konfiguracja, który znajduje się w projekcie zostanie przypisany.

## <a name="how-visual-studio-assigns-solution-configurations"></a>Jak platforma Azure przypisuje konfiguracje rozwiązania
 Po utworzeniu konfiguracji projektu (w **programu Configuration Manager**, wybierając **New** z menu rozwijanego w **konfiguracji** kolumny dla tego projektu) i Wybierz **Utwórz nowe konfiguracje rozwiązania** pole wyboru, Visual Studio szuka Konfiguracja rozwiązania o nazwie podobne do skompilowania projektu na każdej z obsługiwanych platform. W niektórych przypadkach program Visual Studio zmienia nazwę istniejącego konfiguracje rozwiązania lub definiuje nowe.

 Program Visual Studio przypisuje konfiguracje rozwiązania przy użyciu następujących kryteriów.

-   Jeśli Konfiguracja projektu nie określa platformy lub określa tylko jedną platformę, następnie konfiguracji rozwiązania, którego nazwa jest zgodny z typem nowa konfiguracja projektu jest znalezione lub dodane. Domyślna nazwa tej konfiguracji rozwiązania nie ma nazwy platformy; ma postać  *\<Nazwa konfiguracji projektu >*.

-   Jeśli projekt obsługuje wiele platform, Konfiguracja rozwiązania jest znaleźć lub dodano dla każdej z obsługiwanych platform. Nazwa każdej konfiguracji rozwiązania obejmuje zarówno nazwę konfiguracji projektu i platformy, a ma postać  *\<Nazwa konfiguracji projektu > \<nazwa platformy >*.

## <a name="see-also"></a>Zobacz także

- [Przewodnik: Tworzenie aplikacji](../ide/walkthrough-building-an-application.md)
- [Kompilowanie i tworzenie kompilacji](../ide/compiling-and-building-in-visual-studio.md)
- [Rozwiązania i projekty](../ide/solutions-and-projects-in-visual-studio.md)
- [Odwołanie kompilacji C/C++](/cpp/build/reference/c-cpp-building-reference)
- [Przełączniki wiersza polecenia Devenv](../ide/reference/devenv-command-line-switches.md)
- [Kompilowanie konfiguracji (Visual Studio dla komputerów Mac)](/visualstudio/mac/configurations)