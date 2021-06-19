---
title: Dodawanie niestandardowej walidacji architektury do diagramów zależności
description: Zawiera informacje na temat dodawania niestandardowej weryfikacji architektury do diagramów zależności.
ms.date: 11/04/2016
ms.topic: how-to
titleSuffix: ''
helpviewer_keywords:
- dependency diagrams, adding custom validation
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.custom: SEO-VS-2020
ms.workload:
- multiple
ms.openlocfilehash: cc00f86bafebd14177400ffa0ee596a733e9fb28
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112384632"
---
# <a name="add-custom-architecture-validation-to-dependency-diagrams"></a>Dodawanie niestandardowej walidacji architektury do diagramów zależności

W Visual Studio użytkownicy mogą zweryfikować kod źródłowy w projekcie względem modelu warstwy, aby sprawdzić, czy kod źródłowy jest zgodny z zależnościami diagramu zależności. Istnieje standardowy algorytm weryfikacji, ale można zdefiniować własne rozszerzenia weryfikacji.

Gdy użytkownik wybierze  polecenie Weryfikuj architekturę na diagramie zależności, wywoływana jest standardowa metoda walidacji, po której następuje wszystkie zainstalowane rozszerzenia weryfikacji.

> [!NOTE]
> Na diagramie zależności głównym celem walidacji jest porównanie diagramu z kodem programu w innych częściach rozwiązania.

Rozszerzenie weryfikacji warstwy można spakować do rozszerzenia Visual Studio Integration Extension (VSIX), które można dystrybuować do innych Visual Studio użytkowników. Możesz samodzielnie umieścić swój validator w vsix lub połączyć go w tym samym VSIX co inne rozszerzenia. Kod sprawdzania ważności należy napisać we własnym projekcie Visual Studio, a nie w tym samym projekcie co inne rozszerzenia.

> [!WARNING]
> Po utworzeniu projektu weryfikacji [](#example) skopiuj przykładowy kod na końcu tego tematu, a następnie edytuj go do własnych potrzeb.

## <a name="requirements"></a>Wymagania

Zobacz [Wymagania.](../modeling/extend-layer-diagrams.md#requirements)

## <a name="defining-a-layer-validator-in-a-new-vsix"></a>Definiowanie validatora warstwy w nowym VSIX

Najszybszą metodą tworzenia validatora jest użycie szablonu projektu. Dzięki temu kod i manifest VSIX są umieszczane w tym samym projekcie.

### <a name="to-define-an-extension-by-using-a-project-template"></a>Aby zdefiniować rozszerzenie przy użyciu szablonu projektu

1. Utwórz nowy projekt **rozszerzenia walidacji projektanta** warstwy.

    Szablon tworzy projekt, który zawiera mały przykład.

   > [!WARNING]
   > Aby szablon działał prawidłowo:
   >
   > - Edytuj wywołania funkcji `LogValidationError` , aby usunąć opcjonalne argumenty i `errorSourceNodes` `errorTargetNodes` .
   > - Jeśli używasz właściwości niestandardowych, zastosuj aktualizację wymienioną w tece [Dodawanie właściwości niestandardowych do diagramów zależności.](../modeling/add-custom-properties-to-layer-diagrams.md)

2. Edytuj kod, aby zdefiniować weryfikację. Aby uzyskać więcej informacji, zobacz [Walidacja programowania](#programming).

3. Aby przetestować rozszerzenie, zobacz [Debugowanie walidacji warstwy](#debugging).

   > [!NOTE]
   > Metoda zostanie wywołana tylko w określonych okolicznościach, a punkty przerwania nie będą działać automatycznie. Aby uzyskać więcej informacji, zobacz [Debugowanie walidacji warstwy](#debugging).

::: moniker range="vs-2017"

4. Aby zainstalować rozszerzenie w głównym wystąpieniu Visual Studio lub na innym komputerze, znajdź plik *vsix* w *katalogu bin.* Skopiuj go na komputer, na którym chcesz go zainstalować, a następnie kliknij go dwukrotnie. Aby go odinstalować, **wybierz pozycję Rozszerzenia i aktualizacje** w menu Narzędzia. 

::: moniker-end

::: moniker range=">=vs-2019"

4. Aby zainstalować rozszerzenie w głównym wystąpieniu Visual Studio lub na innym komputerze, znajdź plik *vsix* w *katalogu bin.* Skopiuj go na komputer, na którym chcesz go zainstalować, a następnie kliknij go dwukrotnie. Aby go odinstalować, wybierz **pozycję Zarządzaj rozszerzeniami** w menu **Rozszerzenia.**

::: moniker-end

## <a name="adding-a-layer-validator-to-a-separate-vsix"></a>Dodawanie sprawdzania ważności warstwy do oddzielnego vsix

Jeśli chcesz utworzyć jeden vsix, który zawiera moduły sprawdzania, polecenia i inne rozszerzenia warstwy, zalecamy utworzenie jednego projektu w celu zdefiniowania vsix i oddzielnych projektów dla programów obsługi.

### <a name="to-add-layer-validation-to-a-separate-vsix"></a>Aby dodać walidację warstwy do oddzielnego vsix

1. Utwórz nowy projekt **Biblioteka** klas. Ten projekt będzie zawierać klasę walidacji warstwy.

2. Znajdź lub utwórz projekt **VSIX** w swoim rozwiązaniu. Projekt VSIX zawiera plik o nazwie **source.extension.vsixmanifest.**

3. W **Eksplorator rozwiązań** menu prawym przyciskiem myszy projektu VSIX wybierz pozycję **Ustaw jako projekt startowy.**

4. W **pliku source.extension.vsixmanifest** w obszarze **Assets** dodaj projekt weryfikacji warstwy jako składnik MEF:

    1. Wybierz pozycję **Nowy**.

    2. W **oknie dialogowym Dodawanie nowego** zasobu ustaw:

         **Typ**  =  **Microsoft.VisualStudio.MefComponent**

         **Źródło**  =  **Projekt w bieżącym rozwiązaniu**

         **Projekt**  =  *projekt programu sprawdzania ważności*

5. Należy również dodać go jako weryfikację warstwy:

    1. Wybierz pozycję **Nowy**.

    2. W **oknie dialogowym Dodawanie nowego** zasobu ustaw:

         **Typ**  =  **Microsoft.VisualStudio.ArchitectureTools.Layer.Validator**. Nie jest to jedna z opcji na liście rozwijanej. Należy wprowadzić go z klawiatury.

         **Źródło**  =  **Projekt w bieżącym rozwiązaniu**

         **Projekt**  =  *projekt programu sprawdzania ważności*

6. Wróć do projektu weryfikacji warstwy i dodaj następujące odwołania do projektu:

    |**Odwołanie**|**Co to umożliwia**|
    |-|-|
    |Microsoft.VisualStudio.GraphModel.dll|Odczytywanie wykresu architektury|
    |Microsoft.VisualStudio.ArchitectureTools.Extensibility.CodeSchema.dll|Odczytywanie kodu DOM skojarzonego z warstwami|
    |Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.dll|Odczytywanie modelu warstwy|
    |Microsoft.VisualStudio.ArchitectureTools.Extensibility|Odczytywanie i aktualizowanie kształtów i diagramów.|
    |System.componentmodel.composition|Definiowanie składnika weryfikacji przy użyciu Managed Extensibility Framework (MEF)|
    |Microsoft.VisualStudio.Modeling.Sdk. [wersja]|Definiowanie rozszerzeń modelowania|

7. Skopiuj przykładowy kod na końcu tego tematu do pliku klasy w projekcie biblioteki weryfikacji, aby zawierał kod weryfikacji. Aby uzyskać więcej informacji, zobacz [Walidacja programowania](#programming).

8. Aby przetestować rozszerzenie, zobacz [Debugowanie walidacji warstwy](#debugging).

    > [!NOTE]
    > Metoda zostanie wywołana tylko w określonych okolicznościach, a punkty przerwania nie będą działać automatycznie. Aby uzyskać więcej informacji, zobacz [Debugowanie walidacji warstwy](#debugging).

9. Aby zainstalować vsIX w głównym wystąpieniu programu Visual Studio lub na innym komputerze, znajdź plik **vsix** w katalogu **bin** projektu VSIX. Skopiuj go na komputer, na którym chcesz zainstalować vsix. Kliknij dwukrotnie plik VSIX w Eksplorator Windows.

## <a name="programming-validation"></a><a name="programming"></a> Walidacja programowania

Aby zdefiniować rozszerzenie walidacji warstwy, należy zdefiniować klasę o następujących cechach:

- Ogólna forma deklaracji jest następująca:

  ```csharp
  using System.ComponentModel.Composition;
  using Microsoft.VisualStudio.ArchitectureTools.Extensibility.CodeSchema;
  using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;
  using Microsoft.VisualStudio.GraphModel;
  ...
   [Export(typeof(IValidateArchitectureExtension))]
    public partial class Validator1Extension :
                    IValidateArchitectureExtension
    {
      public void ValidateArchitecture(Graph graph)
      {
         GraphSchema schema = graph.DocumentSchema;
        ...
    } }
  ```

- Gdy odkryjesz błąd, możesz zgłosić go przy użyciu funkcji `LogValidationError()` .

  > [!WARNING]
  > Nie używaj opcjonalnych parametrów polecenia `LogValidationError` .

Gdy użytkownik wywołuje polecenie menu **Weryfikuj** architekturę, system środowiska uruchomieniowego warstwy analizuje warstwy i ich artefakty w celu uzyskania grafu. Wykres ma cztery części:

- Modele warstw rozwiązania Visual Studio, które są reprezentowane jako węzły i linki na wykresie.

- Kod, elementy projektu i inne artefakty zdefiniowane w rozwiązaniu i reprezentowane jako węzły oraz linki reprezentujące zależności wykryte w procesie analizy.

- Łącza z węzłów warstwy do węzłów artefaktów kodu.

- Węzły reprezentujące błędy wykryte przez validator.

Po skonstruowaniu grafu wywoływana jest standardowa metoda walidacji. Po zakończeniu wszystkie zainstalowane metody weryfikacji rozszerzenia są wywoływane w nieokreślonym porządku. Graf jest przekazywany do każdej `ValidateArchitecture` metody, która może przeskanować graf i zgłosić wszelkie znalezione błędy.

> [!NOTE]
> Nie jest to proces weryfikacji, który może być używany w językach specyficznych dla domeny.

Metody walidacji nie powinny zmieniać modelu warstwy ani kodu, który jest weryfikowany.

Model grafu jest zdefiniowany w <xref:Microsoft.VisualStudio.GraphModel> . Jej główne klasy to <xref:Microsoft.VisualStudio.GraphModel.GraphNode> i <xref:Microsoft.VisualStudio.GraphModel.GraphLink> .

Każdy węzeł i każde łącze ma co najmniej jedną kategorię, która określa typ elementu lub relacji, który reprezentuje. Węzły typowego grafu mają następujące kategorie:

- Dsl.LayerModel

- Dsl.Layer

- Dsl.Reference

- CodeSchema_Type

- CodeSchema_Namespace

- CodeSchema_Type

- CodeSchema_Method

- CodeSchema_Field

- CodeSchema_Property

Linki z warstw do elementów w kodzie mają kategorię "Reprezentuje".

## <a name="debugging-validation"></a><a name="debugging"></a> Walidacja debugowania

Aby debugować rozszerzenie walidacji warstwy, naciśnij klawisze CTRL+F5. Zostanie otwarte eksperymentalne wystąpienie Visual Studio. W tym przypadku otwórz lub utwórz model warstwy. Ten model musi być skojarzony z kodem i musi mieć co najmniej jedną zależność.

### <a name="test-with-a-solution-that-contains-dependencies"></a>Testowanie za pomocą rozwiązania zawierającego zależności

Walidacja nie jest wykonywana, chyba że istnieją następujące cechy:

- Diagram zależności zawiera co najmniej jeden link zależności.

- Istnieją warstwy w modelu, które są skojarzone z elementami kodu.

Przy pierwszym uruchomieniu eksperymentalnego wystąpienia klasy Visual Studio do testowania rozszerzenia weryfikacji otwórz lub utwórz rozwiązanie o tych cechach.

### <a name="run-clean-solution-before-validate-architecture"></a>Uruchamianie czystego rozwiązania przed weryfikacją architektury

Za każdym razem, gdy aktualizujesz kod weryfikacyjny, użyj polecenia **Clean Solution** (Wyczyść rozwiązanie) w menu **Build** (Kompilacja) w eksperymentalnym rozwiązaniu przed przetestowaniem polecenia Validate (Weryfikuj). Jest to konieczne, ponieważ wyniki weryfikacji są buforowane. Jeśli nie zaktualizowano diagramu zależności testu lub jego kodu, metody walidacji nie zostaną wykonane.

### <a name="launch-the-debugger-explicitly"></a>Jawne uruchamianie debugera

Walidacja jest uruchamiana w osobnym procesie. W związku z tym punkty przerwania w metodzie walidacji nie zostaną wyzwolone. Należy jawnie dołączyć debuger do procesu po rozpoczęcia walidacji.

Aby dołączyć debuger do procesu walidacji, wstaw wywołanie metody na `System.Diagnostics.Debugger.Launch()` początku metody walidacji. Gdy zostanie wyświetlone okno dialogowe debugowania, wybierz główne wystąpienie Visual Studio.

Alternatywnie możesz wstawić wywołanie metody `System.Windows.Forms.MessageBox.Show()` . Gdy pojawi się okno komunikatu, przejdź do głównego wystąpienia usługi Visual Studio a następnie w **menu** Debugowanie kliknij pozycję Dołącz **do procesu.** Wybierz proces o nazwie **Graphcmd.exe**.

Zawsze uruchamiaj wystąpienie eksperymentalne, naciskając klawisze CTRL+F5 **(Rozpocznij bez debugowania).**

### <a name="deploying-a-validation-extension"></a>Wdrażanie rozszerzenia walidacji

Aby zainstalować rozszerzenie weryfikacji na komputerze, na którym jest zainstalowana odpowiednia wersja Visual Studio, otwórz plik VSIX na komputerze docelowym.

## <a name="example-code"></a><a name="example"></a> Przykładowy kod

```csharp
using System;
using System.ComponentModel.Composition;
using System.Globalization;
using System.Linq;
using System.Text.RegularExpressions;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.CodeSchema;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;
using Microsoft.VisualStudio.GraphModel;

namespace Validator3
{
    [Export(typeof(IValidateArchitectureExtension))]
    public partial class Validator3Extension : IValidateArchitectureExtension
    {
        /// <summary>
        /// Validate the architecture
        /// </summary>
        /// <param name="graph">The graph</param>
        public void ValidateArchitecture(Graph graph)
        {
            if (graph == null) throw new ArgumentNullException("graph");

            // Uncomment the line below to debug this extension during validation
            // System.Windows.Forms.MessageBox.Show("Attach 2 to GraphCmd.exe with process id " + System.Diagnostics.Process.GetCurrentProcess().Id);

            // Get all layers on the diagram
            foreach (GraphNode layer in graph.Nodes.GetByCategory("Dsl.Layer"))
            {
                System.Threading.Thread.Sleep(100);
                // Get the required regex property from the layer node
                string regexPattern = "^[a-zA-Z]+$"; //layer[customPropertyCategory] as string;
                if (!string.IsNullOrEmpty(regexPattern))
                {
                    Regex regEx = new Regex(regexPattern);

                    // Get all referenced types in this layer including those from nested layers so each
                    // type is validated against all containing layer constraints.
                    foreach (GraphNode containedType in layer.FindDescendants().Where(node => node.HasCategory("CodeSchema_Type")))
                    {
                        // Check the type name against the required regex
                        CodeGraphNodeIdBuilder builder = new CodeGraphNodeIdBuilder(containedType.Id, graph);
                        string typeName = builder.Type.Name;
                        if (!regEx.IsMatch(typeName))
                        {
                            // Log an error
                            string message = string.Format(CultureInfo.CurrentCulture, Resources.InvalidTypeNameMessage, typeName);
                            this.LogValidationError(graph, typeName + "TypeNameError", message, GraphErrorLevel.Error, layer);
                        }
                    }
                }

            }

        }
    }
}
```

## <a name="see-also"></a>Zobacz też

- [Rozszerzanie diagramów zależności](../modeling/extend-layer-diagrams.md)
