---
title: Wdrażanie programu VSIX w języku DSL | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 6ce16f06-1978-4e19-8cdc-441ee65a3fb2
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: be9d3d44bfceaae1f2912086c3d20c90ce1e094b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75916547"
---
# <a name="vsix-deployment-of-a-dsl"></a>Wdrożenie VSIX dla języka DSL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Język specyficzny dla domeny można zainstalować na własnym komputerze lub na innych komputerach. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] musi być już zainstalowana na komputerze docelowym.

## <a name="installing-and-uninstalling-a-dsl-by-using-the-vsx"></a><a name="Installing"></a> Instalowanie i odinstalowywanie DSL przy użyciu VSX
 Gdy linia DSL jest instalowana przez tę metodę, użytkownik może otworzyć plik DSL z poziomu programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , ale nie można otworzyć go w Eksploratorze Windows.

#### <a name="to-install-a-dsl-by-using-the-vsix"></a>Aby zainstalować DSL przy użyciu VSIX

1. Na komputerze Znajdź plik **. vsix** , który został skompilowany przez projekt pakietu DSL.

    1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt **DslPackage** , a następnie kliknij polecenie **Otwórz folder w Eksploratorze Windows**.

    2. Znajdź plik ** \\ \* \\ bin**_YourProject_**. DslPackage. vsix**

2. Skopiuj plik **. vsix** do komputera docelowego, na którym chcesz zainstalować DSL. Może to być własny komputer lub inny.

    - Komputer docelowy musi mieć jedną z wersji programu [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] , która obsługuje językami DSL w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [obsługiwane wersje programu Visual Studio dla wizualizacji & Modeling SDK](../modeling/supported-visual-studio-editions-for-visualization-amp-modeling-sdk.md).

    - Komputer docelowy musi mieć jedną z wersji [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] określonych w **DslPackage\source.Extensions.manifest**.

3. Na komputerze docelowym kliknij dwukrotnie plik **. vsix** .

     Zostanie otwarty **Instalator rozszerzenia programu Visual Studio** , który zainstaluje rozszerzenie.

4. Uruchom lub Uruchom ponownie [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] .

5. Aby przetestować DSL, użyj, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Aby utworzyć nowy plik, który ma rozszerzenie zdefiniowane dla DSL.

#### <a name="to-uninstall-a-dsl-that-was-installed-by-using-vsx"></a>Aby odinstalować program DSL, który został zainstalowany przy użyciu VSX

1. W menu **Narzędzia** kliknij pozycję **Menedżer rozszerzeń**.

2. Rozwiń **zainstalowane rozszerzenia**.

3. Wybierz rozszerzenie, w którym zdefiniowano DSL, a następnie kliknij przycisk **Odinstaluj**.

   Rzadko błędne rozszerzenie nie zostanie załadowane i tworzy raport w oknie błędu, ale nie jest wyświetlany w Menedżerze rozszerzeń. W takim przypadku można usunąć rozszerzenie, usuwając plik z:

   *LocalAppData* **\Microsoft\VisualStudio\10.0\Extensions**
