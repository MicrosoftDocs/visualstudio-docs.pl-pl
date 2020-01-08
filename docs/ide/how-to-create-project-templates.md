---
title: Tworzenie szablonów projektu
ms.date: 01/02/2018
ms.topic: conceptual
f1_keywords:
- VS.ExportTemplateWizard
helpviewer_keywords:
- project templates [Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: f4caebfdc4e61b683e0f1407d1522f6da2328fcf
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591076"
---
# <a name="how-to-create-project-templates"></a>Porady: Tworzenie szablonów projektów

W tym temacie pokazano, jak utworzyć szablon przy użyciu **Kreatora eksportowania szablonu**, które pakiety szablonu w *zip* pliku.

## <a name="use-the-export-template-wizard"></a>Korzystanie z Kreatora eksportu szablonów

1. Utwórz projekt.

    > [!NOTE]
    > Gdy nazwy projektu, który będzie źródło szablonu, należy używać tylko znaków prawidłowego identyfikatora. W przeciwnym razie błędy kompilacji mogą występować w projektach, które są tworzone na podstawie szablonu. Aby uzyskać więcej informacji na temat prawidłowego identyfikatora znaków zobacz [zadeklarowane nazwy elementów (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names) lub [identyfikatory (C++)](/cpp/cpp/identifiers-cpp). Alternatywnie, można użyć [parametry szablonu](../ide/template-parameters.md) używać nazwy "bezpieczne" dla klas i przestrzeni nazw.

2. Edytuj projekt, dopóki nie jest gotowy do wyeksportowania jako szablon. Na przykład możesz edytować pliki kodu, aby wskazać, gdzie wymiany parametru powinny zostać wykonane. Zobacz [instrukcje: zastępowanie parametrów w szablonie](../ide/how-to-substitute-parameters-in-a-template.md).

3. Na **projektu** menu, wybierz **Eksportuj szablon**.

   **Kreatora eksportowania szablonu** zostanie otwarty.

4. Na **wybierz typ szablonu** wybierz opcję **szablonu projektu**. Wybierz projekt, którego chcesz wyeksportować do szablonu, a następnie wybierz **dalej**.

::: moniker range="vs-2017"

5. Na **wybierz opcje szablonu** strony, wprowadź nazwę i opcjonalny opis, ikona i obrazu podglądu dla szablonu. Te elementy pojawią się w **nowy projekt** okno dialogowe. Wybierz **Zakończ**.

   Projekt jest eksportowana do *zip* pliku umieszczane w lokalizacji określonym produktem wyjściowym i, jeśli zaznaczone, zaimportowane do programu Visual Studio.

Można znaleźć szablonu w **nowy projekt** okna dialogowego rozwiń **zainstalowane** a następnie rozwiń kategorię, która odnosi się do `ProjectType` element *.vstemplate*pliku. Na przykład *.vstemplate* pliku, który zawiera `<ProjectType>CSharp</ProjectType>` pojawia się w obszarze **zainstalowane** > **Visual C#** , domyślnie. Szablonu można organizować w podkatalogu typu projektu, po prostu przez utworzenie folderu w katalogu i wprowadzenie do usługi szablonu *zip* plik. Aby uzyskać więcej informacji, zobacz [porady: lokalizowanie i organizacja szablonów](../ide/how-to-locate-and-organize-project-and-item-templates.md).

::: moniker-end

::: moniker range=">=vs-2019"

5. Na **wybierz opcje szablonu** strony, wprowadź nazwę i opcjonalny opis, ikona i obrazu podglądu dla szablonu. Te elementy będą wyświetlane w oknie dialogowym, w którym tworzysz nowy projekt. Wybierz **Zakończ**.

   Projekt jest eksportowana do *zip* pliku umieszczane w lokalizacji określonym produktem wyjściowym i, jeśli zaznaczone, zaimportowane do programu Visual Studio.

Aby znaleźć szablon w oknie dialogowym, w którym tworzysz nowy projekt, wyszukaj go według nazwy lub przewiń listę. (Filtrowanie na podstawie języka lub typu projektu nie jest obecnie możliwe dla szablonów użytkowników).

::: moniker-end

## <a name="other-ways-to-create-project-templates"></a>Inne sposoby tworzenia szablonów projektu

Szablony projektów można tworzyć ręcznie, zbierając pliki stanowiące projekt do folderu i tworząc plik XML *. vstemplate* z odpowiednimi metadanymi. Aby uzyskać więcej informacji, zobacz [porady: ręczne tworzenie szablonów sieci web](../ide/how-to-manually-create-web-templates.md).

W przypadku programu Visual Studio SDK zainstalowany ukończony szablon można opakować w pliku VSIX do wdrożenia przy użyciu **projekt VSIX** szablonu. Aby uzyskać więcej informacji, zobacz Rozpoczynanie [pracy z szablonem projektu VSIX](../extensibility/getting-started-with-the-vsix-project-template.md).

## <a name="see-also"></a>Zobacz także

- [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)
- [Porady: Tworzenie szablonów elementów](../ide/how-to-create-item-templates.md)
- [Rozpoczynanie pracy przy użyciu szablonu projektu VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)
