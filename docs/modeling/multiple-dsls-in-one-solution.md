---
title: Wiele języków DSL w jednym rozwiązaniu
description: Dowiedz się, jak utworzyć pakiet kilku języków specyficznych dla domeny (DSL) w ramach jednego rozwiązania, aby zostały one zainstalowane razem.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 11baf6439062e28c7361e2fabb4dea4a3430f237
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390922"
---
# <a name="multiple-dsls-in-one-solution"></a>Wiele języków DSL w jednym rozwiązaniu

W ramach jednego rozwiązania można spakować kilka plików DSL, aby zostały one zainstalowane razem.

Można użyć kilku technik integrowania wielu plików DSL. Aby uzyskać więcej informacji, zobacz [Integrating Models by using Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md) (Integrowanie modeli przy użyciu magistrali modeli) i [How to: Add a Drag-and-Drop Handler](../modeling/how-to-add-a-drag-and-drop-handler.md) (Jak dodać obsługę przeciągania i upuszczania) i Customizing Copy Behavior (Dostosowywanie [zachowania kopiowania).](../modeling/customizing-copy-behavior.md)

## <a name="build-more-than-one-dsl-in-the-same-solution"></a>Tworzenie więcej niż jednego DSL w tym samym rozwiązaniu

1. Utwórz nowy projekt **VSIX.**

2. Utwórz co najmniej dwa projekty DSL w katalogu rozwiązania VSIX.

   - Dla każdego DSL otwórz nowe wystąpienie Visual Studio. Utwórz nowy dsl i określ ten sam folder rozwiązania co rozwiązanie VSIX.

   - Upewnij się, że tworzysz każdy DSL z innym rozszerzeniem nazwy pliku.

   - Zmień nazwy projektów **Dsl** i **DslPackage,** aby były różne. Na przykład: `Dsl1` , `DslPackage1` , , `Dsl2` `DslPackage2` .

   - W każdym **pliku DslPackage \* \source.extension.tt** zaktualizuj ten wiersz do poprawnej nazwy projektu Dsl:

      `string dslProjectName = "Dsl2";`

   - W rozwiązaniu VSIX dodaj projekty Dsl* i \* DslPackage. Możesz umieścić każdą parę w swoim folderze rozwiązania.

2. Połącz manifesty VSIX plików DSL:

   1. Otwórz _plik YourVsixProject_**\source.extension.manifest.**

   2. Dla każdego DSL wybierz pozycję **Dodaj zawartość** i dodaj:

       - `Dsl*` project as a MEF Component (projekt **jako składnik MEF)**

       - `DslPackage*` project as a MEF Component (projekt **jako składnik MEF)**

       - `DslPackage*` project as a VS Package (projekt **jako pakiet programu VS)**

3. Skompiluj rozwiązanie.

   Wynikowy plik VSIX zainstaluje oba pliki DSL. Można je przetestować przy użyciu klawisza F5 lub wdrożyć _plik YourVsixProject_**\bin\Debug \\ \* .vsix.**

## <a name="see-also"></a>Zobacz też

- [Integrowanie modeli za pomocą Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md)
- [Instrukcje: Dodawanie obsługi przeciągania i upuszczania](../modeling/how-to-add-a-drag-and-drop-handler.md)
- [Dostosowywanie zachowania dotyczącego kopiowania](../modeling/customizing-copy-behavior.md)