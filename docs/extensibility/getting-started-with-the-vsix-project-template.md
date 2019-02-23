---
title: Wprowadzenie do szablonu projektu VSIX | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, VSIX project template
ms.assetid: 89fac33e-9380-4723-9b45-048a6e16f0ed
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f3de9dfd81b5b694e7163ea8e1a4e52240028e94
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56704192"
---
# <a name="get-started-with-the-vsix-project-template"></a>Rozpoczynanie pracy przy użyciu szablonu projektu VSIX
Aby utworzyć rozszerzenie lub istniejące rozszerzenie wdrożenia pakietu, można użyć szablonu projektu VSIX. Szablon projektu VSIX w wersji Visual Basic i Visual C# i jest instalowany jako część programu Visual Studio SDK.

 Szablon projektu VSIX składa się tylko z *source.extension.vsixmanifest* pliku, który zawiera informacje, rozszerzenia i zasoby wysłaniem go.

 Aby znaleźć szablonu projektu VSIX, należy zainstalować zestawu SDK programu Visual Studio. Aby uzyskać więcej informacji, zobacz [programu Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="deploy-a-custom-project-template-using-the-vsix-project-template"></a>Wdrażanie niestandardowego szablonu projektu przy użyciu szablonu projektu VSIX
 Poniższe kroki pokazują sposób używania projektu VSIX do pakietu szablonu projektu, który można udostępniać innym deweloperom lub przekazania do galerii Visual Studio.

1.  Utwórz szablon projektu.

    1.  Otwórz projekt służący do utworzenia szablonu. Ten projekt może być dowolnym typem projektu.

    2.  Na **projektu** menu, kliknij przycisk **Eksportuj szablon**. Wykonaj kroki kreatora.

         A *zip* plik zostanie utworzony w *%USERPROFILE%\My Documents\Visual Studio \<wersji > \My wyeksportowane szablony\\*.

2.  Utwórz pusty projekt VSIX.

     Na **pliku** menu, kliknij przycisk **New** a następnie kliknij przycisk **projektu**. Wybierz opcję **języka Visual Basic** lub **Visual C#**. W obszarze wybranego węzła, wybierz **rozszerzalności**, a następnie wybierz pozycję **projekt VSIX**.

3.  Dodaj *zip* pliku do projektu. Ustaw jego **Kopiuj do katalogu wyjściowego** właściwość `Copy Always`.

4.  W **Eksploratora rozwiązań**, kliknij dwukrotnie *source.extension.vsixmanifest* plik, aby otworzyć go w **Projektant manifestu VSIX**, a następnie dokonaj następujących zmian:

    -   Ustaw **nazwa produktu** pole **mój szablon projektu**.

    -   Ustaw **identyfikator produktu** pole **MyProjectTemplate - 1**.

    -   Ustaw **Autor** pole **Fabrikam**.

    -   Ustaw **opis** pole **mój szablon projektu**.

    -   W **zasoby** Dodaj **Microsoft.VisualStudio.ProjectTemplate** wpisz i ustaw jego ścieżki na nazwę *zip* pliku.

5.  Zapisz i Zamknij *source.extension.vsixmanifest* pliku.

6.  Skompiluj projekt.

7.  W katalogu wyjściowym, kliknij dwukrotnie *.vsix* pliku.

8.  A **Instalator VSIX** pojawi się okno komunikatu. Postępuj zgodnie z instrukcjami, aby zainstalować rozszerzenie.

9. Zamknij program Visual Studio, a następnie otwórz go ponownie.

10. Wybierz **rozszerzenia i aktualizacje** (na **narzędzia** menu) i wybierz **szablony** kategorii. Jeden z dostępnych rozszerzeń powinien być **mój szablon projektu**.

11. Nowy szablon projektu pojawia się w **nowy projekt** okna dialogowego, w tym samym miejscu co oryginalny szablon projektu. Na przykład, jeśli utworzono szablon o nazwie **konsoli VB** z aplikacji konsoli języka Visual Basic, **konsoli VB** pojawia się w tym samym okienku jako języka Visual Basic **aplikację Konsolową**szablonu.

### <a name="to-specify-the-location-of-the-template-in-the-new-project-dialog-box"></a>Aby określić lokalizację szablonu w oknie dialogowym Nowy projekt

1. Szablon foldery znajdują się w *\Common7\IDE\ProjectTemplates {Visual Studio instalacji Path}* i <em>\Common7\IDE\ItemTemplates {Visual Studio instalacji Path}} katalogi. Nazw najwyższego poziomu sekcje w **nowy projekt</em>*  okna dialogowego nie odpowiadają dokładnie nazwy folderów szablonu. W przypadku, gdy będą się różnić, należy użyć nazwy folderu szablonu.

    Zmiana *.vsix* rozszerzenie do pliku *zip*, a następnie otwórz plik.

2. Utwórz nowy folder o takiej samej nazwie jako części **nowy projekt** szablonu powinny być wyświetlane w oknie dialogowym.

3. Jeśli szablon jest pojawią się w podsekcji, utwórz podfolder o takiej samej nazwie.

4. Przenieś szablonu *zip* pliku do nowego folderu.

5. Zmiana *zip* rozszerzenie *.vsix*.

6. Otwórz manifestu VSIX.

7. VSIX manifest zaktualizować **zasobów** ścieżka szablonu, tak aby punkty do katalogu głównego drzewa katalogów, który zawiera plik szablonu. Na przykład, jeśli szablon znajduje się w *\CSharp\Windows*, powinien wskazywać odwołania *\CSharp*.
