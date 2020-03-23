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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591297"
---
# <a name="manage-external-tools"></a>Zarządzanie narzędziami zewnętrznymi

Narzędzia zewnętrzne można wywołać z wewnątrz programu Visual Studio za pomocą menu **Narzędzia.** W menu **Narzędzia** dostępnych jest kilka domyślnych narzędzi, które można dostosować, dodając własne pliki wykonywalne.

## <a name="tools-available-on-the-tools-menu"></a>Narzędzia dostępne w menu Narzędzia

Menu **Narzędzia** zawiera kilka wbudowanych poleceń, w tym:

::: moniker range="vs-2017"

* **Rozszerzenia i aktualizacje** do [zarządzania rozszerzeniami programu Visual Studio](finding-and-using-visual-studio-extensions.md)
* **Menedżer urywków kodu** do [organizowania urywków kodu](code-snippets.md)
* **Dostosowywanie** do [dostosowywania menu i pasków narzędzi](how-to-customize-menus-and-toolbars-in-visual-studio.md)
* **Opcje** [ustawiania różnych opcji dla środowiska IDE programu Visual Studio i innych narzędzi](reference/options-dialog-box-visual-studio.md)

::: moniker-end

::: moniker range=">=vs-2019"

* **Menedżer urywków kodu** do [organizowania urywków kodu](code-snippets.md)
* **Dostosowywanie** do [dostosowywania menu i pasków narzędzi](how-to-customize-menus-and-toolbars-in-visual-studio.md)
* **Opcje** [ustawiania różnych opcji dla środowiska IDE programu Visual Studio i innych narzędzi](reference/options-dialog-box-visual-studio.md)

::: moniker-end

## <a name="add-new-tools-to-the-tools-menu"></a>Dodawanie nowych narzędzi do menu Narzędzia

Można dodać narzędzie zewnętrzne, aby pojawić się w menu **Narzędzia.**

1. Otwórz okno dialogowe **Narzędzia zewnętrzne,** wybierając pozycję Narzędzia**zewnętrzne** **narzędzia** > .

1. Kliknij pozycję **Dodaj**, a następnie wprowadź informacje. Na przykład następujący wpis powoduje, że **Eksplorator Windows** otwiera się w katalogu pliku, który jest aktualnie otwarty w programie Visual Studio:

   * Tytuł:`Open File Location`

   * Polecenia:`explorer.exe`

   * Argumenty:`/root, "$(ItemDir)"`

   ![Okno dialogowe Narzędzia zewnętrzne](media/external-tools-dialog.png)

Poniżej znajduje się pełna lista argumentów, które mogą być używane podczas definiowania narzędzia zewnętrznego:

|Nazwa|Argument|Opis|
|----------|--------------|-----------------|
|Ścieżka elementu|$(ItemPath)|Pełna nazwa pliku bieżącego pliku (dysk + ścieżka + nazwa pliku).|
|Katalog towarów|$(ItemDir)|Katalog bieżącego pliku (dysk + ścieżka).|
|Nazwa pliku elementu|$(Plik elementu)|Nazwa pliku bieżącego pliku (nazwa pliku).|
|Rozszerzenie towaru|$(ItemExt)|Rozszerzenie nazwy pliku bieżącego pliku.|
|Bieżąca linia|$(Linia curline)|Bieżąca pozycja wiersza kursora w oknie kodu.|
|Bieżąca kolumna|$(CurCol)|Bieżące położenie kolumny kursora w oknie kodu.|
|Bieżący tekst|$(CurText)|Zaznaczony tekst.|
|Ścieżka docelowa|$(Ścieżka docelowa)|Pełna nazwa pliku elementu, który ma zostać zbudowany (dysk + ścieżka + nazwa pliku).|
|Katalog docelowy|$(TargetDir)|Katalog elementu, który ma zostać utworzony.|
|Nazwa obiektu docelowego|$(Nazwa docelowa)|Nazwa pliku elementu, który ma zostać utworzony.|
|Rozszerzenie celu|$(TargetExt)|Rozszerzenie nazwy pliku elementu, który ma zostać utworzony.|
|Katalog binarny|$(BinDir)|Ostateczna lokalizacja pliku binarnego, który jest budowany (zdefiniowany jako dysk + ścieżka).|
|Katalog projektów|$(ProjectDir)|Katalog bieżącego projektu (dysk + ścieżka).|
|Nazwa pliku projektu|$(ProjectFileName)|Nazwa pliku bieżącego projektu (dysk + ścieżka + nazwa pliku).|
|Katalog rozwiązań|$(SolutionDir)|Katalog bieżącego rozwiązania (dysk + ścieżka).|
|Nazwa pliku rozwiązania|$(Nazwa pliku rozwiązania)|Nazwa pliku bieżącego rozwiązania (dysk + ścieżka + nazwa pliku).|

> [!NOTE]
> Na pasku stanu IDE są wyświetlane zmienne **Bieżąca linia** i **Bieżąca kolumna,** aby wskazać, gdzie znajduje się punkt wstawiania w aktywnym **Edytorze kodu**. Zmienna **Bieżący tekst** zwraca tekst lub kod wybrany w tej lokalizacji.

## <a name="see-also"></a>Zobacz też

- [Narzędzia do budowania języka C/C++](/cpp/build/reference/c-cpp-build-tools)
