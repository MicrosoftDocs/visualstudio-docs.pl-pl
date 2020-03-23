---
title: Zmiana nazwy refaktorycyjnie
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.rename
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 4dbccd4732f56d671fd74f59916885ea338136f8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75565464"
---
# <a name="rename-a-code-symbol-refactoring"></a>Zmienianie nazwy symbolu kodu refaktoryzacji

Ten refaktoryzator ma zastosowanie do:

- C#

- Visual Basic

**Co:** Umożliwia zmianę nazwy identyfikatorów symboli kodu, takich jak pola, zmienne lokalne, metody, przestrzenie nazw, właściwości i typy.

**Kiedy:** Chcesz bezpiecznie zmienić nazwę czegoś bez konieczności znajdowania wszystkich wystąpień i kopiować/wklejać nową nazwę.

**Dlaczego?** Kopiowanie i wklejanie nowej nazwy w całym projekcie prawdopodobnie spowodowałoby błędy. To narzędzie refaktoryzacji będzie dokładnie wykonać akcję zmiany nazwy.

## <a name="how-to"></a>Porady

1. Zaznacz lub umieść kursor tekstowy wewnątrz elementu, który ma zostać zmieniony:

   - C#:

       ![Wyróżniony kod - C #](media/rename-highlight-cs.png)

   - Visual Basic:

       ![Wyróżniony kod — Visual Basic](media/rename-highlight-vb.png)

2. Następnie wykonaj jedną z następujących czynności:

   - **Klawiatura**
      - Naciśnij **klawisze Ctrl+R**, a następnie **klawisze Ctrl+R**. (Pamiętaj, że skrót klawiaturowy może się różnić w zależności od wybranego profilu).
   - **Mysz**
      - Wybierz **pozycję Edytuj > refaktoryzatora > zmień nazwę**.
      - Kliknij prawym przyciskiem myszy kod i wybierz polecenie **Zmień nazwę**.

3. Zmień nazwę elementu po prostu wpisując nową nazwę.

   - C#:

      ![Zmienianie nazwy animacji — C #](media/rename-animated-cs.gif)

   - Visual Basic:

      ![Zmiana nazwy - VB](media/rename-rename-vb.png)

   > [!TIP]
   > Można również zaktualizować komentarze i inne ciągi, aby użyć tej nowej nazwy, a także [wyświetlić podgląd zmian](../../ide/preview-changes.md) przed zapisaniem, używając pól wyboru w polu **Zmień nazwę,** które pojawia się w prawym górnym rogu edytora.

4. Gdy ze zmiany będziesz zadowolony, wybierz przycisk **Zastosuj** lub naciśnij klawisz **Enter,** a zmiany zostaną zatwierdzone.

## <a name="remarks"></a>Uwagi

- Począwszy od programu Visual Studio 2019 w wersji 16.3, po zmianie nazwy typu, który pasuje do nazwy pliku, w którym się znajduje, zostanie wyświetlenie pola wyboru, które umożliwia zmianę nazwy pliku w tym samym czasie. Ta opcja jest wyświetlana po zmianie nazwy klasy, interfejsu lub wyliczenia. Ta opcja nie jest obsługiwana dla typów częściowych z wieloma definicjami.

   ![Zmienianie nazwy animacji za pomocą pliku — C #](media/rename-with-file-animated-cs.gif)

- Jeśli używasz nazwy, która już istnieje, która może spowodować konflikt, pole **Zmień nazwę** wyświetli ostrzeżenie.

   ![Zmień nazwę konfliktu](media/rename-conflict-cs.png)

- Innym sposobem zmiany nazwy symbolu jest zmiana jego nazwy w edytorze. Następnie, z kursorem w nazwie symbolu, naciśnij klawisz **Ctrl**+**.** lub po prostu rozwiń menu ikon żarówki, które się pojawi i wybierz **Zmień nazwę \<starej nazwy> na \<nową nazwę>**.

## <a name="see-also"></a>Zobacz też

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)
