---
title: Dodawanie niestandardowej walidacji architektury do diagramów warstw | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- layer diagrams, adding custom validation
ms.assetid: fed7bc08-295a-46d6-9fd8-fb537f1f75f1
caps.latest.revision: 44
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b91f89bc6c3db52526c8c5e64549b08310a17313
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60045884"
---
# <a name="add-custom-architecture-validation-to-layer-diagrams"></a>Dodawanie niestandardowej weryfikacji architektury do diagramów warstw
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W programie Visual Studio użytkownicy mogą sprawdzić poprawność kodu źródłowego w projekcie względem modelu warstwy, aby mogli zweryfikować, że kod źródłowy odpowiada zależnościom na diagramie warstwy. Istnieje algorytm standardowego sprawdzania poprawności, ale można zdefiniować własne rozszerzenia sprawdzania poprawności.  
  
 Gdy użytkownik wybierze **sprawdzanie poprawności architektury** polecenia na diagramie warstwy, wywoływana jest standardowa metoda sprawdzania poprawności, następuje wszystkie rozszerzenia sprawdzania poprawności, które zostały zainstalowane.  
  
> [!NOTE]
>  Sprawdzanie poprawności na diagramie warstwy nie jest taka sama, jak sprawdzanie poprawności na diagramach UML. Na diagramie warstwowym głównym celem jest porównanie diagramu z kodem programu w innych częściach rozwiązania.  
  
 Można spakować swoje rozszerzenie sprawdzania poprawności warstwy do Visual Studio Integration rozszerzenie (VSIX), który można rozdystrybuować innym użytkownikom programu Visual Studio. Teraz można umieścić swój moduł w VSIX przez siebie lub połączyć go w tym samym VSIX jako inne rozszerzenia. Należy wpisać kod modułu sprawdzania poprawności we własnym projekcie programu Visual Studio, a nie w tym samym projekcie jako inne rozszerzenia.  
  
> [!WARNING]
>  Po utworzeniu projektu sprawdzania poprawności, należy skopiować [przykładowy kod](#example) na końcu tego tematu, a następnie Edytuj, że do własnych potrzeb.  
  
## <a name="requirements"></a>Wymagania  
 Zobacz [wymagania](../modeling/extend-layer-diagrams.md#prereqs).  
  
## <a name="defining-a-layer-validator-in-a-new-vsix"></a>Definiowanie Walidatora warstwy w nowym VSIX  
 Najszybszą metodą tworzenia modułu sprawdzania poprawności jest użycie szablonu projektu. Te umieszcza kod i manifestu VSIX w tym samym projekcie.  
  
#### <a name="to-define-an-extension-by-using-a-project-template"></a>Aby zdefiniować rozszerzenie przy użyciu szablonu projektu  
  
1. Tworzenie projektu w nowym rozwiązaniu za pomocą **nowy projekt** polecenie **pliku** menu.  
  
2. W **nowy projekt** dialogowego **projekty modelowania**, wybierz opcję **rozszerzenie sprawdzania poprawności projektanta warstwy**.  
  
    Ten szablon tworzy projekt zawierający krótki przykład.  
  
   > [!WARNING]
   >  Do szablonu makethe działać prawidłowo:  
   > 
   > - Edytuj wywołania `LogValidationError` Aby usunąć opcjonalne argumenty `errorSourceNodes` i `errorTargetNodes`.  
   >   - Jeśli używasz właściwości niestandardowych, Zastosuj aktualizacje wymienione w [Dodawanie właściwości niestandardowych do diagramów warstw](../modeling/add-custom-properties-to-layer-diagrams.md).  
  
3. Edytowanie kodu w celu zdefiniowania walidacji. Aby uzyskać więcej informacji, zobacz [programowanie walidacji](#programming).  
  
4. Aby przetestować rozszerzenie, zobacz [debugowanie walidacji warstwowej](#debugging).  
  
   > [!NOTE]
   >  Metoda zostanie wywołana tylko w szczególnych okolicznościach, a punkty przerwania nie będą działać automatycznie. Aby uzyskać więcej informacji, zobacz [debugowanie walidacji warstwowej](#debugging).  
  
5. Aby zainstalować rozszerzenie w głównym wystąpieniu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], lub na innym komputerze, należy znaleźć **.vsix** w pliku *bin\\*. Skopiuj go na komputerze, na którym chcesz go zainstalować i kliknij go dwukrotnie. Aby odinstalować go, należy użyć **rozszerzenia i aktualizacje** na **narzędzia** menu.  
  
## <a name="adding-a-layer-validator-to-a-separate-vsix"></a>Dodawanie warstwowego modułu Walidującego do oddzielnego VSIX  
 Jeśli chcesz utworzyć jeden VSIX zawierający moduły sprawdzania warstwy, polecenia oraz inne rozszerzenia, zaleca się utworzenie jednego projektu do definiowania VSIX i oddzielnych projektów dla programów obsługi. Aby uzyskać informacje na temat innych rodzajów rozszerzenia modelowania, zobacz [modeli i diagramów UML rozszerzyć](../modeling/extend-uml-models-and-diagrams.md).  
  
#### <a name="to-add-layer-validation-to-a-separate-vsix"></a>Aby dodać sprawdzanie poprawności warstwy do oddzielnego VSIX  
  
1. Utwórz projekt biblioteki klas w nowym lub istniejącym rozwiązaniu Visual Studio. W **nowy projekt** okno dialogowe, kliknij przycisk **Visual C#** a następnie kliknij przycisk **biblioteki klas**. Projekt ten będzie zawierać klasy warstwy sprawdzania poprawności.  
  
2. Identyfikowanie lub Utwórz projekt VSIX w rozwiązaniu. Projekt VSIX zawiera plik o nazwie **source.extension.vsixmanifest**. Jeśli trzeba dodać projekt VSIX, wykonaj następujące kroki:  
  
    1. W **nowy projekt** okna dialogowego wybierz **Visual C#**, **rozszerzalności**, **projekt VSIX**.  
  
    2. W **Eksploratora rozwiązań**, w menu skrótów projektu VSIX **Ustaw jako projekt startowy**.  
  
3. W **source.extension.vsixmanifest**w obszarze **zasoby**, Dodaj projekt sprawdzania poprawności warstwy jako składnik MEF:  
  
    1. Wybierz **nowe**.  
  
    2. W **Dodaj nowy zasób** okno dialogowe, zestaw:  
  
         **Type** = **Microsoft.VisualStudio.MefComponent**  
  
         **Źródło** = **projekt w bieżącym rozwiązaniu**  
  
         **Projekt** = *projektu modułu sprawdzania poprawności*  
  
4. Należy także dodać go jako sprawdzanie poprawności warstwy:  
  
    1. Wybierz **nowe**.  
  
    2. W **Dodaj nowy zasób** okno dialogowe, zestaw:  
  
         **Type** = **Microsoft.VisualStudio.ArchitectureTools.Layer.Validator**. Nie jest jedną z opcji na liście rozwijanej. Należy wprowadzić je przy użyciu klawiatury.  
  
         **Źródło** = **projekt w bieżącym rozwiązaniu**  
  
         **Projekt** = *projektu modułu sprawdzania poprawności*  
  
5. Wróć do projektu warstwy sprawdzania poprawności i dodaj następujące odwołania do projektu:  
  
    |**Dokumentacja**|**Co to pozwala zrobić**|  
    |-------------------|------------------------------------|  
    |Microsoft.VisualStudio.GraphModel.dll|Odczytaj wykres architektury|  
    |Microsoft.VisualStudio.ArchitectureTools.Extensibility.CodeSchema.dll|Odczytać kod DOM skojarzony z warstwami|  
    |Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.dll|Przeczytaj warstwy modelu|  
    |Microsoft.VisualStudio.ArchitectureTools.Extensibility|Przeczytaj i Aktualizuj kształty i diagramy.|  
    |System.ComponentModel.Composition|Zdefiniuj składnik walidacji za pomocą Managed Extensibility Framework (MEF)|  
    |Microsoft.VisualStudio.Modeling.Sdk.[version]|Zdefiniuj rozszerzenia modelowania|  
  
6. Kopiuj przykładowy kod na końcu tego tematu w pliku klasy w projekcie Walidatora biblioteki, aby uwzględnić kod przy sprawdzaniu poprawności. Aby uzyskać więcej informacji, zobacz [programowanie walidacji](#programming).  
  
7. Aby przetestować rozszerzenie, zobacz [debugowanie walidacji warstwowej](#debugging).  
  
    > [!NOTE]
    >  Metoda zostanie wywołana tylko w szczególnych okolicznościach, a punkty przerwania nie będą działać automatycznie. Aby uzyskać więcej informacji, zobacz [debugowanie walidacji warstwowej](#debugging).  
  
8. Aby zainstalować VSIX w głównym wystąpieniu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], lub na innym komputerze, należy znaleźć **.vsix** w pliku **bin** katalogu projektów VSIX. Skopiuj go do komputera, na którym chcesz zainstalować VSIX. Kliknij dwukrotnie plik VSIX w Eksploratorze Windows. (Eksplorator plików w systemie Windows 8).  
  
     Aby odinstalować go, należy użyć **rozszerzenia i aktualizacje** na **narzędzia** menu.  
  
## <a name="programming"></a> Sprawdzanie poprawności programowania  
 Aby zdefiniować rozszerzenie warstwy sprawdzania poprawności, zdefiniujesz klasę, która ma następujące cechy:  
  
- Ogólny formularz zgłoszenia jest następujący:  
  
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
  
- Po wykryciu błędu, możesz go zgłosić za pomocą `LogValidationError()`.  
  
  > [!WARNING]
  >  Nie używaj parametrów opcjonalnych `LogValidationError`.  
  
  Kiedy użytkownik wywoła **sprawdzanie poprawności architektury** polecenia menu, system plików środowiska uruchomieniowego warstwy analizuje warstwy i ich artefakty w celu przedstawienia na wykresie. Wykres ma cztery części:  
  
- Modele warstwy [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozwiązanie, które są reprezentowane jako węzły i łącza na wykresie.  
  
- Kod, elementy projektów i innych artefaktów, które są zdefiniowane w rozwiązaniu i reprezentowane jako węzły i łącza, które reprezentują zależności odnalezione przez proces analizy.  
  
- Łączy z węzłów warstwy do węzłów artefaktu kodu.  
  
- Węzły, które reprezentują błędy wykryte przez Walidatora.  
  
  Gdy wykres został skonstruowany, wywoływana jest standardowa metoda sprawdzania poprawności. Po zakończeniu tej operacji, wszystkie metody sprawdzania poprawności zainstalowanych rozszerzeń są wywoływane w nieokreślonej kolejności. Wykres jest przekazywany do każdej `ValidateArchitecture` metody, która pozwala na skanowanie wykresu i zgłasza wszelkie błędy, które znajdzie.  
  
> [!NOTE]
>  To nie jest taki sam jak proces sprawdzania poprawności, który jest stosowany do diagramów UML i nie jest taki sam jak proces sprawdzania poprawności, który może służyć w językach specyficznych dla domeny.  
  
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
  
## <a name="debugging"></a> Debugowanie sprawdzania poprawności  
 Aby debugować rozszerzenie warstwy sprawdzania poprawności, naciśnij kombinację klawiszy CTRL + F5. Eksperymentalne wystąpienie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zostanie otwarty. W tym wypadku Otwórz lub Utwórz model warstwy. Ten model musi być skojarzony z kodem i musi mieć co najmniej jedną zależność.  
  
### <a name="test-with-a-solution-that-contains-dependencies"></a>Testowanie za pomocą rozwiązania, które zawiera zależności  
 Sprawdzanie poprawności nie jest wykonywane, chyba że występują następujące cechy:  
  
- Istnieje co najmniej jedno łącze zależności na diagramie warstwowym.  
  
- Istnieją warstwy w modelu, które są skojarzone z elementami kodu.  
  
  Przy pierwszym uruchomieniu wystąpienia doświadczalnego [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] do testowania Twojego rozszerzenia sprawdzania poprawności, Otwórz lub Utwórz rozwiązanie, które ma te cechy.  
  
### <a name="run-clean-solution-before-validate-architecture"></a>Uruchom czyste rozwiązanie przez sprawdzeniem poprawności architektury  
 Kiedy należy zaktualizować kod sprawdzania poprawności, używać **czyste rozwiązanie** na polecenia **kompilacji** menu w eksperymentalnym rozwiązaniu, zanim zaczniesz testować polecenie sprawdzania poprawności. Jest to konieczne, ponieważ wyniki weryfikacji są buforowane. Jeśli test diagramu warstwy lub jego kod nie zostały zaktualizowane, nie można wykonać metody sprawdzania poprawności.  
  
### <a name="launch-the-debugger-explicitly"></a>Jawnie Uruchom program debugera  
 Sprawdzanie poprawności działa w oddzielnym procesie. W związku z tym nie będą wyzwalane punktów przerwania w metodzie sprawdzania poprawności. Należy dołączyć debuger do procesu jawnie podczas sprawdzania poprawności zostało rozpoczęte.  
  
 Aby dołączyć debuger do procesu sprawdzania poprawności, należy wstawić wywołanie `System.Diagnostics.Debugger.Launch()` na początku metody sprawdzania poprawności. Gdy pojawi się okno dialogowe debugowania, wybierz wystąpienie główne [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
 Alternatywnie, można wstawić wywołanie do `System.Windows.Forms.MessageBox.Show()`. Gdy pojawi się okno komunikatu, przejdź do głównego wystąpienia [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] i **debugowania** kliknij menu **dołączyć do procesu**. Wybierz proces, który nosi nazwę **Graphcmd.exe**.  
  
 Zawsze uruchamiaj wystąpienie doświadczalne naciskając kombinację klawiszy CTRL + F5 (**Uruchom bez debugowania**).  
  
### <a name="deploying-a-validation-extension"></a>Wdrażanie rozszerzenie sprawdzania poprawności  
 Aby zainstalować rozszerzenie sprawdzania poprawności na komputerze, na którym zainstalowano odpowiedniej wersji programu Visual Studio, otwórz plik VSIX na komputerze docelowym. Aby zainstalować na komputerze, na którym [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] jest zainstalowany, należy ręcznie wyodrębnić zawartości VSIX do folderu rozszerzeń. Aby uzyskać więcej informacji, zobacz [wdrażanie rozszerzenia modelu warstwy](../modeling/deploy-a-layer-model-extension.md).  
  
## <a name="example"></a> Przykładowy kod  
  
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
