---
title: Kodowanie i wiersz znaków podziału
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 59ed38c28c6818fb618156450d47c05b4f35d63d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62978172"
---
# <a name="encodings-and-line-endings"></a>Końce kodowania i wiersza

Następujące znaki są interpretowane jako podziały wierszy w programie Visual Studio:

- CR LF: Znaku powrotu karetki i wysuwu wiersza Unicode znaki 000 D + 000A

- LF: Znak nowego wiersza, Unicode 000A

- NEL: Następny wiersz, znaków Unicode 0085

- LS: Separator wiersza, znaków Unicode 2028

- PS: Separator akapitu, znaków Unicode 2029

Tekst, który jest kopiowany z innych aplikacji zachowuje oryginalne kodowanie i znaki podziału wiersza. Na przykład po Kopiuj tekst ze Schowka i wklej go do pliku tekstowego w programie Visual Studio tekst ma tych samych ustawień, których go w Notatniku.

Po otwarciu pliku, który zawiera znaki podziału wiersza w innej, zobaczysz okno dialogowe z pytaniem, czy powinny być znormalizowane znaki podziału wiersza niespójna, jakiego typu wiersza podziały wierszy i wybrać.

## <a name="advanced-save-options"></a>Zaawansowane opcje zapisywania

Możesz użyć **pliku** > **zaawansowane opcje zapisywania** okno dialogowe, aby określić typ ma znaki podziału wiersza. Można również zmienić kodowanie pliku przy użyciu tych samych ustawień.

![Okno dialogowe Zaawansowane opcje zapisywania](media/line_endings.png)

> [!NOTE]
> Jeśli nie widzisz **zaawansowane opcje zapisywania** na **pliku** menu, można go dodać. Wybierz **narzędzia**, **Dostosuj**, a następnie wybierz **polecenia** kartę. W **pasek Menu** listy rozwijanej wybierz **pliku**, następnie wybierz **Dodaj polecenie** przycisku. W **Dodaj polecenie** okno dialogowe, w obszarze **kategorie**, wybierz **pliku**, a następnie w polu **polecenia** wybierz  **Zaawansowane opcje zapisywania**. Wybierz **OK** , a następnie wybierz **Przenieś w dół** przycisk, aby przenieść polecenia do dowolnego miejsca, w menu. Wybierz **Zamknij** zamknąć **Dostosuj** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Dostosowywanie menu i pasków zadań](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md#customizing_menu).
>
> Alternatywnie, możesz uzyskać dostęp **zaawansowane opcje zapisywania** okno dialogowe, wybierając **pliku** > **Zapisz \<pliku\> jako**. W **Zapisz plik jako** okna dialogowego Wybierz trójkąt listy rozwijanej obok **Zapisz** przycisk, a następnie wybierz **Zapisz z kodowaniem**.

## <a name="see-also"></a>Zobacz także

- [Funkcje edytora kodu](../ide/writing-code-in-the-code-and-text-editor.md)