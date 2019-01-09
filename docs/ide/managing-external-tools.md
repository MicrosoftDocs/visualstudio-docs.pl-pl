---
title: Zarządzanie narzędziami zewnętrznymi
ms.date: 11/20/2017
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- vs.externaltools
helpviewer_keywords:
- external tools [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8f918ad272683de5316467d1027e098c1ead91a6
ms.sourcegitcommit: 73861cd0ea92e50a3be1ad2a0ff0a7b07b057a1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54154066"
---
# <a name="manage-external-tools"></a>Zarządzanie narzędziami zewnętrznymi

Można wywołać narzędzia zewnętrzne z poziomu programu Visual Studio przy użyciu **narzędzia** menu. Kilka domyślne narzędzia są dostępne z **narzędzia** menu, a menu można dostosować, dodając inne elementy wykonywalne samodzielnie.

## <a name="tools-available-on-the-tools-menu"></a>Narzędzia dostępne w menu Narzędzia

**Narzędzia** menu zawiera kilka wbudowanych poleceń, takich jak:

* **Rozszerzenia i aktualizacje** do [zarządzać rozszerzeniami programu Visual Studio](finding-and-using-visual-studio-extensions.md)
* **Menedżer fragmentów kodu** do [organizowanie fragmentów kodu](code-snippets.md)
* **Ochrona preEmptive — Dotfuscator** można uruchomić [Dotfuscator Community Edition (CE)](dotfuscator/index.md) , gdy jest [zainstalowane](dotfuscator/install.md)
* **Dostosuj** do [Dostosowywanie menu i paski narzędzi](how-to-customize-menus-and-toolbars-in-visual-studio.md)
* **Opcje** do [ustawić szereg różnych opcji dla programu Visual Studio IDE i innych narzędzi](reference/options-dialog-box-visual-studio.md)

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
|Katalog rozwiązania|$ (Solutiondir)|Katalog bieżącego rozwiązania (dysku i ścieżki).|
|Nazwa pliku rozwiązania|$(SolutionFileName)|Nazwa pliku bieżącego rozwiązania (dysk i ścieżkę pliku nazwa).|

> [!NOTE]
> Na pasku stanu IDE Wyświetla **bieżącego wiersza** i **bieżącej kolumny** zmienne, aby wskazać, gdzie punkt wstawiania znajduje się w aktywnej **Edytor kodu**. **Aktualny tekst** zmiennej zwraca tekst lub kod wybrane w tej lokalizacji.

## <a name="see-also"></a>Zobacz także

- [Narzędzia kompilacji C/C++](/cpp/build/reference/c-cpp-build-tools)
