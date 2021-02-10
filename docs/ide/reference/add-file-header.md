---
title: Dodawanie nagłówka pliku
description: Dowiedz się, jak dodać nagłówki plików do istniejących plików, projektów i rozwiązań przy użyciu pliku EditorConfig.
ms.custom: SEO-VS-2020
ms.date: 07/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 2b177092b04d5042f62dfd0b34d2bfbf4f1f0228
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933872"
---
# <a name="add-file-header"></a>Dodawanie nagłówka pliku

Ta generacja kodu ma zastosowanie do:

- C#

- Visual Basic

**Co:** Dodaj nagłówki plików do istniejących plików, projektów i rozwiązań przy użyciu [EditorConfig](../create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project).

**Kiedy:** Chcesz łatwo dodać nagłówek pliku do plików, projektów i rozwiązań.

**Dlaczego:** Zespół wymaga dołączenia nagłówka pliku do celów praw autorskich. 

## <a name="how-to"></a>Porady

1. Dodaj [EditorConfig](../create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project) do projektu lub rozwiązania, jeśli jeszcze go nie masz.

2. Dodaj następującą regułę do pliku EditorConfig: *file_header_template*.

3. Ustaw wartość reguły tak, aby była równa tekstowi nagłówka, który ma zostać zastosowany. Można użyć `{fileName}` jako symbolu zastępczego dla nazwy pliku.

    ![Zrzut ekranu przedstawiający plik EditorConfig z wartością file_header_template.](media/add-file-header-rule.png)

    > [!NOTE]
    > Nie można mieć jawnych wielowierszowych EditorConfig i będzie trzeba użyć znaku nowego wiersza systemu UNIX, aby wstawić nowe wiersze.

4. Umieść karetkę na pierwszym wierszu dowolnego pliku C# lub Visual Basic.

5. Naciśnij klawisz **Ctrl** + **.** Aby wyzwolić menu **szybkie akcje i operacje refaktoryzacji** .

6. Wybierz pozycję **Dodaj nagłówek pliku**. 

    ![Zrzut ekranu przedstawiający opcję Dodawanie nagłówka pliku.](media/add-file-header.png)

7. Aby zastosować nagłówek pliku do całego projektu lub rozwiązania, wybierz opcję **projekt** lub **rozwiązanie** w obszarze **Napraw wszystkie wystąpienia w:** .

8. Zostanie otwarte okno dialogowe **Popraw wszystkie wystąpienia** , w którym można wyświetlić podgląd zmian.

    ![Okno dialogowe Popraw wszystkie wystąpienia](media/file-header-preview-changes.png)

8. Wybierz pozycję **Zastosuj** , aby zastosować zmiany.

## <a name="see-also"></a>Zobacz też

- [Generowanie kodu](../code-generation-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)