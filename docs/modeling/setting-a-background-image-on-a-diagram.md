---
title: Ustawienie obrazu tła w diagramie
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c4b559b80613197dae62bc6246bd7ef1532d7071
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55941169"
---
# <a name="setting-a-background-image-on-a-diagram"></a>Ustawienie obrazu tła w diagramie
W Visual Studio Visualization i Modeling SDK należy określić obraz tła dla wygenerowanego projektanta przy użyciu niestandardowego kodu.

## <a name="setting-the-background-image"></a>Ustawienie obrazu tła

#### <a name="to-set-a-background-image-for-a-generated-designer"></a>Aby ustawić obraz tła dla wygenerowanego projektanta

1.  Skopiuj plik obrazu, który chcesz użyć jako tło diagramu do katalogu Dsl\Resources dla bieżącego projektu.

2.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy Dsl\Resources folder, wskaż **Dodaj**, a następnie kliknij przycisk **istniejący element**.

3.  W **Dodaj istniejący element** okno dialogowe, przejdź do folderu Dsl\Resources.

4.  W **pliki typu** kliknij **pliki obrazów**.

5.  Kliknij plik obrazu, który został skopiowany do katalogu, a następnie kliknij przycisk **Dodaj**.

6.  Kliknij prawym przyciskiem myszy Dsl, a następnie kliknij przycisk **właściwości** aby otworzyć okno właściwości projektu Dsl.

7.  Na **zasobów** kliknij pozycję **ten projekt nie zawiera domyślnego pliku zasobów. Kliknij tutaj, aby go utworzyć.**

8.  Dodaj plik obrazu do pliku zasobów przez przeciąganie obrazów z **Eksploratora rozwiązań** do okna zasobów.

9. Otwórz menu Plik, a następnie kliknij opcję, aby zapisać wprowadzone właściwości projektu.

10. Sprawdź, czy plik Dsl\Properties\Resources.resx istnieje i ma plik Resources.Designer.cs wczytywania.

11. Jeśli brakuje Resources.Designer.cs, kliknij plik Resources.resx w **Eksploratora rozwiązań**.

12. W oknie **Właściwości** ustaw właściwość `Custom Tool` na `ResXFileCodeGenerator`. 

13. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt Dsl, wskaż **Dodaj**i kliknij przycisk **nowy Folder**.

14. Nazwa folderu **niestandardowe**.

15. Kliknij prawym przyciskiem myszy folder niestandardowy, wskaż opcję **Dodaj**i kliknij przycisk **nowy element**.

16. W **Dodaj nowy element** dialogowym **szablony** kliknij **pliku z kodem**.

17. W **nazwa** wpisz `BackgroundImage.cs`i kliknij przycisk **Dodaj**.

18. Skopiuj następujący kod do pliku BackgroundImage.cs, dostosowując obszaru nazw, nazwa klasy diagramu i nazwę zasobu w pliku obrazu.

     Zastąp nazwę klasy częściowej diagram, który jest zdefiniowany w Dsl\GeneratedCode\Diagrams.cs "MyDiagramClass". Można także pobrać poprawną przestrzeń nazw z pliku Dsl\GeneratedCode\Diagrams.cs.

    ```csharp
    using System;
    using Microsoft.VisualStudio.Modeling.Diagrams;

    // Fix the namespace:
    namespace Fabrikam.MyLanguage
    {
      // Fix the Diagram Class name - get it from GeneratedCode\Diagram.cs

      public partial class Language29Diagram
      {
        protected override void InitializeInstanceResources()
        {
          // Fix the Resources namespace and the Image resource name:
          ImageField backgroundField = new ImageField("background",
              Fabrikam.MyLanguage.Properties.Resources.MyPicture);

          backgroundField.DefaultFocusable = false;
          backgroundField.DefaultSelectable = false;
          backgroundField.DefaultVisibility = true;
          backgroundField.DefaultUnscaled = false;

          shapeFields.Add(backgroundField);

          backgroundField.AnchoringBehavior
            .SetTopAnchor(AnchoringBehavior.Edge.Top, 0.01);
          backgroundField.AnchoringBehavior
            .SetLeftAnchor(AnchoringBehavior.Edge.Left, 0.01);
          backgroundField.AnchoringBehavior
            .SetRightAnchor(AnchoringBehavior.Edge.Right, 0.01);
          backgroundField.AnchoringBehavior
            .SetBottomAnchor(AnchoringBehavior.Edge.Bottom, 0.01);

          base.InitializeInstanceResources();
        }
      }
    }
    ```

     Aby uzyskać więcej informacji na temat Dostosowywanie modelu za pomocą kodu programu zobacz [nawigowanie i aktualizowanie modelu w kodzie programu](../modeling/navigating-and-updating-a-model-in-program-code.md).

## <a name="see-also"></a>Zobacz też

- [Definiowanie kształtów i łączników](../modeling/defining-shapes-and-connectors.md)
- [Dostosowywanie pól tekstowych i obrazu](../modeling/customizing-text-and-image-fields.md)
- [Nawigowanie i aktualizowanie modelu w kodzie programu](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Pisanie kodu pod kątem dostosowywania języka specyficznego dla domeny](../modeling/writing-code-to-customise-a-domain-specific-language.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
