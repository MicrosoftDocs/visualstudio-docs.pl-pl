---
title: Aktualizowanie istniejących szablonów elementów projektu
ms.date: 01/02/2018
ms.topic: how-to
helpviewer_keywords:
- item templates, updating
- Visual Studio templates, updating
- project templates, updating
- updating templates [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: d5d9726ecbf3cb7c403f682aadb197a26b0dc26b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85283921"
---
# <a name="how-to-update-existing-templates"></a>Instrukcje: aktualizowanie istniejących szablonów

Po utworzeniu szablonu i przeprowadzeniu kompresji plików do pliku *zip* warto zmodyfikować szablon. Można to zrobić przez ręczne zmianę plików w szablonie lub przez wyeksportowanie nowego szablonu z projektu, który jest oparty na szablonie.

## <a name="use-the-export-template-wizard"></a>Korzystanie z Kreatora eksportu szablonów

Program Visual Studio zawiera **Kreatora eksportowania szablonu** , którego można użyć do zaktualizowania istniejącego szablonu:

1. Wybierz pozycję **plik**  >  **Nowy**  >  **projekt** z paska menu.

1. Wybierz szablon, który chcesz zaktualizować, i wykonaj kroki, aby utworzyć nowy projekt.

1. Zmodyfikuj projekt w programie Visual Studio. Na przykład zmień typ danych wyjściowych lub Dodaj nowy plik do projektu.

1. W menu **projekt** wybierz polecenie **Eksportuj szablon**.

    Zostanie otwarty **Kreator eksportu szablonu** .

1. Postępuj zgodnie z monitami wyświetlanymi w kreatorze, aby wyeksportować szablon jako plik *. zip* .

1. Obowiązkowe Umieść plik *. zip* w następującym katalogu: *%USERPROFILE%\Documents\Visual Studio \<version\> \Templates\ProjectTemplates* , aby udostępnić go do wyboru. Należy wykonać ten krok, jeśli nie wybrano opcji **automatycznie Importuj szablon do programu Visual Studio** w **Kreatorze eksportu szablonów**.

1. Usuń stary plik template *. zip* .

## <a name="manually-update-an-existing-template"></a>Ręcznie Aktualizuj istniejący szablon

Istniejący szablon można zaktualizować bez użycia **Kreatora eksportu szablonów**, modyfikując pliki w skompresowanym pliku *zip* .

### <a name="to-manually-update-an-existing-template"></a>Aby ręcznie zaktualizować istniejący szablon

1. Znajdź plik *zip* , który zawiera szablon. Szablony projektu użytkownika znajdują się w witrynie *%USERPROFILE%\Documents\Visual Studio \<version\> \Templates\ProjectTemplates*.

1. Wyodrębnij plik *zip* .

1. Zmodyfikuj lub Usuń bieżące pliki szablonu lub Dodaj nowe pliki do szablonu.

1. Otwórz, zmodyfikuj i Zapisz plik XML *. vstemplate* , aby obsłużyć zaktualizowane zachowanie lub nowe pliki.

    Aby uzyskać więcej informacji o schemacie *. vstemplate* , zobacz [Dokumentacja schematu szablonu programu Visual Studio (rozszerzalność)](../extensibility/visual-studio-template-schema-reference.md). Aby uzyskać więcej informacji o tym, co można Sparametryzuj w plikach źródłowych, zobacz [Parametry szablonu](../ide/template-parameters.md).

1. Wybierz pliki w szablonie, a następnie w menu kontekstowym lub prawym przyciskiem myszy, a następnie wybierz polecenie **Wyślij do**  >  **folderu skompresowanego (spakowanego)**.

    Wybrane pliki są kompresowane do pliku *zip* .

1. Umieść nowy plik *zip* w tym samym katalogu, w którym znajduje się stary plik *. zip* .

1. Usuń wyodrębnione pliki szablonów i stary plik template *. zip* .

## <a name="see-also"></a>Zobacz też

- [Dostosowywanie szablonów](../ide/customizing-project-and-item-templates.md)
- [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)
- [Odwołanie do schematu szablonu programu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Parametry szablonu](../ide/template-parameters.md)
