---
title: Zarządzanie narzędziami zewnętrznymi
ms.date: 11/20/2017
ms.topic: conceptual
f1_keywords:
- vs.externaltools
helpviewer_keywords:
- external tools [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0f22c687f88c7736d5c088ebc28ff490c4c16b8f
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591297"
---
# <a name="manage-external-tools"></a>Zarządzanie narzędziami zewnętrznymi

Możesz wywoływać zewnętrzne narzędzia z programu Visual Studio za pomocą menu **Narzędzia** . W menu **Narzędzia** dostępne są kilka domyślnych narzędzi i można dostosować je, dodając inne własne pliki wykonywalne.

## <a name="tools-available-on-the-tools-menu"></a>Narzędzia dostępne w menu Narzędzia

Menu **Narzędzia** zawiera kilka wbudowanych poleceń, takich jak:

::: moniker range="vs-2017"

* **Rozszerzenia i aktualizacje** do [zarządzania rozszerzeniami programu Visual Studio](finding-and-using-visual-studio-extensions.md)
* **Menedżer fragmentów kodu** do [organizowania fragmentów kodu](code-snippets.md)
* **Dostosuj** , aby [dostosować menu i paski narzędzi](how-to-customize-menus-and-toolbars-in-visual-studio.md)
* **Opcje** [ustawiania różnych opcji dla środowiska IDE programu Visual Studio i innych narzędzi](reference/options-dialog-box-visual-studio.md)

::: moniker-end

::: moniker range=">=vs-2019"

* **Menedżer fragmentów kodu** do [organizowania fragmentów kodu](code-snippets.md)
* **Dostosuj** , aby [dostosować menu i paski narzędzi](how-to-customize-menus-and-toolbars-in-visual-studio.md)
* **Opcje** [ustawiania różnych opcji dla środowiska IDE programu Visual Studio i innych narzędzi](reference/options-dialog-box-visual-studio.md)

::: moniker-end

## <a name="add-new-tools-to-the-tools-menu"></a>Dodaj nowe narzędzia do menu Narzędzia

Możesz dodać zewnętrzne narzędzie, które ma być wyświetlane w menu **Narzędzia** .

1. Otwórz okno dialogowe **narzędzia zewnętrzne** , wybierając pozycję **Narzędzia** > **narzędzia zewnętrzne**.

1. Kliknij przycisk **Dodaj**, a następnie Wypełnij informacje. Na przykład poniższy wpis powoduje otwarcie **Eksploratora Windows** w katalogu pliku, który jest aktualnie otwarty w programie Visual Studio:

   * Tytuł: `Open File Location`

   * Polecenie: `explorer.exe`

   * Argumenty: `/root, "$(ItemDir)"`

   ![Okno dialogowe narzędzia zewnętrzne](media/external-tools-dialog.png)

Poniżej znajduje się pełna lista argumentów, których można użyć podczas definiowania narzędzia zewnętrznego:

|Nazwa|Argument|Opis|
|----------|--------------|-----------------|
|Ścieżka elementu|$ (Ścieżki elementu)|Pełna nazwa pliku bieżącego pliku (dysk + ścieżka + nazwa pliku).|
|Katalog elementu|$ (ItemDir)|Katalog bieżącego pliku (dysk + ścieżka).|
|Nazwa pliku elementu|$ (ItemFilename)|Nazwa pliku bieżącego pliku (nazwa pliku).|
|Rozszerzenie elementu|$ (ItemExt)|Rozszerzenie nazwy pliku bieżącego pliku.|
|Bieżący wiersz|$ (CurLine)|Pozycja bieżącego wiersza kursora w oknie kodu.|
|Bieżąca kolumna|$ (CurCol)|Bieżąca pozycja kolumny kursora w oknie kodu.|
|Bieżący tekst|$ (CurText)|Zaznaczony tekst.|
|Ścieżka docelowa|$ (TargetPath)|Pełna nazwa pliku elementu do skompilowania (dysk + ścieżka + nazwa pliku).|
|Katalog docelowy|$ (TargetDir)|Katalog elementu do skompilowania.|
|Nazwa docelowa|$ (TargetName)|Nazwa pliku elementu do skompilowania.|
|Rozszerzenie docelowe|$ (TargetExt)|Rozszerzenie nazwy pliku do skompilowania.|
|Katalog binarny|$ (BinDir)|Końcowa lokalizacja tworzonego pliku binarnego (zdefiniowana jako dysk + ścieżka).|
|Katalog projektu|$ (ProjectDir)|Katalog bieżącego projektu (dysk + ścieżka).|
|Nazwa pliku projektu|$(ProjectFileName)|Nazwa pliku bieżącego projektu (dysk + ścieżka + nazwa pliku).|
|Katalog rozwiązania|$ (SolutionDir)|Katalog bieżącego rozwiązania (dysk + ścieżka).|
|Nazwa pliku rozwiązania|$(SolutionFileName)|Nazwa pliku bieżącego rozwiązania (dysk + ścieżka + nazwa pliku).|

> [!NOTE]
> Pasek stanu IDE wyświetla **bieżący wiersz** i bieżące zmienne **kolumn** , aby wskazać, gdzie punkt wstawiania znajduje się w aktywnym **edytorze kodu**. **Bieżąca zmienna tekstowa** zwraca tekst lub kod wybrany w tej lokalizacji.

## <a name="see-also"></a>Zobacz także

- [Narzędzia dlaC++ języka C/build](/cpp/build/reference/c-cpp-build-tools)
