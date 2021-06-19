---
title: Ustawienie obrazu tła w diagramie
description: Dowiedz się, że w Visual Studio SDK wizualizacji i modelowania możesz ustawić obraz tła dla wygenerowanego projektanta przy użyciu kodu niestandardowego.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9304117932b92408f12a23747253de66dfd767d1
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385672"
---
# <a name="setting-a-background-image-on-a-diagram"></a>Ustawienie obrazu tła w diagramie
W Visual Studio SDK wizualizacji i modelowania można ustawić obraz tła dla wygenerowanego projektanta przy użyciu kodu niestandardowego.

## <a name="setting-the-background-image"></a>Ustawianie obrazu tła

#### <a name="to-set-a-background-image-for-a-generated-designer"></a>Aby ustawić obraz tła dla wygenerowanego projektanta

1. Skopiuj plik obrazu, którego chcesz użyć jako tła diagramu, do katalogu Dsl\Resources bieżącego projektu.

2. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy folder Dsl\Resources, wskaż polecenie **Dodaj**, a następnie kliknij pozycję **Istniejący element**.

3. W **oknie dialogowym Dodawanie** istniejącego elementu przejdź do folderu Dsl\Resources.

4. Na liście **Pliki typu kliknij** pozycję Pliki **obrazów.**

5. Kliknij plik obrazu skopiowany do katalogu, a następnie kliknij przycisk **Dodaj**.

6. Kliknij prawym przyciskiem myszy dsl, a następnie kliknij **przycisk właściwości,** aby otworzyć właściwości projektu Dsl.

7. Na karcie **Zasoby** kliknij pozycję **Ten projekt nie zawiera domyślnego pliku zasobów. Kliknij tutaj, aby go utworzyć.**

8. Dodaj plik obrazu do pliku zasobów, przeciągając obraz **z Eksplorator rozwiązań** do okna zasobów.

9. Otwórz menu Plik i kliknij opcję , aby zapisać właściwości projektu.

10. Sprawdź, czy plik Dsl\Properties\Resources.resx istnieje i zawiera plik Resources.Designer.cs.

11. Jeśli brakuje pliku Resources.Designer.cs, kliknij plik Resources.resx w **Eksplorator rozwiązań**.

12. W **oknie** Właściwości ustaw właściwość `Custom Tool` na `ResXFileCodeGenerator` wartość .

13. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy projekt Dsl, wskaż polecenie **Dodaj** i kliknij pozycję **Nowy folder**.

14. Nadaj folderowi **nazwę Niestandardowy**.

15. Kliknij prawym przyciskiem myszy folder Niestandardowy, wskaż polecenie **Dodaj** i kliknij **pozycję Nowy element.**

16. W **oknie dialogowym** Dodawanie nowego elementu na liście **Szablony** kliknij pozycję **Plik kodu**.

17. W polu **Nazwa** wpisz `BackgroundImage.cs` , a następnie kliknij przycisk **Dodaj**.

18. Skopiuj następujący kod do pliku BackgroundImage.cs, dostosowując przestrzeń nazw, nazwę klasy diagramu i nazwę zasobu pliku obrazu.

     Zastąp "MyDiagramClass" nazwą klasy częściowej diagramu zdefiniowanej w pliku Dsl\GeneratedCode\Diagrams.cs. Poprawną przestrzeń nazw można również pobrać z pliku Dsl\GeneratedCode\Diagrams.cs.

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

     Aby uzyskać więcej informacji na temat dostosowywania modelu za pomocą kodu programu, zobacz [Navigating and Updating a Model in Program Code](../modeling/navigating-and-updating-a-model-in-program-code.md)(Nawigowanie i aktualizowanie modelu w kodzie programu).

## <a name="see-also"></a>Zobacz też

- [Definiowanie kształtów i łączników](../modeling/defining-shapes-and-connectors.md)
- [Dostosowywanie pól tekstowych i obrazu](../modeling/customizing-text-and-image-fields.md)
- [Nawigowanie i aktualizowanie modelu w kodzie programu](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Pisanie kodu pod kątem dostosowywania języka specyficznego dla domeny](../modeling/writing-code-to-customise-a-domain-specific-language.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
