---
title: Wiele języków DSL w jednym rozwiązaniu
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8c894ce7466c253916794495649fa65d703e6d67
ms.sourcegitcommit: 489aca71046fb6e4aafd0a4509cd7dc149d707b1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2019
ms.locfileid: "58416152"
---
# <a name="multiple-dsls-in-one-solution"></a>Wiele języków DSL w jednym rozwiązaniu

Można spakować kilka języków DSL w ramach jednego rozwiązania, tak, aby zainstalować je ze sobą.

Kilka technik umożliwia integrowanie wiele języków DSL. Aby uzyskać więcej informacji, zobacz [integrowanie modeli za pomocą programu Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md) i [jak: Dodawanie obsługi przeciągania i upuszczania](../modeling/how-to-add-a-drag-and-drop-handler.md) i [Dostosowywanie zachowania dotyczącego kopiowania](../modeling/customizing-copy-behavior.md).

## <a name="build-more-than-one-dsl-in-the-same-solution"></a>Twórz więcej niż jednym języku DSL w tym samym rozwiązaniu

1. Utwórz nową **projekt VSIX** projektu.

2. W katalogu rozwiązania VSIX, należy utworzyć dwa lub więcej projektów języka DSL.

   - Dla każdego języka DSL Otwórz nowe wystąpienie programu Visual Studio. Utwórz nowy język DSL i określić ten sam folder rozwiązania jako rozwiązania VSIX.

   - Upewnij się, tworzenie każdego DSL z rozszerzeniem innej nazwy pliku.

   - Zmiany nazw **Dsl** i **DslPackage** projektów, tak aby były różne. Na przykład: `Dsl1`, `DslPackage1`, `Dsl2`, `DslPackage2`.

   - W każdym **DslPackage\*\source.extension.tt**, zaktualizować ten wiersz do poprawnej nazwy projektu Dsl:

      `string dslProjectName = "Dsl2";`

   - W przypadku rozwiązania VSIX Dodaj Dsl * i DslPackage\* projektów. Warto umieścić każdej pary w jego własnym folderze rozwiązania.

2. Łączenie języków DSL manifesty VSIX:

   1.  Otwórz _YourVsixProject_**\source.extension.manifest**.

   2.  Dla każdego języka DSL, wybierz **Dodaj zawartość** i Dodaj:

       -   `Dsl*` projekt jako **składnik MEF**

       -   `DslPackage*` projekt jako **składnik MEF**

       -   `DslPackage*` projekt jako **pakietu programu VS**

3. Skompiluj rozwiązanie.

   Wynikowy VSIX zainstaluje zarówno językami DSL. Można je przetestować, naciskając klawisz F5 lub wdrożyć _YourVsixProject_**\bin\Debug\\\*.vsix**.

## <a name="see-also"></a>Zobacz także

- [Integrowanie modeli za pomocą Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md)
- [Instrukcje: Dodawanie obsługi przeciągania i upuszczania](../modeling/how-to-add-a-drag-and-drop-handler.md)
- [Dostosowywanie zachowania dotyczącego kopiowania](../modeling/customizing-copy-behavior.md)