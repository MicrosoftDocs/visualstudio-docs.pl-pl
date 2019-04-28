---
title: Zarządzanie narzędziami zewnętrznymi
ms.date: 11/20/2017
ms.topic: conceptual
f1_keywords:
- vs.externaltools
helpviewer_keywords:
- external tools [Visual Studio]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3562ed9ebf2d62ab002ac227486218c8c38ad337
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62535689"
---
# <a name="manage-external-tools"></a>Zarządzanie narzędziami zewnętrznymi

Można wywołać narzędzia zewnętrzne z poziomu programu Visual Studio przy użyciu **narzędzia** menu. Kilka domyślne narzędzia są dostępne z **narzędzia** menu, a menu można dostosować, dodając inne elementy wykonywalne samodzielnie.

## <a name="tools-available-on-the-tools-menu"></a>Narzędzia dostępne w menu Narzędzia

**Narzędzia** menu zawiera kilka wbudowanych poleceń, w tym:

::: moniker range="vs-2017"

* **Rozszerzenia i aktualizacje** do [zarządzać rozszerzeniami programu Visual Studio](finding-and-using-visual-studio-extensions.md)
* **Menedżer fragmentów kodu** do [organizowanie fragmentów kodu](code-snippets.md)
* **Dostosuj** do [Dostosowywanie menu i paski narzędzi](how-to-customize-menus-and-toolbars-in-visual-studio.md)
* **Opcje** do [ustawić szereg różnych opcji dla programu Visual Studio IDE i innych narzędzi](reference/options-dialog-box-visual-studio.md)

::: moniker-end

::: moniker range=">=vs-2019"

* **Menedżer fragmentów kodu** do [organizowanie fragmentów kodu](code-snippets.md)
* **Dostosuj** do [Dostosowywanie menu i paski narzędzi](how-to-customize-menus-and-toolbars-in-visual-studio.md)
* **Opcje** do [ustawić szereg różnych opcji dla programu Visual Studio IDE i innych narzędzi](reference/options-dialog-box-visual-studio.md)

::: moniker-end

## <a name="add-new-tools-to-the-tools-menu"></a>Dodawanie nowych narzędzi do menu Narzędzia

Możesz dodać zewnętrznego narzędzia ma być wyświetlana w **narzędzia** menu.

1. Otwórz **zewnętrznych narzędzi** okno dialogowe, wybierając **narzędzia** > **zewnętrznych narzędzi**.

1. Kliknij przycisk **Dodaj**, a następnie wypełnij informacje. Na przykład następujący wpis powoduje **Eksplorator Windows** można otworzyć w katalogu pliku obecnie masz otwarty w programie Visual Studio:

   * Tytuł: `Open File Location`

   * Polecenie: `explorer.exe`

   * Argumenty: `/root, "$(ItemDir)"`

   ![Okno dialogowe narzędzia zewnętrzne](media/external-tools-dialog.png)

Oto Pełna lista argumentów, które mogą być używane podczas definiowania narzędzie zewnętrzne:

|Nazwa|Argument|Opis|
|----------|--------------|-----------------|
|Ścieżka elementu|$(ItemPath)|Pełnej nazwy pliku bieżącego pliku (dysk i ścieżkę pliku nazwa).|
|Element katalogu|$(ItemDir)|Katalog bieżącego pliku (dysku i ścieżki).|
|Nazwa pliku elementu|$(ItemFilename)|Nazwa pliku w bieżącym pliku (nazwa pliku).|
|Rozszerzenie elementu|$(ItemExt)|Rozszerzenie nazwy pliku bieżącego pliku.|
|Bieżący wiersz|$(CurLine)|Bieżący wiersz pozycja kursora w oknie kodu.|
|Bieżąca kolumna|$(CurCol)|Bieżąca kolumna pozycja kursora w oknie kodu.|
|Aktualny tekst|$(CurText)|Zaznaczony tekst.|
|Ścieżka docelowa|$(TargetPath)|Pełnej nazwy pliku elementu, który ma zostać utworzony (dysk i ścieżkę pliku nazwa).|
|Katalog docelowy|$(TargetDir)|Katalog elementu, który ma zostać utworzony.|
|Nazwa obiektu docelowego|$(TargetName)|Nazwa pliku elementu, który ma zostać utworzony.|
|Rozszerzenie docelowe|$(TargetExt)|Rozszerzenie nazwy pliku elementu, który ma zostać utworzony.|
|Katalog danych binarnych|$(BinDir)|Lokalizacji końcowej plik binarny, który jest konstruowany (zdefiniowany jako dysku i ścieżki).|
|Katalog projektu|$(ProjectDir)|Katalog bieżący projekt (dysku i ścieżki).|
|Nazwa pliku projektu|$(ProjectFileName)|Nazwa pliku bieżącego projektu (dysk i ścieżkę pliku nazwa).|
|Katalog rozwiązania|$(SolutionDir)|Katalog bieżącego rozwiązania (dysku i ścieżki).|
|Nazwa pliku rozwiązania|$(SolutionFileName)|Nazwa pliku bieżącego rozwiązania (dysk i ścieżkę pliku nazwa).|

> [!NOTE]
> Na pasku stanu IDE Wyświetla **bieżącego wiersza** i **bieżącej kolumny** zmienne, aby wskazać, gdzie punkt wstawiania znajduje się w aktywnej **Edytor kodu**. **Aktualny tekst** zmiennej zwraca tekst lub kod wybrane w tej lokalizacji.

## <a name="see-also"></a>Zobacz także

- [Narzędzia kompilacji C/C++](/cpp/build/reference/c-cpp-build-tools)
