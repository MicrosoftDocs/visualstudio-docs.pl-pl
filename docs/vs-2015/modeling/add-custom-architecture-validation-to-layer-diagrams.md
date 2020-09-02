---
title: Dodawanie niestandardowej walidacji architektury do diagramów warstw | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- layer diagrams, adding custom validation
ms.assetid: fed7bc08-295a-46d6-9fd8-fb537f1f75f1
caps.latest.revision: 44
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0b5ebe4e38878df209ab6065b1dbca88cd8404b2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655302"
---
# <a name="add-custom-architecture-validation-to-layer-diagrams"></a>Dodawanie niestandardowej weryfikacji architektury do diagramów warstw
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W programie Visual Studio użytkownicy mogą sprawdzać poprawność kodu źródłowego w projekcie względem modelu warstwy, aby można było sprawdzić, czy kod źródłowy jest zgodny z zależnościami na diagramie warstwowym. Istnieje standardowy algorytm walidacji, ale można zdefiniować własne rozszerzenia sprawdzania poprawności.

 Gdy użytkownik wybierze polecenie **Weryfikuj architekturę** na diagramie warstwowym, wywoływana jest standardowa metoda sprawdzania poprawności, a następnie wszystkie rozszerzenia sprawdzania poprawności, które zostały zainstalowane.

> [!NOTE]
> Walidacja w diagramie warstwowym nie jest taka sama jak Walidacja w diagramach UML. Na diagramie warstwowym głównym celem jest porównanie diagramu z kodem programu w innych częściach rozwiązania.

 Możesz spakować rozszerzenie z walidacją warstwy do rozszerzenia programu Visual Studio Integration (VSIX), które można dystrybuować do innych użytkowników programu Visual Studio. Możesz umieścić swój moduł sprawdzania poprawności w VSIX lub można połączyć go w tym samym VSIX, co inne rozszerzenia. Należy napisać kod modułu sprawdzania poprawności we własnym projekcie programu Visual Studio, a nie w tym samym projekcie, w którym są inne rozszerzenia.

> [!WARNING]
> Po utworzeniu projektu sprawdzania poprawności Skopiuj [przykładowy kod](#example) na końcu tego tematu, a następnie zmodyfikuj go do własnych potrzeb.

## <a name="requirements"></a>Wymagania
 Zobacz [wymagania](../modeling/extend-layer-diagrams.md#prereqs).

## <a name="defining-a-layer-validator-in-a-new-vsix"></a>Definiowanie modułu sprawdzania poprawności warstwy w nowym VSIX
 Najszybszą metodą tworzenia modułu sprawdzania poprawności jest użycie szablonu projektu. Spowoduje to umieszczenie kodu i manifestu VSIX w tym samym projekcie.

#### <a name="to-define-an-extension-by-using-a-project-template"></a>Aby zdefiniować rozszerzenie przy użyciu szablonu projektu

1. Utwórz projekt w nowym rozwiązaniu za pomocą polecenia **Nowy projekt** w menu **plik** .

2. W oknie dialogowym **Nowy projekt** w obszarze **projekty modelowania**wybierz pozycję **rozszerzenie walidacji projektanta warstwy**.

    Szablon tworzy projekt, który zawiera niewielki przykład.

   > [!WARNING]
   > Aby makethe szablon działał prawidłowo:
   >
   > - Edytuj wywołania do, `LogValidationError` Aby usunąć opcjonalne argumenty `errorSourceNodes` i `errorTargetNodes` .
   >   - W przypadku używania właściwości niestandardowych należy zastosować aktualizację wymienioną w temacie [Dodawanie właściwości niestandardowych do diagramów warstwowych](../modeling/add-custom-properties-to-layer-diagrams.md).

3. Edytuj kod w celu zdefiniowania walidacji. Aby uzyskać więcej informacji, zobacz [Walidacja programowania](#programming).

4. Aby przetestować rozszerzenie, zobacz [debugowanie walidacji warstwy](#debugging).

   > [!NOTE]
   > Metoda zostanie wywołana tylko w określonych okolicznościach, a punkty przerwania nie będą działać automatycznie. Aby uzyskać więcej informacji, zobacz [debugowanie walidacji warstwy](#debugging).

5. Aby zainstalować rozszerzenie w głównym wystąpieniu programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , lub na innym komputerze, Znajdź plik **. vsix** w pliku *bin \\ *. Skopiuj go do komputera, na którym chcesz go zainstalować, a następnie kliknij go dwukrotnie. Aby go odinstalować, użyj **rozszerzeń i aktualizacji** w menu **Narzędzia** .

## <a name="adding-a-layer-validator-to-a-separate-vsix"></a>Dodawanie modułu sprawdzania poprawności warstwy do oddzielnego VSIX
 Jeśli chcesz utworzyć jeden VSIX, który zawiera moduły walidacji warstwy, polecenia i inne rozszerzenia, zalecamy utworzenie jednego projektu do definiowania VSIX i oddzielnych projektów dla programów obsługi. Aby uzyskać informacje o innych typach rozszerzeń modelowania, zobacz [Rozszerzanie modeli UML i diagramów](../modeling/extend-uml-models-and-diagrams.md).

#### <a name="to-add-layer-validation-to-a-separate-vsix"></a>Aby dodać sprawdzanie poprawności warstwy do oddzielnego VSIX

1. Utwórz projekt biblioteki klas w nowym lub istniejącym rozwiązaniu programu Visual Studio. W oknie dialogowym **Nowy projekt** kliknij pozycję **Visual C#** , a następnie kliknij pozycję **Biblioteka klas**. Ten projekt będzie zawierać klasę walidacji warstwy.

2. Zidentyfikuj lub Utwórz projekt VSIX w rozwiązaniu. Projekt VSIX zawiera plik o nazwie **source. Extension. vsixmanifest**. Jeśli musisz dodać projekt VSIX, wykonaj następujące kroki:

    1. W oknie dialogowym **Nowy projekt** wybierz **Visual C#**, **rozszerzalność**, **Projekt VSIX**.

    2. W **Eksplorator rozwiązań**, w menu skrótów projektu VSIX, **Ustaw jako projekt startowy**.

3. W polu **source. Extension. vsixmanifest**w obszarze **zasoby**Dodaj projekt walidacji warstwy jako składnik MEF:

    1. Wybierz pozycję **Nowy**.

    2. W oknie dialogowym **Dodaj nowy zasób** Ustaw:

         **Typ**  =  **Microsoft. VisualStudio. MefComponent**

         **Źródło**  =  **Projekt w bieżącym rozwiązaniu**

         **Projekt**  =  *Twój projekt modułu sprawdzania poprawności*

4. Należy również dodać go jako walidację warstwy:

    1. Wybierz pozycję **Nowy**.

    2. W oknie dialogowym **Dodaj nowy zasób** Ustaw:

         **Typ**  =  **Microsoft. VisualStudio. ArchitectureTools. Layer. walidator**. Nie jest to jedna z opcji na liście rozwijanej. Musisz wprowadzić ją z klawiatury.

         **Źródło**  =  **Projekt w bieżącym rozwiązaniu**

         **Projekt**  =  *Twój projekt modułu sprawdzania poprawności*

5. Wróć do projektu walidacji warstwy i Dodaj następujące odwołania do projektu:

    |**Odwołanie**|**Co można zrobić**|
    |-------------------|------------------------------------|
    |Microsoft.VisualStudio.GraphModel.dll|Odczytywanie wykresu architektury|
    |Microsoft.VisualStudio.ArchitectureTools.Extensibility.CodeSchema.dll|Odczytaj kod DOM skojarzony z warstwami|
    |Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.dll|Odczytaj model warstwy|
    |Microsoft. VisualStudio. ArchitectureTools. rozszerzalność|Odczytuj i Aktualizuj kształty i diagramy.|
    |System. ComponentModel. kompozycji|Zdefiniuj składnik walidacji przy użyciu Managed Extensibility Framework (MEF)|
    |Microsoft. VisualStudio. Modeling. Sdk. nowszym|Definiowanie rozszerzeń modelowania|

6. Skopiuj przykładowy kod na końcu tego tematu do pliku klasy w projekcie biblioteki modułu sprawdzania poprawności, aby zawierał kod do walidacji. Aby uzyskać więcej informacji, zobacz [Walidacja programowania](#programming).

7. Aby przetestować rozszerzenie, zobacz [debugowanie walidacji warstwy](#debugging).

    > [!NOTE]
    > Metoda zostanie wywołana tylko w określonych okolicznościach, a punkty przerwania nie będą działać automatycznie. Aby uzyskać więcej informacji, zobacz [debugowanie walidacji warstwy](#debugging).

8. Aby zainstalować VSIX w głównym wystąpieniu programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , lub na innym komputerze, Znajdź plik **. vsix** w katalogu **bin** projektu VSIX. Skopiuj go do komputera, na którym chcesz zainstalować VSIX. Kliknij dwukrotnie plik VSIX w Eksploratorze Windows. (Eksplorator plików w systemie Windows 8).

     Aby go odinstalować, użyj **rozszerzeń i aktualizacji** w menu **Narzędzia** .

## <a name="programming-validation"></a><a name="programming"></a> Sprawdzanie poprawności programowania
 Aby zdefiniować rozszerzenie sprawdzania poprawności warstwy, należy zdefiniować klasę o następujących cechach:

- Ogólna forma deklaracji jest następująca:

  ```

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

- Po znalezieniu błędu można zgłosić go za pomocą polecenia `LogValidationError()` .

  > [!WARNING]
  > Nie należy używać parametrów opcjonalnych `LogValidationError` .

  Gdy użytkownik wywołuje polecenie menu **Weryfikuj architekturę** , system środowiska uruchomieniowego warstwy analizuje warstwy i ich artefakty w celu utworzenia grafu. Wykres ma cztery części:

- Modele warstwy [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozwiązania, które są reprezentowane jako węzły i linki na grafie.

- Kod, elementy projektu i inne artefakty, które są zdefiniowane w rozwiązaniu i reprezentowane jako węzły, oraz linki reprezentujące zależności wykryte przez proces analizy.

- Linki z węzłów warstwy do węzłów artefaktów kodu.

- Węzły, które reprezentują błędy wykryte przez moduł walidacji.

  Gdy wykres został skonstruowany, wywoływana jest standardowa metoda sprawdzania poprawności. Po zakończeniu tej czynności wszystkie zainstalowane metody walidacji rozszerzeń są wywoływane w nieokreślonej kolejności. Wykres jest przesyłany do każdej `ValidateArchitecture` metody, która może przeskanować wykres i zgłosić wszystkie znalezione błędy.

> [!NOTE]
> Nie jest to takie samo, jak proces sprawdzania poprawności, który jest stosowany do diagramów UML i nie jest taki sam, jak proces sprawdzania poprawności, który może być używany w językach specyficznych dla domeny.

 Metody sprawdzania poprawności nie powinny zmieniać modelu warstwy ani kodu, który jest sprawdzany.

 Model grafu jest zdefiniowany w <xref:Microsoft.VisualStudio.GraphModel> . Klasy główne są <xref:Microsoft.VisualStudio.GraphModel.GraphNode> i <xref:Microsoft.VisualStudio.GraphModel.GraphLink> .

 Każdy węzeł i każde łącze ma jedną lub więcej kategorii, które określają typ elementu lub relacji, które reprezentuje. Węzły typowego wykresu mają następujące kategorie:

- DSL. LayerModel

- DSL. Layer

- DSL. Reference

- CodeSchema_Type

- CodeSchema_Namespace

- CodeSchema_Type

- CodeSchema_Method

- CodeSchema_Field

- CodeSchema_Property

  Linki z warstw do elementów w kodzie mają kategorię "reprezentowane".

## <a name="debugging-validation"></a><a name="debugging"></a> Sprawdzanie poprawności debugowania
 Aby debugować rozszerzenie warstwy sprawdzania poprawności, naciśnij klawisze CTRL + F5. Doświadczalne wystąpienie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zostanie otwarte. W tym wystąpieniu Otwórz lub Utwórz model warstwy. Ten model musi być skojarzony z kodem i musi mieć co najmniej jedną zależność.

### <a name="test-with-a-solution-that-contains-dependencies"></a>Testowanie z rozwiązaniem zawierającym zależności
 Sprawdzanie poprawności nie jest wykonywane, chyba że są obecne następujące cechy:

- Istnieje co najmniej jedno łącze zależności na diagramie warstwowym.

- Istnieją warstwy w modelu, które są skojarzone z elementami kodu.

  Podczas pierwszego uruchomienia eksperymentalnego wystąpienia programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] w celu przetestowania rozszerzenia walidacji Otwórz lub Utwórz rozwiązanie, które ma te cechy.

### <a name="run-clean-solution-before-validate-architecture"></a>Uruchom czyste rozwiązanie przed walidacją architektury
 Za każdym razem, gdy aktualizujesz kod weryfikacyjny, użyj polecenia **Oczyść rozwiązanie** w menu **kompilacja** w eksperymentalnym rozwiązaniu, przed przetestowaniem polecenia walidacji. Jest to konieczne, ponieważ wyniki walidacji są buforowane. Jeśli nie zaktualizowano diagramu warstwy testów lub jego kodu, metody walidacji nie zostaną wykonane.

### <a name="launch-the-debugger-explicitly"></a>Jawnie uruchom debuger
 Sprawdzanie poprawności przebiega w osobnym procesie. W związku z tym punkty przerwania w metodzie walidacji nie będą wyzwalane. Musisz dołączyć debuger do procesu jawnie po rozpoczęciu walidacji.

 Aby dołączyć debuger do procesu sprawdzania poprawności, Wstaw wywołanie na początku `System.Diagnostics.Debugger.Launch()` metody walidacji. Gdy pojawi się okno dialogowe debugowanie, wybierz główne wystąpienie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

 Alternatywnie można wstawić wywołanie do `System.Windows.Forms.MessageBox.Show()` . Gdy pojawi się okno komunikatu, przejdź do głównego wystąpienia programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] i w menu **debugowanie** kliknij przycisk **Dołącz do procesu**. Wybierz proces o nazwie **Graphcmd.exe**.

 Zawsze uruchamiaj eksperymentalne wystąpienie przez naciśnięcie klawiszy CTRL + F5 (**Rozpocznij bez debugowania**).

### <a name="deploying-a-validation-extension"></a>Wdrażanie rozszerzenia walidacji
 Aby zainstalować rozszerzenie sprawdzania poprawności na komputerze, na którym jest zainstalowana odpowiednia wersja programu Visual Studio, Otwórz plik VSIX na komputerze docelowym. Aby zainstalować program na komputerze, na którym [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] jest zainstalowany, należy ręcznie wyodrębnić zawartość VSIX do folderu rozszerzeń. Aby uzyskać więcej informacji, zobacz [Wdrażanie modelu warstwy](../modeling/deploy-a-layer-model-extension.md).

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
 [Rozszerzone diagramy warstw](../modeling/extend-layer-diagrams.md)
