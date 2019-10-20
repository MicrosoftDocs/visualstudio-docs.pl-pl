---
title: Zarządzanie właściwościami projektu i rozwiązania | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: d727efc0-1096-4ede-84b6-31a65da22ac0
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ec48aac60a8f15527c92d19a38ca9f996dcfdd6f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651361"
---
# <a name="managing-project-and-solution-properties"></a>Zarządzanie właściwościami projektów i rozwiązań
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Projekty mają właściwości, które regulują wiele aspektów kompilowania, debugowania, testowania i wdrażania. Niektóre właściwości są wspólne dla wszystkich typów projektów, a niektóre z nich są unikatowe dla określonych języków lub platform. Aby uzyskać dostęp do właściwości projektu, kliknij prawym przyciskiem myszy węzeł projektu w Eksplorator rozwiązań i wybierz właściwości lub przez wpisanie właściwości w polu wyszukiwania **szybkiego** dostępu na pasku menu.

 ![Menu kontekstowe projektu](../ide/media/vs2015-proj-prop-menu.gif "vs2015_proj_prop_menu")

 Projekty platformy .NET mają również węzeł właściwości w drzewie projektu.

 ![Węzeł właściwości w drzewie Eksplorator rozwiązań](../ide/media/vs2015-props-se.png "VS2015_Props_SE")

> [!TIP]
> Rozwiązania mają kilka właściwości i dlatego elementy projektu; te właściwości są dostępne w [oknie właściwości](../ide/reference/properties-window.md), a nie w **projektancie projektu**.

## <a name="project-properties"></a>Właściwości projektu
 Właściwości projektu są zorganizowane w grupy, a każda grupa ma własną stronę właściwości, a strony mogą być różne dla różnych języków i typów projektów.

### <a name="c-and-visual-basic-projects"></a>C#i projekty Visual Basic
 W C# projektach i Visual Basic, właściwości są ujawniane w **projektancie projektu**. Na poniższej ilustracji przedstawiono stronę właściwości kompilacja dla projektu WPF w C#:

 ![Projektant projektu programu Visual Studio](../ide/media/vs2015-proppage-build.png "VS2015_PropPage_Build")

 Aby uzyskać informacje na temat każdej strony właściwości w projektancie projektu, zobacz [Informacje o właściwościach projektu](../ide/reference/project-properties-reference.md).

### <a name="c-and-javascript-projects"></a>C++i projekty JavaScript
 C++i projekty JavaScript mają inny interfejs użytkownika do zarządzania właściwościami projektu. Na C++ tej ilustracji przedstawiono stronę właściwości projektu (strony JavaScript są podobne):

 ![Właściwości projektu&#43; &#43; języka Visual C](../ide/media/vs2015-projprops-cpp.png "VS2015_ProjProps_cpp")

 Aby uzyskać informacje C++ na temat właściwości projektu, zobacz [Praca z właściwościami projektu](https://msdn.microsoft.com/library/9b0d6f8b-7d4e-4e61-aa75-7d14944816cd). Aby uzyskać więcej informacji na temat właściwości języka JavaScript, zobacz [strony właściwości, JavaScript](../ide/reference/property-pages-javascript.md).

## <a name="solution-properties"></a>Właściwości rozwiązania
 Aby uzyskać dostęp do właściwości w rozwiązaniu, kliknij prawym przyciskiem myszy węzeł rozwiązanie w **Eksplorator rozwiązań** i wybierz polecenie **Właściwości**. W oknie dialogowym można ustawić konfiguracje projektu dla kompilacji lub kompilacje wydań, wybrać projekty, które powinny być projektem startowym po naciśnięciu klawisza F5 i ustawić opcje analizy kodu.

## <a name="see-also"></a>Zobacz też
 [Rozwiązania i projekty w programie Visual Studio](../ide/solutions-and-projects-in-visual-studio.md)
