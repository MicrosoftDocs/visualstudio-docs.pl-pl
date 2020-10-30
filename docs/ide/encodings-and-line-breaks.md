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
ms.openlocfilehash: 6634a0b2715fb83a397b5e8cd0c8c68274771e2a
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2020
ms.locfileid: "93045590"
---
# <a name="encodings-and-line-endings"></a>Kodowania i końce wierszy

Następujące znaki są interpretowane jako podziały wierszy w programie Visual Studio:

- CR LF: karetka + Return, znaki Unicode 000D + 000A

- LF: wiersz wysuwu wiersza, 000A znaków Unicode

- NEL: Następny wiersz, znak Unicode 0085

- LS: separator wiersza, znak Unicode 2028

- PS: Separator akapitu, znak Unicode 2029

Tekst skopiowany z innych aplikacji zachowuje pierwotne kodowanie i znaki podziału wiersza. Na przykład podczas kopiowania tekstu z programu Notepad i wklejania go do pliku tekstowego w programie Visual Studio, tekst ma te same ustawienia, które miały w Notatniku.

Po otwarciu pliku, który ma różne znaki podziału wiersza, może pojawić się okno dialogowe z pytaniem, czy niespójne znaki podziału wiersza powinny być znormalizowane, oraz jaki typ podziałów wierszy ma zostać wybrany.

## <a name="advanced-save-options"></a>Zaawansowane opcje zapisywania

Za pomocą **File**  >  okna dialogowego **Zaawansowane opcje zapisywania** w pliku można określić typ pożądanych znaków podziału wiersza. Możesz również zmienić kodowanie pliku przy użyciu tych samych ustawień.

![Zaawansowane opcje zapisywania — okno dialogowe](media/line_endings.png)

> [!NOTE]
> Jeśli nie widzisz **opcji Zaawansowane zapisywanie** w menu **plik** , możesz je dodać. 
> 1. Wybierz **Narzędzia** , **Dostosuj** , 
> 1. Wybierz kartę **polecenia** , wybierz przycisk radiowy **pasek menu** i z odpowiedniej listy rozwijanej wybierz **plik** . Wybierz przycisk **polecenia Dodaj** . 
> 1. W oknie dialogowym **Dodawanie polecenia** w obszarze **Kategorie** wybierz pozycję **plik** , a następnie na liście **polecenia** wybierz pozycję **Zaawansowane opcje zapisywania** . Wybierz przycisk **OK** .
> 1. Użyj przycisków **Przenieś w górę** i **Przenieś w dół** , aby przenieść polecenie do dowolnego miejsca w menu. Wybierz przycisk **Zamknij** , aby zamknąć okno dialogowe **Dostosowywanie** . 
> Aby uzyskać więcej informacji, zobacz [Dostosowywanie menu i pasków narzędzi](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md#customizing_menu).
>
> Alternatywnie możesz uzyskać dostęp do okna dialogowego **Zaawansowane opcje zapisywania** , wybierając pozycję **plik**  >  **Zapisz \<file\> jako** . W oknie dialogowym **Zapisz plik jako** wybierz Trójkąt listy rozwijanej obok przycisku **Zapisz** , a następnie wybierz pozycję **Zapisz z kodowaniem** .

## <a name="see-also"></a>Zobacz też

- [Funkcje edytora kodu](../ide/writing-code-in-the-code-and-text-editor.md)
