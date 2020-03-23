---
title: Kodowanie i znaki podziału wiersza
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.Encoding
helpviewer_keywords:
- line breaks
- encoding
- Visual Studio, encoding
- editors, line breaks
- line break characters
- Visual Studio, line break characters
ms.assetid: 8f9b3ffc-7b8d-44f4-87cb-dc29105be12d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6448b553c1da9e697bca3860cb8507727c99cc08
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75588593"
---
# <a name="encodings-and-line-endings"></a>Kodowanie i zakończenia wierszy

Następujące znaki są interpretowane jako podziały wierszy w programie Visual Studio:

- CR LF: Powrót karetki + kanał liniowy, znaki Unicode 000D + 000A

- LF: Kanał liniowy, znak Unicode 000A

- NEL: Następny wiersz, znak Unicode 0085

- LS: Separator linii, znak Unicode 2028

- PS: Separator akapitu, znak Unicode 2029

Tekst skopiowany z innych aplikacji zachowuje oryginalne kodowanie i znaki podziału wiersza. Na przykład podczas kopiowania tekstu z Notatnika i wklejać go do pliku tekstowego w programie Visual Studio, tekst ma takie same ustawienia, jak w Notatniku.

Po otwarciu pliku, który ma różne znaki podziału wiersza, może zostać wyświetlone okno dialogowe z pytaniem, czy niespójne znaki podziału wiersza powinny być znormalizowane i jaki typ podziałów wierszy wybrać.

## <a name="advanced-save-options"></a>Zaawansowane opcje zapisywania

Za pomocą okna dialogowego Opcje**zapisywania zaawansowanego** **pliku** > można określić odpowiedni typ znaków podziału wiersza. Można również zmienić kodowanie pliku z tymi samymi ustawieniami.

![Okno dialogowe Zaawansowane opcje zapisywania](media/line_endings.png)

> [!NOTE]
> Jeśli w menu **Plik** nie są widoczne **opcje zapisywania zaawansowanego,** możesz je dodać. Wybierz polecenie **Narzędzia**, **Dostosuj**, a następnie wybierz kartę **Polecenia.** Z listy rozwijanej **Pasek menu** wybierz pozycję **Plik**, a następnie wybierz przycisk **Dodaj polecenie.** W oknie dialogowym **Dodawanie polecenia** w obszarze **Kategorie**wybierz pozycję **Plik**, a następnie na liście **Polecenia** wybierz pozycję Zaawansowane **opcje zapisywania**. Wybierz **przycisk OK,** a następnie wybierz przycisk **Przenieś w dół,** aby przenieść polecenie w dowolne miejsce w menu. Wybierz **pozycję Zamknij,** aby zamknąć okno dialogowe **Dostosowywanie.** Aby uzyskać więcej informacji, zobacz [Dostosowywanie menu i pasków narzędzi](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md#customizing_menu).
>
> Alternatywnie można uzyskać dostęp do okna dialogowego **Zaawansowane opcje zapisywania,** wybierając **pozycję Plik** > **Zapisz \<\> plik jako**. W oknie dialogowym **Zapisywanie pliku jako** wybierz trójkąt rozwijany obok przycisku **Zapisz** i wybierz pozycję Zapisz **z kodowaniem**.

## <a name="see-also"></a>Zobacz też

- [Funkcje edytora kodu](../ide/writing-code-in-the-code-and-text-editor.md)
