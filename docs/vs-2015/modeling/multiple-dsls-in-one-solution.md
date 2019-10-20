---
title: Wiele językami DSL w jednym rozwiązaniu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 7e668620-6217-4e87-aea7-e9036776c8e4
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9a3b35e05108db879b365b9cafc39cacdf843397
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668555"
---
# <a name="multiple-dsls-in-one-solution"></a>Wiele języków DSL w jednym rozwiązaniu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W ramach jednego rozwiązania można spakować kilka językami DSL, aby zostały one zainstalowane razem.

 Do integracji wielu językami DSL można użyć kilku technik. Aby uzyskać więcej informacji, zobacz [integrowanie modeli za pomocą Visual Studio ModelBus](../modeling/integrating-models-by-using-visual-studio-modelbus.md) i [instrukcje: Dodawanie obsługi przeciągania i upuszczania](../modeling/how-to-add-a-drag-and-drop-handler.md) oraz [Dostosowywanie zachowania kopiowania](../modeling/customizing-copy-behavior.md).

### <a name="to-build-more-than-one-dsl-in-the-same-solution"></a>Aby skompilować więcej niż jeden DSL w tym samym rozwiązaniu

1. Utwórz co najmniej dwa rozwiązania DSL i projekt VSIX, a następnie Dodaj wszystkie projekty do jednego rozwiązania.

   - Aby utworzyć nowy projekt VSIX: w oknie dialogowym **Nowy projekt** wybierz pozycję **Wizualizacja C#** , **rozszerzalność**, **Projekt VSIX**.

   - Utwórz co najmniej dwa rozwiązania DSL w katalogu rozwiązania VSIX.

        Dla każdego DSL Otwórz nowe wystąpienie programu Visual Studio. Utwórz nowy DSL i określ ten sam folder rozwiązania jako rozwiązanie VSIX.

        Upewnij się, że tworzysz każde DSL z innym rozszerzeniem nazwy pliku.

   - Zmień nazwy projektów **DSL** i **DslPackage** tak, aby były różne. Na przykład: `Dsl1`, `DslPackage1`, `Dsl2` `DslPackage2`.

   - W każdym **DslPackage \* \ source.Extension.tt**zaktualizuj ten wiersz do prawidłowej nazwy projektu DSL:

        `string dslProjectName = "Dsl2";`

   - W rozwiązaniu VSIX Dodaj projekty DSL * i DslPackage \*.

        Możesz chcieć umieścić każdą parę w swoim własnym folderze rozwiązania.

2. Połącz manifesty VSIX językami DSL:

   1. Otwórz _YourVsixProject_ **\source.Extension.manifest**.

   2. Dla każdego DSL wybierz pozycję **Dodaj zawartość** i Dodaj:

       - `Dsl*` projekt jako **składnik MEF**

       - `DslPackage*` projekt jako **składnik MEF**

       - `DslPackage*` projekt jako **pakiet programu vs**

3. Skompiluj rozwiązanie.

   W rezultacie program VSIX zainstaluje oba językami DSL. Można je przetestować przy użyciu klawisza F5 lub wdrożyć _YourVsixProject_ **\bin\debug \\ \*. vsix**.

## <a name="see-also"></a>Zobacz też
 [Integrowanie modeli za pomocą programu Visual Studio ModelBus](../modeling/integrating-models-by-using-visual-studio-modelbus.md) [How to: Dodawanie obsługi przeciągania i upuszczania](../modeling/how-to-add-a-drag-and-drop-handler.md) [Dostosowywanie zachowania kopiowania](../modeling/customizing-copy-behavior.md)
