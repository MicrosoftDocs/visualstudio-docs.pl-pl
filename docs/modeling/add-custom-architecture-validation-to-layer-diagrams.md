---
title: Dodawanie niestandardowej walidacji architektury do diagramów zależności
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams, adding custom validation
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7e1d0a0cd2b82c16871e157e6f78c766895c34b3
ms.sourcegitcommit: 489aca71046fb6e4aafd0a4509cd7dc149d707b1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2019
ms.locfileid: "58415047"
---
# <a name="add-custom-architecture-validation-to-dependency-diagrams"></a>Dodawanie niestandardowej walidacji architektury do diagramów zależności

W programie Visual Studio użytkownicy mogą sprawdzić poprawność kodu źródłowego w projekcie względem modelu warstwy, aby mogli zweryfikować, że kod źródłowy odpowiada zależnościom na diagramie zależności. Istnieje algorytm standardowego sprawdzania poprawności, ale można zdefiniować własne rozszerzenia sprawdzania poprawności.

Gdy użytkownik wybierze **sprawdzanie poprawności architektury** polecenie diagram zależności, wywoływana jest standardowa metoda sprawdzania poprawności, następuje wszystkie rozszerzenia sprawdzania poprawności, które zostały zainstalowane.

> [!NOTE]
> Na diagramie zależności głównym celem sprawdzania poprawności jest porównanie diagramu z kodem programu w innych częściach rozwiązania.

Można spakować swoje rozszerzenie sprawdzania poprawności warstwy do Visual Studio Integration rozszerzenie (VSIX), który można rozdystrybuować innym użytkownikom programu Visual Studio. Teraz można umieścić swój moduł w VSIX przez siebie lub połączyć go w tym samym VSIX jako inne rozszerzenia. Należy wpisać kod modułu sprawdzania poprawności we własnym projekcie programu Visual Studio, a nie w tym samym projekcie jako inne rozszerzenia.

> [!WARNING]
> Po utworzeniu projektu sprawdzania poprawności, należy skopiować [przykładowy kod](#example) na końcu tego tematu, a następnie Edytuj, że do własnych potrzeb.

## <a name="requirements"></a>Wymagania

Zobacz [wymagania](../modeling/extend-layer-diagrams.md#prereqs).

## <a name="defining-a-layer-validator-in-a-new-vsix"></a>Definiowanie Walidatora warstwy w nowym VSIX

Najszybszą metodą tworzenia modułu sprawdzania poprawności jest użycie szablonu projektu. Te umieszcza kod i manifestu VSIX w tym samym projekcie.

### <a name="to-define-an-extension-by-using-a-project-template"></a>Aby zdefiniować rozszerzenie przy użyciu szablonu projektu

1. Utwórz nową **rozszerzenie sprawdzania poprawności projektanta warstwy** projektu.

    Ten szablon tworzy projekt zawierający krótki przykład.

   > [!WARNING]
   > Aby szablon działał prawidłowo:
   >
   > - Edytuj wywołania `LogValidationError` Aby usunąć opcjonalne argumenty `errorSourceNodes` i `errorTargetNodes`.
   > - Jeśli używasz właściwości niestandardowych, Zastosuj aktualizacje wymienione w [Dodawanie właściwości niestandardowych do diagramów zależności](../modeling/add-custom-properties-to-layer-diagrams.md).

2. Edytowanie kodu w celu zdefiniowania walidacji. Aby uzyskać więcej informacji, zobacz [programowanie walidacji](#programming).

3. Aby przetestować rozszerzenie, zobacz [debugowanie walidacji warstwowej](#debugging).

   > [!NOTE]
   > Metoda zostanie wywołana tylko w szczególnych okolicznościach, a punkty przerwania nie będą działać automatycznie. Aby uzyskać więcej informacji, zobacz [debugowanie walidacji warstwowej](#debugging).

::: moniker range="vs-2017"

4. Aby zainstalować rozszerzenie w głównym wystąpieniu programu Visual Studio lub na innym komputerze, należy znaleźć *.vsix* w pliku *bin* katalogu. Skopiuj go na komputerze, na którym chcesz go zainstalować i kliknij go dwukrotnie. Aby odinstalować go, wybierz opcję **rozszerzenia i aktualizacje** na **narzędzia** menu.

::: moniker-end

::: moniker range=">=vs-2019"

4. Aby zainstalować rozszerzenie w głównym wystąpieniu programu Visual Studio lub na innym komputerze, należy znaleźć *.vsix* w pliku *bin* katalogu. Skopiuj go na komputerze, na którym chcesz go zainstalować i kliknij go dwukrotnie. Aby odinstalować go, wybierz opcję **Zarządzaj rozszerzeniami** na **rozszerzenia** menu.

::: moniker-end

## <a name="adding-a-layer-validator-to-a-separate-vsix"></a>Dodawanie warstwowego modułu Walidującego do oddzielnego VSIX

Jeśli chcesz utworzyć jeden VSIX zawierający moduły sprawdzania warstwy, polecenia oraz inne rozszerzenia, zaleca się utworzenie jednego projektu do definiowania VSIX i oddzielnych projektów dla programów obsługi.

### <a name="to-add-layer-validation-to-a-separate-vsix"></a>Aby dodać sprawdzanie poprawności warstwy do oddzielnego VSIX

1. Utwórz nową **biblioteki klas** projektu. Projekt ten będzie zawierać klasy warstwy sprawdzania poprawności.

2. Znajdowanie lub tworzenie **projekt VSIX** w rozwiązaniu. Projekt VSIX zawiera plik o nazwie **source.extension.vsixmanifest**.

3. W **Eksploratora rozwiązań**, w menu kliknij prawym przyciskiem myszy projekt VSIX, wybierz **Ustaw jako projekt startowy**.

4. W **source.extension.vsixmanifest**w obszarze **zasoby**, Dodaj projekt sprawdzania poprawności warstwy jako składnik MEF:

    1.  Wybierz **nowe**.

    2.  W **Dodaj nowy zasób** okno dialogowe, zestaw:

         **Type** = **Microsoft.VisualStudio.MefComponent**

         **Źródło** = **projekt w bieżącym rozwiązaniu**

         **Projekt** = *projektu modułu sprawdzania poprawności*

5. Należy także dodać go jako sprawdzanie poprawności warstwy:

    1.  Wybierz **nowe**.

    2.  W **Dodaj nowy zasób** okno dialogowe, zestaw:

         **Type** = **Microsoft.VisualStudio.ArchitectureTools.Layer.Validator**. Nie jest jedną z opcji na liście rozwijanej. Należy wprowadzić je przy użyciu klawiatury.

         **Źródło** = **projekt w bieżącym rozwiązaniu**

         **Projekt** = *projektu modułu sprawdzania poprawności*

6. Wróć do projektu warstwy sprawdzania poprawności i dodaj następujące odwołania do projektu:

    |**Dokumentacja**|**Co to pozwala zrobić**|
    |-|-|
    |Microsoft.VisualStudio.GraphModel.dll|Odczytaj wykres architektury|
    |Microsoft.VisualStudio.ArchitectureTools.Extensibility.CodeSchema.dll|Odczytać kod DOM skojarzony z warstwami|
    |Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.dll|Przeczytaj warstwy modelu|
    |Microsoft.VisualStudio.ArchitectureTools.Extensibility|Przeczytaj i Aktualizuj kształty i diagramy.|
    |System.ComponentModel.Composition|Zdefiniuj składnik walidacji za pomocą Managed Extensibility Framework (MEF)|
    |Microsoft.VisualStudio.Modeling.Sdk.[version]|Zdefiniuj rozszerzenia modelowania|

7. Kopiuj przykładowy kod na końcu tego tematu w pliku klasy w projekcie Walidatora biblioteki, aby uwzględnić kod przy sprawdzaniu poprawności. Aby uzyskać więcej informacji, zobacz [programowanie walidacji](#programming).

8. Aby przetestować rozszerzenie, zobacz [debugowanie walidacji warstwowej](#debugging).

    > [!NOTE]
    > Metoda zostanie wywołana tylko w szczególnych okolicznościach, a punkty przerwania nie będą działać automatycznie. Aby uzyskać więcej informacji, zobacz [debugowanie walidacji warstwowej](#debugging).

9. Aby zainstalować VSIX w głównym wystąpieniu programu Visual Studio lub na innym komputerze, należy znaleźć **.vsix** w pliku **bin** katalogu projektów VSIX. Skopiuj go do komputera, na którym chcesz zainstalować VSIX. Kliknij dwukrotnie plik VSIX w Eksploratorze Windows.

##  <a name="programming"></a> Sprawdzanie poprawności programowania

Aby zdefiniować rozszerzenie warstwy sprawdzania poprawności, zdefiniujesz klasę, która ma następujące cechy:

- Ogólny formularz zgłoszenia jest następujący:

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

- Po wykryciu błędu, możesz go zgłosić za pomocą `LogValidationError()`.

  > [!WARNING]
  > Nie używaj parametrów opcjonalnych `LogValidationError`.

Kiedy użytkownik wywoła **sprawdzanie poprawności architektury** polecenia menu, system plików środowiska uruchomieniowego warstwy analizuje warstwy i ich artefakty w celu przedstawienia na wykresie. Wykres ma cztery części:

- Modele warstwy rozwiązanie programu Visual Studio, które są reprezentowane jako węzły i łącza na wykresie.

- Kod, elementy projektów i innych artefaktów, które są zdefiniowane w rozwiązaniu i reprezentowane jako węzły i łącza, które reprezentują zależności odnalezione przez proces analizy.

- Łączy z węzłów warstwy do węzłów artefaktu kodu.

- Węzły, które reprezentują błędy wykryte przez Walidatora.

Gdy wykres został skonstruowany, wywoływana jest standardowa metoda sprawdzania poprawności. Po zakończeniu tej operacji, wszystkie metody sprawdzania poprawności zainstalowanych rozszerzeń są wywoływane w nieokreślonej kolejności. Wykres jest przekazywany do każdej `ValidateArchitecture` metody, która pozwala na skanowanie wykresu i zgłasza wszelkie błędy, które znajdzie.

> [!NOTE]
> Nie jest taki sam jak proces sprawdzania poprawności, który może służyć w językach specyficznych dla domeny.

Metody sprawdzania poprawności nie powinny zmieniać warstwy modelu lub kod, który jest weryfikowany.

Model wykresu jest zdefiniowany w <xref:Microsoft.VisualStudio.GraphModel>. Jego główne klasy to <xref:Microsoft.VisualStudio.GraphModel.GraphNode> i <xref:Microsoft.VisualStudio.GraphModel.GraphLink>.

Każdy węzeł i każde łącze posiada jedną lub więcej kategorii, które określają typ elementu lub relacji, który reprezentuje. Węzły typowych wykresów mają następujące kategorie:

- Dsl.LayerModel

- Dsl.Layer

- Dsl.Reference

- CodeSchema_Type

- CodeSchema_Namespace

- CodeSchema_Type

- CodeSchema_Method

- CodeSchema_Field

- CodeSchema_Property

Łączy z warstwy do elementów w kodzie należą do kategorii "Reprezentuje".

##  <a name="debugging"></a> Debugowanie sprawdzania poprawności

Aby debugować rozszerzenie warstwy sprawdzania poprawności, naciśnij kombinację klawiszy CTRL + F5. Otwiera doświadczalne wystąpienie programu Visual Studio. W tym wypadku Otwórz lub Utwórz model warstwy. Ten model musi być skojarzony z kodem i musi mieć co najmniej jedną zależność.

### <a name="test-with-a-solution-that-contains-dependencies"></a>Testowanie za pomocą rozwiązania, które zawiera zależności

Sprawdzanie poprawności nie jest wykonywane, chyba że występują następujące cechy:

- Brakuje co najmniej jedno łącze zależności na diagram zależności.

- Istnieją warstwy w modelu, które są skojarzone z elementami kodu.

Podczas pierwszego uruchomienia doświadczalne wystąpienie programu Visual Studio, aby przetestować rozszerzenie sprawdzania poprawności, Otwórz lub Utwórz rozwiązanie, które ma te cechy.

### <a name="run-clean-solution-before-validate-architecture"></a>Uruchom czyste rozwiązanie przez sprawdzeniem poprawności architektury

Kiedy należy zaktualizować kod sprawdzania poprawności, używać **czyste rozwiązanie** na polecenia **kompilacji** menu w eksperymentalnym rozwiązaniu, zanim zaczniesz testować polecenie sprawdzania poprawności. Jest to konieczne, ponieważ wyniki weryfikacji są buforowane. Jeśli nie zaktualizowano diagram zależności testu lub jego kod, nie można wykonać metody sprawdzania poprawności.

### <a name="launch-the-debugger-explicitly"></a>Jawnie Uruchom program debugera

Sprawdzanie poprawności działa w oddzielnym procesie. W związku z tym nie będą wyzwalane punktów przerwania w metodzie sprawdzania poprawności. Należy dołączyć debuger do procesu jawnie podczas sprawdzania poprawności zostało rozpoczęte.

Aby dołączyć debuger do procesu sprawdzania poprawności, należy wstawić wywołanie `System.Diagnostics.Debugger.Launch()` na początku metody sprawdzania poprawności. Gdy pojawi się okno dialogowe debugowania, wybierz wystąpienie główne programu Visual Studio.

Alternatywnie, można wstawić wywołanie do `System.Windows.Forms.MessageBox.Show()`. Gdy pojawi się okno komunikatu, przejdź do głównego wystąpienia programu Visual Studio i na **debugowania** kliknij menu **dołączyć do procesu**. Wybierz proces, który nosi nazwę **Graphcmd.exe**.

Zawsze uruchamiaj wystąpienie doświadczalne naciskając kombinację klawiszy CTRL + F5 (**Uruchom bez debugowania**).

### <a name="deploying-a-validation-extension"></a>Wdrażanie rozszerzenie sprawdzania poprawności

Aby zainstalować rozszerzenie sprawdzania poprawności na komputerze, na którym zainstalowano odpowiedniej wersji programu Visual Studio, otwórz plik VSIX na komputerze docelowym.

##  <a name="example"></a> Przykładowy kod

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
