---
title: Tworzenie szablonów projektu
ms.date: 01/02/2018
ms.topic: how-to
f1_keywords:
- VS.ExportTemplateWizard
helpviewer_keywords:
- project templates [Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: e6f168244971a348cdb7938af463538d0fa2acaf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85284389"
---
# <a name="how-to-create-project-templates"></a>Instrukcje: Tworzenie szablonów projektu

W tym temacie pokazano, jak utworzyć szablon przy użyciu **Kreatora eksportu szablonów**, który pakuje szablon w pliku *zip* .

## <a name="use-the-export-template-wizard"></a>Korzystanie z Kreatora eksportu szablonów

1. Utwórz projekt.

    > [!NOTE]
    > Używaj tylko prawidłowych znaków identyfikatora podczas nadawania nazwy projektowi, który będzie źródłem szablonu. W przeciwnym razie błędy kompilacji mogą wystąpić w projektach, które są tworzone na podstawie szablonu. Aby uzyskać więcej informacji na temat prawidłowych znaków identyfikatora, zobacz [zadeklarowane nazwy elementów (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names) lub [identyfikatory (C++)](/cpp/cpp/identifiers-cpp). Alternatywnie możesz użyć [parametrów szablonu](../ide/template-parameters.md) , aby użyć "bezpiecznych" nazw dla klas i przestrzeni nazw.

2. Edytuj projekt, dopóki nie będzie gotowy do eksportowania jako szablon. Na przykład możesz chcieć edytować pliki kodu, aby wskazać, gdzie ma zostać zamieniony parametr. Zobacz [jak: zastępowanie parametrów w szablonie](../ide/how-to-substitute-parameters-in-a-template.md).

3. W menu **projekt** wybierz polecenie **Eksportuj szablon**.

   Zostanie otwarty **Kreator eksportu szablonu** .

4. Na stronie **Wybieranie typu szablonu** wybierz **szablon projektu**. Wybierz projekt, który chcesz wyeksportować do szablonu, a następnie wybierz przycisk **dalej**.

::: moniker range="vs-2017"

5. Na stronie **Wybieranie opcji szablonu** wprowadź nazwę i opcjonalny opis, ikonę i obraz podglądu szablonu. Te elementy będą wyświetlane w oknie dialogowym **Nowy projekt** . Wybierz pozycję **Zakończ**.

   Projekt zostanie wyeksportowany do pliku *zip* i umieszczony w określonej lokalizacji wyjściowej, a w przypadku wybrania zaimportowany do programu Visual Studio.

Aby znaleźć szablon w oknie dialogowym **Nowy projekt** , rozwiń węzeł **zainstalowane** , a następnie rozwiń kategorię odpowiadającą `ProjectType` elementowi w pliku *. vstemplate* . Na przykład plik *. vstemplate* , który zawiera `<ProjectType>CSharp</ProjectType>` Domyślnie pojawia się w obszarze **zainstalowane**środowisko  >  **Visual C#**. Szablon można organizować w podkatalogu typu projektu po prostu przez utworzenie folderu w tym katalogu i umieszczenie w nim pliku *zip* szablonu. Aby uzyskać więcej informacji, zobacz [How to: Lokalizowanie i organizowanie szablonów](../ide/how-to-locate-and-organize-project-and-item-templates.md).

::: moniker-end

::: moniker range=">=vs-2019"

5. Na stronie **Wybieranie opcji szablonu** wprowadź nazwę i opcjonalny opis, ikonę i obraz podglądu szablonu. Te elementy będą wyświetlane w oknie dialogowym, w którym tworzysz nowy projekt. Wybierz pozycję **Zakończ**.

   Projekt zostanie wyeksportowany do pliku *zip* i umieszczony w określonej lokalizacji wyjściowej, a w przypadku wybrania zaimportowany do programu Visual Studio.

Aby znaleźć szablon w oknie dialogowym, w którym tworzysz nowy projekt, wyszukaj go według nazwy lub przewiń listę. (Filtrowanie na podstawie języka lub typu projektu nie jest obecnie możliwe dla szablonów użytkowników).

::: moniker-end

## <a name="other-ways-to-create-project-templates"></a>Inne sposoby tworzenia szablonów projektu

Szablony projektów można tworzyć ręcznie, zbierając pliki stanowiące projekt do folderu i tworząc plik XML *. vstemplate* z odpowiednimi metadanymi. Aby uzyskać więcej informacji, zobacz [How to: Manual Create Web templates](../ide/how-to-manually-create-web-templates.md).

Jeśli masz zainstalowany zestaw Visual Studio SDK, możesz otoczyć gotowy szablon w pliku VSIX do wdrożenia przy użyciu szablonu **projektu VSIX** . Aby uzyskać więcej informacji, zobacz Rozpoczynanie [pracy z szablonem projektu VSIX](../extensibility/getting-started-with-the-vsix-project-template.md).

## <a name="see-also"></a>Zobacz też

- [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)
- [Instrukcje: Tworzenie szablonów elementów](../ide/how-to-create-item-templates.md)
- [Wprowadzenie do szablonu projektu VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)
