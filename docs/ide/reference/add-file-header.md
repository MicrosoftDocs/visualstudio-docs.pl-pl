---
title: Dodaj nagłówek pliku
ms.date: 07/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 44cf9c34a69d665186a9f386e7ec34c5a59b8cdc
ms.sourcegitcommit: 8b1314ceab58e0d562cdbb1367fa738fdca7bf1e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/13/2020
ms.locfileid: "86285384"
---
# <a name="add-file-header"></a>Dodaj nagłówek pliku

Ta generacja kodu ma zastosowanie do:

- C#

- Visual Basic

**Co:** Dodaj nagłówki plików do istniejących plików, projektów i rozwiązań przy użyciu [EditorConfig](https://docs.microsoft.com/visualstudio/ide/create-portable-custom-editor-options#add-an-editorconfig-file-to-a-project).

**Kiedy:** Chcesz łatwo dodać nagłówek pliku do plików, projektów i rozwiązań.

**Dlaczego:** Zespół wymaga dołączenia nagłówka pliku do celów praw autorskich. 

## <a name="how-to"></a>Porady

1. Dodaj [EditorConfig](https://docs.microsoft.com/visualstudio/ide/create-portable-custom-editor-options#add-an-editorconfig-file-to-a-project) do projektu lub rozwiązania, jeśli jeszcze go nie masz.

2. Dodaj następującą regułę do pliku EditorConfig: *file_header_template*.

3. Ustaw wartość reguły tak, aby była równa tekstowi nagłówka, który ma zostać zastosowany.

    ![Reguła nagłówka pliku EditorConfig](media/add-file-header-rule.png)

> [!NOTE]
> Nie można mieć jawnych wielowierszowych EditorConfig i będzie trzeba użyć znaku nowego wiersza systemu UNIX, aby wstawić nowe wiersze.

4. Umieść karetkę na pierwszym wierszu dowolnego pliku C# lub Visual Basic.

5. Naciśnij klawisz **Ctrl** + **.** Aby wyzwolić menu **szybkie akcje i operacje refaktoryzacji** .

6. Wybierz pozycję **Dodaj nagłówek pliku**. 

    ![Reguła nagłówka pliku EditorConfig](media/add-file-header.png)

7. Aby zastosować nagłówek pliku do całego projektu lub rozwiązania, wybierz opcję **projekt** lub **rozwiązanie** w obszarze **Napraw wszystkie wystąpienia w:** .

8. Zostanie otwarte okno dialogowe **Popraw wszystkie wystąpienia** , w którym można wyświetlić podgląd zmian.

    ![Okno dialogowe Popraw wszystkie wystąpienia](media/file-header-preview-changes.png)

8. Wybierz pozycję **Zastosuj** , aby zastosować zmiany.

## <a name="see-also"></a>Zobacz także

- [Generowanie kodu](../code-generation-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)
