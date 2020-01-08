---
title: Zarządzanie właściwościami projektów i rozwiązań
ms.date: 11/04/2016
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 01fcdc09c9d3ee4f5a38a95ef4304bfdf537d527
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591310"
---
# <a name="manage-project-and-solution-properties"></a>Zarządzanie właściwościami projektów i rozwiązań

Projekty mają właściwości, które regulują wiele aspektów kompilowania, debugowania, testowania i wdrażania. Niektóre właściwości są wspólne dla wszystkich typów projektów, a niektóre z nich są unikatowe dla określonych języków lub platform. Aby uzyskać dostęp do właściwości projektu, kliknij prawym przyciskiem myszy węzeł projektu w **Eksplorator rozwiązań** i wybierz **Właściwości** lub przez wpisanie **Właściwości** w polu wyszukiwania na pasku menu, a następnie wybierz z wyników **okno właściwości** .

![Menu kontekstowe projektu](../ide/media/vs2015_proj_prop_menu.gif)

Projekty platformy .NET mogą także mieć węzeł właściwości w drzewie projektu.

![Węzeł właściwości w drzewie Eksplorator rozwiązań](../ide/media/vs2015_props_se.png)

> [!NOTE]
> Ten temat dotyczy programu Visual Studio w Windows. Aby uzyskać Visual Studio dla komputerów Mac, zobacz [Zarządzanie właściwościami rozwiązań i projektów (Visual Studio dla komputerów Mac)](/visualstudio/mac/managing-solutions-and-project-properties).

## <a name="project-properties"></a>Właściwości projektu

Właściwości projektu są zorganizowane w grupy, a każda grupa ma własną stronę właściwości. Strony mogą być różne dla różnych języków i typów projektów.

### <a name="c-visual-basic-and-f-projects"></a>C#, Visual Basic i F# projekty

W C#, Visual Basic i F# projekty, właściwości są uwidocznione w **projektancie projektu**. Na poniższej ilustracji przedstawiono stronę właściwości **kompilacja** dla projektu WPF w C#:

![Projektant projektu programu Visual Studio](../ide/media/vs2015_proppage_build.png)

Aby uzyskać informacje na temat każdej strony właściwości w **projektancie projektu**, zobacz [Informacje o właściwościach projektu](../ide/reference/project-properties-reference.md).

> [!TIP]
> Rozwiązania mają kilka właściwości i dlatego elementy projektu; te właściwości są dostępne w [okno właściwości](../ide/reference/properties-window.md), a nie **projektanta projektu**.

### <a name="c-and-javascript-projects"></a>C++i projekty JavaScript

C++i projekty JavaScript mają inny interfejs użytkownika do zarządzania właściwościami projektu. Na C++ tej ilustracji przedstawiono stronę właściwości projektu (strony JavaScript są podobne):

![Właściwości projektu&#43; &#43; języka Visual C](../ide/media/vs2015_projprops_cpp.png)

Aby uzyskać informacje C++ na temat właściwości projektu, zobacz [Work with ProjectC++Properties ()](/cpp/build/working-with-project-properties). Aby uzyskać więcej informacji na temat właściwości języka JavaScript, zobacz [strony właściwości, JavaScript](../ide/reference/property-pages-javascript.md).

## <a name="solution-properties"></a>Właściwości rozwiązania

Aby uzyskać dostęp do właściwości w rozwiązaniu, kliknij prawym przyciskiem myszy węzeł rozwiązanie w **Eksplorator rozwiązań** i wybierz polecenie **Właściwości**. W oknie dialogowym można ustawić konfiguracje **projektu dla kompilacji** lub kompilacje **wydań** , wybrać projekty, które powinny być projektem startowym po naciśnięciu klawisza **F5** i ustawić opcje analizy kodu.

## <a name="see-also"></a>Zobacz także

- [Rozwiązania i projekty w programie Visual Studio](../ide/solutions-and-projects-in-visual-studio.md)
- [Zarządzanie właściwościami rozwiązań i projektu (Visual Studio dla komputerów Mac)](/visualstudio/mac/managing-solutions-and-project-properties)
