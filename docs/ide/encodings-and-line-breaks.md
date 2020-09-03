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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75588593"
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

Za pomocą **File**  >  okna dialogowego**Zaawansowane opcje zapisywania** w pliku można określić typ pożądanych znaków podziału wiersza. Możesz również zmienić kodowanie pliku przy użyciu tych samych ustawień.

![Zaawansowane opcje zapisywania — okno dialogowe](media/line_endings.png)

> [!NOTE]
> Jeśli nie widzisz **opcji Zaawansowane zapisywanie** w menu **plik** , możesz je dodać. Wybierz **Narzędzia**, **Dostosuj**, a następnie wybierz kartę **polecenia** . Z listy rozwijanej **pasek menu** wybierz **plik**, a następnie wybierz przycisk **polecenie Dodaj** . W oknie dialogowym **Dodawanie polecenia** w obszarze **Kategorie**wybierz pozycję **plik**, a następnie na liście **polecenia** wybierz pozycję **Zaawansowane opcje zapisywania**. Wybierz **OK** , a następnie kliknij przycisk **Przenieś w dół** , aby przenieść polecenie do dowolnego miejsca w menu. Wybierz przycisk **Zamknij** , aby zamknąć okno dialogowe **Dostosowywanie** . Aby uzyskać więcej informacji, zobacz [Dostosowywanie menu i pasków narzędzi](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md#customizing_menu).
>
> Alternatywnie możesz uzyskać dostęp do okna dialogowego **Zaawansowane opcje zapisywania** , wybierając pozycję **plik**  >  **Zapisz \<file\> jako**. W oknie dialogowym **Zapisz plik jako** wybierz Trójkąt listy rozwijanej obok przycisku **Zapisz** , a następnie wybierz pozycję **Zapisz z kodowaniem**.

## <a name="see-also"></a>Zobacz też

- [Funkcje edytora kodu](../ide/writing-code-in-the-code-and-text-editor.md)
