---
title: Aktualizowanie istniejących szablonów elementów projektu
ms.date: 01/02/2018
ms.topic: conceptual
helpviewer_keywords:
- item templates, updating
- Visual Studio templates, updating
- project templates, updating
- updating templates [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 44f99646330d3c8a75bd94310bc0adf9073f9d49
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591362"
---
# <a name="how-to-update-existing-templates"></a>Jak: Aktualizowanie istniejących szablonów

Po utworzeniu szablonu i skompresji plików do pliku *zip* można zmodyfikować szablon. Można to zrobić ręcznie, zmieniając pliki w szablonie lub eksportując nowy szablon z projektu opartego na szablonie.

## <a name="use-the-export-template-wizard"></a>Korzystanie z Kreatora eksportu szablonów

Program Visual Studio udostępnia **Kreatora szablonów eksportu,** który może służyć do aktualizacji istniejącego szablonu:

1. Z paska menu **wybierz pozycję Plik** > **nowego** > **projektu.**

1. Wybierz szablon, który chcesz zaktualizować, i przejdź przez kroki, aby utworzyć nowy projekt.

1. Zmodyfikuj projekt w programie Visual Studio. Na przykład zmień typ danych wyjściowych lub dodaj nowy plik do projektu.

1. W menu **Projekt** wybierz polecenie **Eksportuj szablon**.

    Zostanie otwarty **Kreator szablonów eksportu.**

1. Postępuj zgodnie z instrukcjami kreatora, aby wyeksportować szablon jako plik *zip.*

1. (Opcjonalnie) Umieść plik *zip* w następującym katalogu: *%USERPROFILE%\Documents\Visual Studio \<version\>\Templates\ProjectTemplates,* aby udostępnić go do wyboru. Ten krok należy wykonać, jeśli nie **wybrano opcji Automatycznie zaimportuj szablon do programu Visual Studio** w **Kreatorze eksportu szablonów**.

1. Usuń stary plik *zip* szablonu.

## <a name="manually-update-an-existing-template"></a>Ręczne aktualizowanie istniejącego szablonu

Istniejący szablon można zaktualizować bez użycia **Kreatora eksportu szablonów,** modyfikując pliki w skompresowanym pliku *zip.*

### <a name="to-manually-update-an-existing-template"></a>Aby ręcznie zaktualizować istniejący szablon

1. Znajdź plik *zip* zawierający szablon. Szablony projektów użytkownika znajdują się w pliku *%USERPROFILE%\Documents\Visual Studio \<version\>\Templates\ProjectTemplates*.

1. Wyodrębnij plik *.zip.*

1. Modyfikowanie lub usuwanie bieżących plików szablonów lub dodawanie nowych plików do szablonu.

1. Otwórz, zmodyfikuj i zapisz plik XML *vstemplate,* aby obsłużyć zaktualizowane zachowanie lub nowe pliki.

    Aby uzyskać więcej informacji na temat schematu *.vstemplate,* zobacz [Odwołanie do schematu szablonu programu Visual Studio (rozszerzalność)](../extensibility/visual-studio-template-schema-reference.md). Aby uzyskać więcej informacji na temat parametrów w plikach źródłowych, zobacz [Parametry szablonu](../ide/template-parameters.md).

1. Zaznacz pliki w szablonie, a następnie z menu kontekstowego lub z menu kontekstowego i wybierz polecenie **Wyślij do** > **folderu Skompresowanego (spakowanego).**

    Wybrane pliki zostaną skompresowane do pliku *zip.*

1. Umieść nowy plik *zip* w tym samym katalogu co stary plik *.zip.*

1. Usuń wyodrębnione pliki szablonów i stary plik *.zip* szablonu.

## <a name="see-also"></a>Zobacz też

- [Dostosowywanie szablonów](../ide/customizing-project-and-item-templates.md)
- [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)
- [Odwołanie do schematu szablonu programu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Parametry szablonu](../ide/template-parameters.md)
