---
title: Wprowadzenie do szablonu projektu VSIX | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio SDK, VSIX project template
ms.assetid: 89fac33e-9380-4723-9b45-048a6e16f0ed
caps.latest.revision: 26
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1f7230bce49342ad8e31baeb3f46c72f1c45d776
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51787734"
---
# <a name="getting-started-with-the-vsix-project-template"></a>Wprowadzenie do szablonu projektu VSIX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby utworzyć rozszerzenie lub istniejące rozszerzenie wdrożenia pakietu, można użyć szablonu projektu VSIX. Szablon projektu VSIX w wersji Visual Basic i Visual C# i jest instalowany jako część programu Visual Studio SDK.  
  
 Szablon projektu VSIX po prostu składa się z plik source.extension.vsixmanifest, który zawiera informacje o rozszerzeniu i zasobów, które wysłaniem go.  
  
 Aby znaleźć szablonu projektu VSIX, należy zainstalować zestawu SDK programu Visual Studio. Aby uzyskać więcej informacji, zobacz [programu Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="deploying-a-custom-project-template-using-the-vsix-project-template"></a>Wdrażanie niestandardowego szablonu projektu przy użyciu szablonu projektu VSIX  
 Poniższe kroki pokazują sposób używania projektu VSIX do pakietu szablonu projektu, który można udostępniać innym deweloperom lub przekazania do galerii Visual Studio.  
  
1.  Utwórz szablon projektu.  
  
    1.  Otwórz projekt służący do utworzenia szablonu. Ten projekt może być dowolnym typem projektu.  
  
    2.  Na **pliku** menu, kliknij przycisk **Eksportuj szablon**. Wykonaj kroki kreatora.  
  
         Plik zip jest tworzony w %USERPROFILE%\My Documents\Visual Studio  *\<wersji >* \My wyeksportowane szablony\\.  
  
2.  Utwórz pusty projekt VSIX.  
  
     Na **pliku** menu, kliknij przycisk **New** a następnie kliknij przycisk **projektu**. Wybierz opcję **języka Visual Basic** lub **Visual C#**. W obszarze wybranego węzła, wybierz **rozszerzalności**, a następnie wybierz pozycję **projekt VSIX**.  
  
3.  Dodaj plik zip do projektu. Ustaw jego **Kopiuj do katalogu wyjściowego** właściwość `Copy Always`.  
  
4.  W **Eksploratora rozwiązań**, kliknij dwukrotnie `source.extension.vsixmanifest` plik, aby otworzyć go w **Projektant manifestu VSIX**, a następnie dokonaj następujących zmian:  
  
    -   Ustaw **nazwa produktu** pole **mój szablon projektu**.  
  
    -   Ustaw **identyfikator produktu** pole **MyProjectTemplate - 1**.  
  
    -   Ustaw **Autor** pole **Fabrikam**.  
  
    -   Ustaw **opis** pole **mój szablon projektu**.  
  
    -   W **zasoby** Dodaj **Microsoft.VisualStudio.ProjectTemplate** wpisz i ustaw jego ścieżki na nazwę pliku zip.  
  
5.  Zapisz i zamknij plik source.extension.vsixmanifest.  
  
6.  Skompiluj projekt.  
  
7.  W katalogu wyjściowym kliknij dwukrotnie plik .vsix.  
  
8.  A **Instalator VSIX** pojawi się okno komunikatu. Postępuj zgodnie z instrukcjami, aby zainstalować rozszerzenie.  
  
9. Zamknij program Visual Studio, a następnie otwórz go ponownie.  
  
10. Wybierz **rozszerzenia i aktualizacje** (na **narzędzia** menu) i wybierz **szablony** kategorii. Jeden z dostępnych rozszerzeń powinien być **mój szablon projektu**.  
  
11. Nowy szablon projektu pojawia się w **nowy projekt** okna dialogowego, w tym samym miejscu co oryginalny szablon projektu. Na przykład, jeśli utworzono szablon o nazwie **konsoli VB** z aplikacji konsoli języka Visual Basic, **konsoli VB** pojawia się w tym samym okienku jako języka Visual Basic **aplikację Konsolową**szablonu.  
  
#### <a name="to-specify-the-location-of-the-template-in-the-new-project-dialog-box"></a>Aby określić lokalizację szablonu w oknie dialogowym Nowy projekt  
  
1.  Szablon foldery znajdują się w *ścieżkę instalacji w usłudze Visual Studio*\Common7\IDE\ProjectTemplates i *ścieżkę instalacji w usłudze Visual Studio*\Common7\IDE\ItemTemplates katalogów. Nazwy sekcji najwyższego poziomu w oknie dialogowym Nowy projekt nie odpowiadają dokładnie nazwy folderów szablonu. W przypadku, gdy będą się różnić, należy użyć nazwy folderu szablonu.  
  
     Zmień rozszerzenie pliku .vsix na .zip, a następnie otwórz plik.  
  
2.  Utwórz nowy folder o takiej samej nazwie jak części okna dialogowego Nowy projekt szablonu powinny być wyświetlane w.  
  
3.  Jeśli szablon jest pojawią się w podsekcji, utwórz podfolder o takiej samej nazwie.  
  
4.  Przenieś plik zip szablonu do nowego folderu.  
  
5.  Zmień rozszerzenie ZIP na .vsix.  
  
6.  Otwórz manifestu VSIX.  
  
7.  VSIX manifest zaktualizować **zasobów** ścieżka szablonu, tak aby punkty do katalogu głównego drzewa katalogów, który zawiera plik szablonu. Na przykład jeśli szablon \CSharp\Windows, powinien wskazywać odwołania \CSharp.

