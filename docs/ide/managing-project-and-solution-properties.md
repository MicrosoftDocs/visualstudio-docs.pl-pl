---
title: Zarządzanie właściwościami projektów i rozwiązań
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 77ac77ca999ef627c0f3c9e763b7e5799b97d679
ms.sourcegitcommit: bc43970c000f07c9cc2051f1264a9742943a9755
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2018
ms.locfileid: "51349247"
---
# <a name="manage-project-and-solution-properties"></a>Zarządzanie właściwościami projektów i rozwiązań

Projekty mają właściwości, które zarządzają wiele aspektów kompilacji, debugowanie, testowanie i wdrażanie. Niektóre właściwości są wspólne dla wszystkich typów projektów, a niektóre są unikatowe dla określonych języków lub platform. Dostęp do właściwości projektu, kliknij prawym przyciskiem myszy węzeł projektu w **Eksploratora rozwiązań** i wybierając pozycję **właściwości**, lub wpisując "properties" w **Szybkie uruchamianie** pole wyszukiwania na pasku menu.

![Menu kontekstowego projektu](../ide/media/vs2015_proj_prop_menu.gif)

Projekty .NET mogą zawierać również węzeł właściwości w drzewie projektu sam.

![Właściwości węzła w drzewie Eksploratora rozwiązań](../ide/media/vs2015_props_se.png)

> [!NOTE]
> Ten temat dotyczy programu Visual Studio w Windows. Dla programu Visual Studio dla komputerów Mac, zobacz [Zarządzanie właściwościami rozwiązania i projektu (Visual Studio dla komputerów Mac)](/visualstudio/mac/managing-solutions-and-project-properties).

## <a name="project-properties"></a>Właściwości projektu

Właściwości projektu są zorganizowane w grupy, a każda grupa ma swoją własną stronę właściwości. Strony mogą być różne dla różnych języków i typów projektów.

### <a name="c-visual-basic-and-f-projects"></a>C#, Visual Basic i F# projektów

W C#, Visual Basic i F# projektów, właściwości są widoczne w **projektanta projektu**. Poniższa ilustracja przedstawia **kompilacji** strony właściwości dla projektu WPF w C#:

![Projektant projektu programu Visual Studio](../ide/media/vs2015_proppage_build.png)

Aby uzyskać informacje o poszczególnych stron właściwości w programie **projektanta projektu**, zobacz [projektu odwołanie do właściwości](../ide/reference/project-properties-reference.md).

> [!TIP]
> Rozwiązania mają kilka właściwości, a więc elementy; projektu te właściwości są dostępne w [okno właściwości](../ide/reference/properties-window.md), a nie **projektanta projektu**.

### <a name="c-and-javascript-projects"></a>Projekty języka C++ i JavaScript

Projekty języka C++ i JavaScript mają inny użytkownik za pomocą interfejsu zarządzania właściwości projektu. Ta ilustracja przedstawia strony właściwości projektu C++ (strony w języku JavaScript są podobne):

![Program Visual C&#43; &#43; właściwości projektu](../ide/media/vs2015_projprops_cpp.png)

Aby uzyskać informacji na temat właściwości projektu C++, zobacz [Praca z właściwościami projektu (C++)](/cpp/ide/working-with-project-properties). Aby uzyskać więcej informacji na temat właściwości kodu JavaScript, zobacz [strony właściwości, JavaScript](../ide/reference/property-pages-javascript.md).

## <a name="solution-properties"></a>Właściwości rozwiązania

Aby uzyskać dostęp do właściwości rozwiązania, kliknij prawym przyciskiem myszy węzeł rozwiązania w **Eksploratora rozwiązań** i wybierz polecenie **właściwości**. W oknie dialogowym można ustawić konfiguracje projektu **debugowania** lub **wersji** kompilacji, wybierz, które projekty powinny być uruchamiania projektu podczas **F5** wciśnięty i kod zestawu Opcje analizy.

## <a name="see-also"></a>Zobacz także

- [Rozwiązania i projekty w programie Visual Studio](../ide/solutions-and-projects-in-visual-studio.md)
- [Zarządzanie właściwościami rozwiązania i projektu (Visual Studio dla komputerów Mac)](/visualstudio/mac/managing-solutions-and-project-properties)
