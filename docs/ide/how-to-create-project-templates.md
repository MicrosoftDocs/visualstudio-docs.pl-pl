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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591076"
---
# <a name="how-to-create-project-templates"></a>Jak: Tworzenie szablonów projektów

W tym temacie pokazano, jak utworzyć szablon za pomocą **Kreatora eksportu szablonów**, który pakuje szablon w pliku *zip.*

## <a name="use-the-export-template-wizard"></a>Korzystanie z Kreatora eksportu szablonów

1. Tworzenie projektu.

    > [!NOTE]
    > Podczas nazywania projektu, który będzie źródłem szablonu, należy używać tylko prawidłowych znaków identyfikacyjnych. W przeciwnym razie błędy kompilacji mogą wystąpić w projektach, które są tworzone na podstawie szablonu. Aby uzyskać więcej informacji na temat prawidłowych znaków identyfikacyjnych, zobacz [Zadeklarowane nazwy elementów (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names) lub [Identyfikatory (C++)](/cpp/cpp/identifiers-cpp). Alternatywnie można użyć [parametrów szablonu](../ide/template-parameters.md) do używania "bezpiecznych" nazw dla klas i obszarów nazw.

2. Edytuj projekt, aż będzie gotowy do wyeksportowania jako szablon. Na przykład można edytować pliki kodu, aby wskazać, gdzie powinno nastąpić zastąpienie parametrów. Zobacz [Jak: Zastępowanie parametrów w szablonie](../ide/how-to-substitute-parameters-in-a-template.md).

3. W menu **Projekt** wybierz polecenie **Eksportuj szablon**.

   Zostanie otwarty **Kreator szablonów eksportu.**

4. Na stronie **Wybierz typ szablonu** wybierz pozycję **Szablon projektu**. Wybierz projekt, który chcesz wyeksportować do szablonu, a następnie wybierz pozycję **Dalej**.

::: moniker range="vs-2017"

5. Na stronie **Wybierz opcje szablonu** wprowadź nazwę i opcjonalny opis, ikonę i obraz podglądu szablonu. Te elementy pojawią się w oknie dialogowym **Nowy projekt.** Wybierz **pozycję Zakończ**.

   Projekt jest eksportowany do pliku *zip* i umieszczany w określonej lokalizacji wyjściowej, a jeśli jest zaznaczona, importowany do programu Visual Studio.

Aby znaleźć szablon w oknie dialogowym **Nowy projekt,** rozwiń węzeł **Zainstalowany,** a następnie rozwiń kategorię odpowiadającą elementowi `ProjectType` w pliku *vstemplate.* Na przykład plik *vstemplate,* `<ProjectType>CSharp</ProjectType>` który zawiera pojawia się w obszarze **Zainstalowane** > **visual C#**, domyślnie. Szablon można uporządkować w podkatalog typu projektu, tworząc folder w tym katalogu i umieszczając w nim plik *zip* szablonu. Aby uzyskać więcej informacji, zobacz [Jak: Lokalizowanie i organizowanie szablonów](../ide/how-to-locate-and-organize-project-and-item-templates.md).

::: moniker-end

::: moniker range=">=vs-2019"

5. Na stronie **Wybierz opcje szablonu** wprowadź nazwę i opcjonalny opis, ikonę i obraz podglądu szablonu. Te elementy pojawią się w oknie dialogowym, w którym utworzysz nowy projekt. Wybierz **pozycję Zakończ**.

   Projekt jest eksportowany do pliku *zip* i umieszczany w określonej lokalizacji wyjściowej, a jeśli jest zaznaczona, importowany do programu Visual Studio.

Aby znaleźć szablon w oknie dialogowym, w którym tworzysz nowy projekt, wyszukaj go według nazwy lub przewiń listę. (Filtrowanie na podstawie języka lub typu projektu nie jest obecnie możliwe dla szablonów użytkowników).

::: moniker-end

## <a name="other-ways-to-create-project-templates"></a>Inne sposoby tworzenia szablonów projektów

Szablony projektów można tworzyć ręcznie, zbierając pliki, które tworzą projekt w folderze i tworząc plik XML *vstemplate* z odpowiednimi metadanymi. Aby uzyskać więcej informacji, zobacz [Jak: Ręcznie tworzyć szablony sieci Web](../ide/how-to-manually-create-web-templates.md).

Jeśli masz zainstalowany pakiet SDK programu Visual Studio, możesz zawinąć gotowy szablon w pliku VSIX do wdrożenia przy użyciu szablonu **projektu VSIX.** Aby uzyskać więcej informacji, zobacz [Wprowadzenie do szablonu projektu VSIX](../extensibility/getting-started-with-the-vsix-project-template.md).

## <a name="see-also"></a>Zobacz też

- [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)
- [Jak: Tworzenie szablonów elementów](../ide/how-to-create-item-templates.md)
- [Wprowadzenie do szablonu projektu VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)
