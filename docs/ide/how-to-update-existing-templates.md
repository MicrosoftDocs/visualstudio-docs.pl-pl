---
title: Aktualizowanie istniejących szablonów elementów projektu
ms.date: 01/02/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- item templates, updating
- Visual Studio templates, updating
- project templates, updating
- updating templates [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: db5b9c3f601ae11b704e54ae2ebcd58f10c4c724
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53835831"
---
# <a name="how-to-update-existing-templates"></a>Instrukcje: Aktualizowanie istniejących szablonów

Po utworzeniu szablonu i plików do skompresowania *zip* pliku, możesz chcieć zmodyfikować szablon. Można to zrobić ręcznie, zmieniając pliki w szablonie, lub przez wyeksportowanie szablonu z projektu, który jest oparty na szablonie.

## <a name="using-the-export-template-wizard-to-update-an-existing-project-template"></a>Przy użyciu Kreatora eksportowania szablonu, aby zaktualizować istniejący szablon projektu

Program Visual Studio udostępnia **Kreatora eksportowania szablonu** można zaktualizować istniejący szablon:

1. Otwórz **nowy projekt** okno dialogowe, wybierając **pliku** > **New** > **projektu**.

1. Wybierz szablon, który chcesz zaktualizować, wprowadź nazwę i lokalizację dla swojego projektu, a następnie wybierz **OK**.

1. Modyfikowanie projektu w programie Visual Studio.

1. Na **projektu** menu, wybierz **Eksportuj szablon**.

    **Kreatora eksportowania szablonu** zostanie otwarty.

1. Postępuj zgodnie z instrukcjami w kreatorze, aby wyeksportować szablon jako *zip* pliku.

1. (Opcjonalnie) Aby dodać szablon do **nowy projekt** okno dialogowe, miejsce *zip* pliku w następującym katalogu: *%USERPROFILE%\Documents\Visual Studio \<wersji\>\Templates\ProjectTemplates*. Musisz wykonać ten krok, jeśli nie wybrana opcja **automatycznie zaimportuj szablon do programu Visual Studio** w **Kreatora eksportowania szablonu**.

1. Usuń stary szablon *zip* pliku.

## <a name="manually-update-an-existing-template"></a>Ręcznie zaktualizować istniejący szablon

Możesz zaktualizować istniejący szablon bez użycia **Kreatora eksportowania szablonu**, modyfikując pliki znajdujące się w skompresowanym *zip* pliku.

### <a name="to-manually-update-an-existing-template"></a>Aby ręcznie zaktualizować istniejący szablon

1. Znajdź *zip* pliku, który zawiera szablon. Szablony projektów użytkownika znajdują się w folderze *%USERPROFILE%\Documents\Visual Studio \<wersji\>\Templates\ProjectTemplates*.

1. Wyodrębnij *zip* pliku.

1. Zmodyfikować lub usunąć bieżące pliki szablonu lub Dodaj nowe pliki do szablonu.

1. Otwierać, modyfikować i zapisywać *.vstemplate* pliku XML, aby obsłużyć zachowanie zaktualizowane lub nowe pliki.

    Aby uzyskać więcej informacji na temat *.vstemplate* schematu, zobacz [odwołanie do schematu szablonu Visual Studio (rozszerzalność)](../extensibility/visual-studio-template-schema-reference.md). Aby uzyskać więcej informacji na temat co można sparametryzować w plikach źródłowych, zobacz [parametry szablonu](../ide/template-parameters.md).

1. Wybierz pliki do szablonu, a następnie w menu kliknij prawym przyciskiem myszy lub kontekstu, a następnie wybierz **wysyłać** > **skompresowany folder (zip)**.

    Wybrane pliki są kompresowane do *zip* pliku.

1. Umieść nową *zip* pliku w tym samym katalogu co stary *zip* pliku.

1. Usuń pliki szablonów wyodrębniony i starego szablonu *zip* pliku.

## <a name="see-also"></a>Zobacz także

- [Dostosowywanie szablonów](../ide/customizing-project-and-item-templates.md)
- [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)
- [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Parametry szablonu](../ide/template-parameters.md)