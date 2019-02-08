---
title: Tworzenie szablonów projektu
ms.date: 01/02/2018
ms.topic: conceptual
f1_keywords:
- VS.ExportTemplateWizard
helpviewer_keywords:
- project templates [Visual Studio], creating
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4feed7e3ebdab56adc2c607ed0075c1a7fc3c620
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55937984"
---
# <a name="how-to-create-project-templates"></a>Instrukcje: Tworzenie szablonów projektu

W tym temacie pokazano, jak utworzyć szablon przy użyciu **Kreatora eksportowania szablonu**, które pakiety szablonu w *zip* pliku.

## <a name="to-create-a-user-project-template-by-using-the-export-template-wizard"></a>Aby utworzyć szablon projektu użytkownika za pomocą Kreatora eksportowania szablonu

1. Utwórz projekt.

    > [!NOTE]
    > Gdy nazwy projektu, który będzie źródło szablonu, należy używać tylko znaków prawidłowego identyfikatora. W przeciwnym razie błędy kompilacji mogą występować w projektach, które są tworzone na podstawie szablonu. Aby uzyskać więcej informacji na temat prawidłowego identyfikatora znaków zobacz [zadeklarowane nazwy elementów (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names) lub [identyfikatory (C++)](/cpp/cpp/identifiers-cpp). Alternatywnie, można użyć [parametry szablonu](../ide/template-parameters.md) używać nazwy "bezpieczne" dla klas i przestrzeni nazw.

2. Edytuj projekt, dopóki nie jest gotowy do wyeksportowania jako szablon. Na przykład możesz edytować pliki kodu, aby wskazać, gdzie wymiany parametru powinny zostać wykonane. Zobacz [jak: Zastępowanie parametrów w szablonie](../ide/how-to-substitute-parameters-in-a-template.md).

3. Na **projektu** menu, wybierz **Eksportuj szablon**.

   **Kreatora eksportowania szablonu** zostanie otwarty.

4. Na **wybierz typ szablonu** wybierz opcję **szablonu projektu**. Wybierz projekt, którego chcesz wyeksportować do szablonu, a następnie wybierz **dalej**.

5. Na **wybierz opcje szablonu** strony, wprowadź nazwę i opcjonalny opis, ikona i Podgląd obrazu szablonu. Te elementy pojawią się w **nowy projekt** okno dialogowe. Wybierz **Zakończ**.

   Projekt jest eksportowana do *zip* pliku umieszczane w lokalizacji określonym produktem wyjściowym i, jeśli zaznaczone, zaimportowane do programu Visual Studio.

>[!NOTE]
> Można znaleźć szablonu w **nowy projekt** okna dialogowego rozwiń **zainstalowane** a następnie rozwiń kategorię, która odnosi się do `ProjectType` element *.vstemplate*pliku. Na przykład *.vstemplate* pliku, który zawiera `<ProjectType>CSharp</ProjectType>` pojawia się w obszarze **zainstalowane** > **Visual C#** , domyślnie. Szablonu można organizować w podkatalogu typu projektu, po prostu przez utworzenie folderu w katalogu i wprowadzenie do usługi szablonu *zip* plik. Aby uzyskać więcej informacji, zobacz [jak: Lokalizowanie i organizacja szablonów](../ide/how-to-locate-and-organize-project-and-item-templates.md).

## <a name="other-ways-to-create-project-templates"></a>Inne sposoby tworzenia szablonów projektu

Tworzenie szablonów projektów ręcznie zbierania plików wchodzących w skład projektu do folderu, a następnie tworząc *.vstemplate* plik XML z odpowiednie metadane. Aby uzyskać więcej informacji, zobacz [jak: Ręczne tworzenie szablonów sieci web](../ide/how-to-manually-create-web-templates.md).

W przypadku programu Visual Studio SDK zainstalowany ukończony szablon można opakować w pliku VSIX do wdrożenia przy użyciu **projekt VSIX** szablonu. Aby uzyskać więcej informacji, zobacz [rozpoczęcie korzystania z szablonu projektu VSIX](../extensibility/getting-started-with-the-vsix-project-template.md).

## <a name="see-also"></a>Zobacz także

- [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)
- [Instrukcje: Tworzenie szablonów elementów](../ide/how-to-create-item-templates.md)
- [Rozpoczynanie pracy przy użyciu szablonu projektu VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)