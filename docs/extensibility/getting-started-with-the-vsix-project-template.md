---
title: Wprowadzenie do szablonu projektu VSIX | Dokumentacja firmy Microsoft
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, VSIX project template
ms.assetid: 89fac33e-9380-4723-9b45-048a6e16f0ed
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a8bb85e507e62bf7dd13288cbd08d7bf9d06973e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66342463"
---
# <a name="get-started-with-the-vsix-project-template"></a>Rozpoczynanie pracy przy użyciu szablonu projektu VSIX

Aby utworzyć rozszerzenie lub istniejące rozszerzenie wdrożenia pakietu, można użyć szablonu projektu VSIX. Szablon projektu VSIX w wersji Visual Basic i Visual C# i jest instalowany jako część programu Visual Studio SDK.

 Szablon projektu VSIX składa się tylko z *source.extension.vsixmanifest* pliku, który zawiera informacje, rozszerzenia i zasoby wysłaniem go.

 Aby znaleźć szablonu projektu VSIX, należy zainstalować zestawu SDK programu Visual Studio. Aby uzyskać więcej informacji, zobacz [programu Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="deploy-a-custom-project-template-using-the-vsix-project-template"></a>Wdrażanie niestandardowego szablonu projektu przy użyciu szablonu projektu VSIX

 Poniższe kroki pokazują sposób używania projektu VSIX do pakietu szablonu projektu, który można udostępniać innym deweloperom lub przekazania do galerii Visual Studio.

1. Utwórz szablon projektu.

    1. Otwórz projekt służący do utworzenia szablonu. Ten projekt może być dowolnym typem projektu.

    2. Na **projektu** menu, kliknij przycisk **Eksportuj szablon**. Wykonaj kroki kreatora.

         A *zip* plik zostanie utworzony w *%USERPROFILE%\My Documents\Visual Studio {version} \My wyeksportowane szablony\\* .

2. Utwórz pusty projekt VSIX.

     Wybierz **pliku** > **nowe** > **projektu**. W polu wyszukiwania wpisz "vsix", a następnie wybierz opcję **C#** lub **języka Visual Basic** wersję **projekt VSIX**.

3. Dodaj *zip* pliku do projektu. Ustaw jego **Kopiuj do katalogu wyjściowego** właściwość `Copy Always`.

4. W **Eksploratora rozwiązań**, kliknij dwukrotnie *source.extension.vsixmanifest* plik, aby otworzyć go w **Projektant manifestu VSIX**, a następnie dokonaj następujących zmian:

    - Ustaw **nazwa produktu** pole **mój szablon projektu**.

    - Ustaw **identyfikator produktu** pole **MyProjectTemplate - 1**.

    - Ustaw **Autor** pole **Fabrikam**.

    - Ustaw **opis** pole **mój szablon projektu**.

    - W **zasoby** Dodaj **Microsoft.VisualStudio.ProjectTemplate** wpisz i ustaw jego ścieżki na nazwę *zip* pliku.

5. Zapisz i Zamknij *source.extension.vsixmanifest* pliku.

6. Skompiluj projekt.

7. W katalogu wyjściowym, kliknij dwukrotnie *.vsix* pliku.

8. A **Instalator VSIX** pojawi się okno komunikatu. Postępuj zgodnie z instrukcjami, aby zainstalować rozszerzenie.

9. Zamknij program Visual Studio, a następnie otwórz go ponownie.

::: moniker range="vs-2017"

10. Wybierz **rozszerzenia i aktualizacje** (na **narzędzia** menu) i wybierz **szablony** kategorii. Jeden z dostępnych rozszerzeń powinien być **mój szablon projektu**.

::: moniker-end

::: moniker range=">=vs-2019"

10. Wybierz **Zarządzaj rozszerzeniami** (na **rozszerzenia** menu) i wybierz **szablony** kategorii. Jeden z dostępnych rozszerzeń powinien być **mój szablon projektu**.

::: moniker-end

11. Nowy szablon projektu pojawia się w **nowy projekt** okna dialogowego, w tym samym miejscu co oryginalny szablon projektu. Na przykład, jeśli utworzono szablon o nazwie **konsoli VB** z aplikacji konsoli języka Visual Basic, **konsoli VB** pojawia się w tym samym okienku jako języka Visual Basic **aplikację Konsolową**szablonu.

### <a name="to-specify-the-location-of-the-template-in-the-new-project-dialog-box"></a>Aby określić lokalizację szablonu w oknie dialogowym Nowy projekt

1. Szablon foldery znajdują się w *\Common7\IDE\ProjectTemplates {Visual Studio instalacji Path}* i *\Common7\IDE\ItemTemplates {Visual Studio instalacji Path}* katalogów. Nazwy sekcje najwyższego poziomu w **nowy projekt** okna dialogowego nie odpowiadają dokładnie nazwy folderów szablonu. W przypadku, gdy będą się różnić, należy użyć nazwy folderu szablonu.

    Zmiana *.vsix* rozszerzenie do pliku *zip*, a następnie otwórz plik.

2. Utwórz nowy folder o takiej samej nazwie jako części **nowy projekt** szablonu powinny być wyświetlane w oknie dialogowym.

3. Jeśli szablon jest pojawią się w podsekcji, utwórz podfolder o takiej samej nazwie.

4. Przenieś szablonu *zip* pliku do nowego folderu.

5. Zmiana *zip* rozszerzenie *.vsix*.

6. Otwórz manifestu VSIX.

7. VSIX manifest zaktualizować **zasobów** ścieżka szablonu, tak aby punkty do katalogu głównego drzewa katalogów, który zawiera plik szablonu. Na przykład, jeśli szablon znajduje się w *\CSharp\Windows*, powinien wskazywać odwołania *\CSharp*.
