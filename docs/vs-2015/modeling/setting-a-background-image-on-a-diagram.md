---
title: Ustawianie obrazu tła na diagramie | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: e334a24c-8521-4072-b50f-e59158dde145
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2b7d206852101a1d99a08eac710d88e93afe4a04
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671205"
---
# <a name="setting-a-background-image-on-a-diagram"></a>Ustawienie obrazu tła w diagramie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W programie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Wizualizacja i modelowanie SDK można ustawić obraz tła dla wygenerowanego projektanta przy użyciu kodu niestandardowego.

## <a name="setting-the-background-image"></a>Ustawianie obrazu tła

#### <a name="to-set-a-background-image-for-a-generated-designer"></a>Aby ustawić obraz tła dla wygenerowanego projektanta

1. Skopiuj plik obrazu, który ma być używany jako tło diagramu w katalogu Dsl\Resources dla bieżącego projektu.

2. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy folder Dsl\Resources, wskaż polecenie **Dodaj**, a następnie kliknij pozycję **istniejący element**.

3. W oknie dialogowym **Dodaj istniejący element** przejdź do folderu Dsl\Resources.

4. Na liście **Pliki typu** kliknij pozycję **pliki obrazów**.

5. Kliknij plik obrazu, który został skopiowany do katalogu, a następnie kliknij przycisk **Dodaj**.

6. Kliknij prawym przyciskiem myszy pozycję DSL, a następnie kliknij pozycję **Właściwości** , aby otworzyć właściwości projektu DSL.

7. Na karcie **zasoby** kliknij pozycję **ten projekt nie zawiera domyślnego pliku zasobów. Kliknij tutaj, aby go utworzyć.**

8. Dodaj plik obrazu do pliku zasobów, przeciągając obraz z **Eksplorator rozwiązań** do okna zasoby.

9. Otwórz menu plik, a następnie kliknij opcję, aby zapisać właściwości projektu.

10. Sprawdź, czy plik Dsl\Properties\Resources.resx istnieje i czy znajduje się w nim plik Resources.Designer.cs.

11. Jeśli brakuje Resources.Designer.cs, kliknij plik resources. resx w **Eksplorator rozwiązań**.

12. W oknie **Właściwości** Ustaw `Custom Tool` Właściwość na `ResXFileCodeGenerator` .

13. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt DSL, wskaż polecenie **Dodaj**, a następnie kliknij pozycję **Nowy folder**.

14. Nadaj nazwę folderowi **niestandardowemu**.

15. Kliknij prawym przyciskiem myszy folder niestandardowy, wskaż polecenie **Dodaj**i kliknij pozycję **nowy element**.

16. W oknie dialogowym **Dodaj nowy element** na liście **Szablony** kliknij pozycję **plik kodu**.

17. W polu **Nazwa** wpisz `BackgroundImage.cs` , a następnie kliknij przycisk **Dodaj**.

18. Skopiuj następujący kod do pliku BackgroundImage.cs, dostosowując przestrzeń nazw, nazwę klasy diagramu i nazwę zasobu pliku obrazu.

     Zastąp ciąg "MyDiagramClass" nazwą częściowej klasy diagramu, która jest zdefiniowana w Dsl\GeneratedCode\Diagrams.cs. Możesz również pobrać poprawną przestrzeń nazw z pliku Dsl\GeneratedCode\Diagrams.cs.

    ```
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

     Aby uzyskać więcej informacji na temat dostosowywania modelu przy użyciu kodu programu, zobacz [nawigowanie i aktualizowanie modelu w kodzie programu](../modeling/navigating-and-updating-a-model-in-program-code.md).

## <a name="see-also"></a>Zobacz też
 [Definiowanie kształtów i łączników](../modeling/defining-shapes-and-connectors.md) [Dostosowywanie pól tekstowych i obrazów](../modeling/customizing-text-and-image-fields.md) [nawigowanie i aktualizowanie modelu w kodzie programowym](../modeling/navigating-and-updating-a-model-in-program-code.md) [pisanie kodu w celu dostosowania języka specyficznego dla domeny](../modeling/writing-code-to-customise-a-domain-specific-language.md)
