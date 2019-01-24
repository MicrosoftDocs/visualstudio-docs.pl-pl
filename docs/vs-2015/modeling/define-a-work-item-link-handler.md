---
title: Definiowanie procedury obsługi łącza elementu roboczego | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API
ms.assetid: d52e0bbf-0166-4bb4-a2e3-cefed6188875
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7bc151e69206e37f88eac04ac8bbb2f4d9dbf1ad
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54767963"
---
# <a name="define-a-work-item-link-handler"></a>Definiowanie procedury obsługi łącza elementu roboczego
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można tworzyć rozszerzenia programu Visual Studio Integration które reaguje, gdy użytkownik tworzy lub usuwa łącze między elementem modelu UML i elementu roboczego. Na przykład gdy użytkownik wybierze opcję połączenia nowego elementu roboczego do elementu modelu, kod może zainicjować pola elementu roboczego z wartości w modelu.  
  
## <a name="set-up-a-uml-extension-solution"></a>Skonfiguruj rozwiązanie rozszerzenia UML  
 Pozwoli to na opracowanie programów obsługi i rozdystrybuować je innym użytkownikom. Należy skonfigurować dwa projekty programu Visual Studio:  
  
-   Projekt biblioteki klas zawierający kod obsługi łączy.  
  
-   Projekt VSIX, który działa jako kontener dla polecenia instalowania. Jeśli chcesz, możesz dodać inne składniki w tym samym VSIX.  
  
#### <a name="to-set-up-the-visual-studio-solution"></a>Aby skonfigurować rozwiązanie programu Visual Studio  
  
1.  Utwórz projekt biblioteki klas, dodając go do istniejącego rozwiązania VSIX albo tworząc nowe rozwiązanie.  
  
    1.  Na **pliku** menu, wybierz **New**, **projektu**.  
  
    2.  W obszarze **zainstalowane szablony**, rozwiń węzeł **Visual C#** lub **języka Visual Basic**, następnie w środkowej kolumnie kliknij **biblioteki klas**.  
  
    3.  Ustaw **rozwiązania** do wskazania, czy chcesz, aby utworzyć nowe rozwiązanie lub dodać składnik do rozwiązania VSIX, które jest już otwarte.  
  
    4.  Ustaw projekt nazwę i lokalizację i kliknij przycisk OK.  
  
2.  Chyba że rozwiązanie zawiera już jeden, Utwórz projekt VSIX.  
  
    1.  W **Eksploratora rozwiązań**, w menu skrótów rozwiązania wybierz **Dodaj**, **nowy projekt**.  
  
    2.  W obszarze **zainstalowane szablony**, rozwiń węzeł **Visual C#** lub **języka Visual Basic**, a następnie wybierz **rozszerzalności**. W środkowej kolumnie Wybierz **projekt VSIX**.  
  
3.  Ustaw projekt VSIX jako projekt startowy rozwiązania.  
  
    -   W Eksploratorze rozwiązań w menu skrótów projektu VSIX wybierz **Ustaw jako projekt startowy**.  
  
4.  W **source.extension.vsixmanifest**w obszarze **zawartości**, Dodaj projekt biblioteki klas jako składnik MEF.  
  
    1.  Na **metadanych** kartę, ustaw nazwę VSIX.  
  
    2.  Na **Instaluj obiekty docelowe** kartę, należy ustawić wersji programu Visual Studio jako obiekty docelowe.  
  
    3.  Na **zasoby** kartę, wybrać **New**i w oknie dialogowym Ustaw:  
  
         **Typ** = **składnik MEF**  
  
         **Źródło** = **projekt w bieżącym rozwiązaniu**  
  
         **Projekt** = *projektu biblioteki klas*  
  
## <a name="defining-the-work-item-link-handler"></a>Definiowanie procedury obsługi łącza elementu roboczego  
 Wykonaj wszystkie poniższe zadania w projekcie biblioteki klas.  
  
### <a name="project-references"></a>Odwołania do projektu  
 Dodaj następujący kod [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)] zestawy do odwołań projektu:  
  
 `Microsoft.TeamFoundation.WorkItemTracking.Client.dll`  
  
 `Microsoft.VisualStudio.TeamFoundation.WorkItemTracking.dll Microsoft.VisualStudio.Modeling.Sdk.[version]`  
  
 `Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml`  
  
 `Microsoft.VisualStudio.Uml.Interfaces`  
  
 `System.ComponentModel.Composition`  
  
 `System.Drawing` -używany przez przykładowy kod  
  
 Jeśli nie możesz znaleźć jednego z tych odwołań w obszarze **.Net** karcie **Dodaj odwołanie** okno dialogowe, użyj karty Przeglądaj, aby je znaleźć w \Program Files\Microsoft programu Visual Studio [wersja] \Common7\IDE\ PrivateAssemblies\\.  
  
### <a name="import-the-work-item-namespace"></a>Importuj Namespace elementu roboczego  
 W swojej [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projektu **odwołania**, dodaj odwołania do następujących zestawów:  
  
- Microsoft.TeamFoundation.WorkItemTracking.Client.dll  
  
- Microsoft.VisualStudio.TeamFoundation.WorkItemTracking.dll  
  
  W kodzie programu zaimportuj następujące przestrzenie nazw:  
  
```  
using System.ComponentModel.Composition;  
using Microsoft.VisualStudio.Uml.Classes;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
using Microsoft.VisualStudio.TeamFoundation.WorkItemTracking;  
using System.Linq;  
```  
  
### <a name="define-the-linked-work-item-event-handler"></a>Definiowanie procedury obsługi zdarzeń dla elementu połączonego z pracą  
 Dodaj plik klasy do projektu biblioteki klas i ustaw jego zawartość w następujący sposób. Zmień nazwy przestrzeni nazw i klasy, na co wolisz.  
  
```  
using System.ComponentModel.Composition;  
using Microsoft.VisualStudio.Uml.Classes;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;  
using Microsoft.VisualStudio.TeamFoundation.WorkItemTracking;  
using System.Linq;  
  
namespace WorkItems  
{  
  [Export(typeof(ILinkedWorkItemExtension))]  
  public class MyWorkItemExtension : ILinkedWorkItemExtension  
  {  
    // Called before a new work item is edited by the user.  
    // Use this to initialize work item fields from the model element.  
    public void OnWorkItemCreated(System.Collections.Generic.IEnumerable<IElement> elementsToBeLinked, IWorkItemDocument workItemDocument)  
    {  
      INamedElement namedElement =  
            elementsToBeLinked.First() as INamedElement;  
      if (namedElement != null)  
        workItemDocument.Item.Title = namedElement.Name;  
  
    }  
  
    // Called when any work item is linked to a model element.  
    public void OnWorkItemLinked(System.Collections.Generic.IEnumerable<IElement> elements, string serverUri, int workItemId)  
    {  
      foreach (IElement element in elements)  
        foreach (IShape shape in element.Shapes())  
          shape.Color = System.Drawing.Color.Red;  
    }  
  
    // Called when a work item is unlinked from a model element.  
    public void OnWorkItemRemoved(IElement element, string serverUri, int workItemId)  
    {  
      foreach (IShape shape in element.Shapes())  
        shape.Color = System.Drawing.Color.White;  
    }  
  }  
}  
```  
  
## <a name="testing-the-link-handler"></a>Testowanie obsługi łącza  
 Do celów testowych wykonaj procedurę obsługi łącza w trybie debugowania.  
  
> [!WARNING]
>  Możesz musi już być podłączony do TFS źródła kodu kontrolki (SCC) można utworzyć lub połączyć elementu roboczego. Jeśli próbujesz nawiązać połączenie z inną SCC TFS, Visual Studio powoduje zamknięcie bieżącego rozwiązania automatycznie. Upewnij się, że jesteś podłączony do odpowiednich SCC przed przystąpieniem do tworzenia lub łącze do elementu roboczego. W kolejnych wersjach programu Visual Studio polecenia menu nie są dostępne, jeśli nie są połączone SCC.  
  
#### <a name="to-test-the-link-handler"></a>Testowanie obsługi łącza  
  
1.  Naciśnij klawisz **F5**, lub na **debugowania** menu, wybierz **Rozpocznij debugowanie**.  
  
     Eksperymentalne wystąpienie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozpoczyna się.  
  
     **Rozwiązywanie problemów z**: Jeśli nowy [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nie start, upewnij się, że projekt VSIX jest ustawiony jako projekt startowy rozwiązania.  
  
2.  W eksperymentalnym [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], Otwórz lub Utwórz projekt modelowania i otworzyć lub utworzyć diagram modelowania.  
  
3.  Utwórz element modelu, taki jak klasa UML i ustaw jego nazwę.  
  
4.  Kliknij prawym przyciskiem myszy element, a następnie kliknij przycisk **Utwórz element roboczy**.  
  
    -   Jeśli podmenu zawiera **Otwórz połączenie serwera programu Team Foundation**, konieczne będzie Zamknij projekt, nawiązać połączenie z odpowiednią TFS i ponownie uruchom tę procedurę.  
  
    -   Jeśli podmenu zawiera listę typów elementów roboczych, kliknij jeden.  
  
         Zostanie otwarty nowy formularz elementu roboczego.  
  
5.  Sprawdź, czy tytuł elementu roboczego jest taki sam jak element modelu, jeśli użyto przykładowego kodu w poprzedniej sekcji. W tym przykładzie pokazano `OnWorkItemCreated()` pracował.  
  
6.  Wypełnij formularz, Zapisz i Zamknij element roboczy.  
  
7.  Sprawdź, czy element roboczy jest teraz wyświetlane w kolorze czerwonym. W tym przykładzie pokazano `OnWorkItemLinked()` w przykładowym kodzie.  
  
     **Rozwiązywanie problemów z**: Jeśli nie uruchomiono metody obsługi, upewnij się, że:  
  
    -   Projekt biblioteki klas jest wymieniony jako składnik listy MEF **zawartości** listy w **source.extensions.manifest** w projekcie VSIX.  
  
    -   Poprawny `Export` atrybut jest dołączany do klasy obsługi i wdraża klasy `ILinkedWorkItemExtension`.  
  
    -   Parametry wszystkich `Import` i `Export` atrybuty są prawidłowe.  
  
## <a name="about-the-work-item-handler-code"></a>O kodzie procedury obsługi elementu roboczego  
  
### <a name="listening-for-new-work-items"></a>Nasłuchiwanie nowych elementów roboczych  
 `OnWorkItemCreated` jest wywoływana, gdy użytkownik zdecyduje się na utworzenie nowego elementu roboczego, który zostanie powiązany z elementami modelu. Twój kod może zainicjować pola elementów roboczych. Element roboczy jest następnie prezentowany użytkownikowi, który może aktualizować pola i zapisać element roboczy. Link do elementu modelu nie jest tworzony, dopóki element roboczy został pomyślnie zapisany.  
  
```  
public void OnWorkItemCreated(  
    IEnumerable<IElement> elementsToBeLinked,  
    IWorkItemDocument workItem)  
{  
  INamedElement namedElement =   
         elementsToBeLinked.First() as INamedElement;  
  if (namedElement != null)  
      workItem.Item.Title = namedElement.Name;  
}  
```  
  
### <a name="listening-for-link-creation"></a>Nasłuchiwanie tworzenia łącza  
 `OnWorkItemLinked` jest wywoływana po utworzeniu łącza. Jest to, czy łącze do nowego elementu roboczego lub istniejącego elementu. Jest on wywoływany raz dla każdego elementu roboczego.  
  
```  
public void OnWorkItemLinked  
        (IEnumerable<IElement> elements,   
         string serverUri, // TFS server  
         int workItemId)  
{  
  foreach (IElement element in elements)  
    foreach (IShape shape in element.Shapes())  
         shape.Color = System.Drawing.Color.Red;  
}  
```  
  
> [!NOTE]
>  Aby ten przykład działał, należy dodać odwołanie projektu do `System.Drawing.dll`i zaimportuj przestrzeń nazw `Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation`. Jednak te dodatki nie są wymagane dla innych implementacji `OnWorkItemLinked`.  
  
### <a name="listening-for-link-removal"></a>Nasłuchiwanie usuwania łącza  
 `OnWorkItemRemoved` jest wywoływana, gdy tuż przed każdym łączem do elementu roboczego, który jest skreślony. Jeśli element modelu zostanie usunięty, wszystkie jego łącza zostaną usunięte.  
  
```  
public void OnWorkItemRemoved  
         (IElement element, string serverUri, int workItemId)  
{...}  
```  
  
## <a name="updating-a-work-item"></a>Aktualizacja elementu roboczego  
 Za pomocą przestrzeni nazw Team Foundation, możesz manipulować elementami roboczymi.  
  
 Aby użyć w poniższym przykładzie, należy dodać te zestawy .NET do odwołań projektu:  
  
-   Microsoft.TeamFoundation.Client.dll  
  
-   Microsoft.TeamFoundation.WorkItemTracking.Client.dll  
  
```  
  
using Microsoft.TeamFoundation.Client;  
using Microsoft.TeamFoundation.WorkItemTracking.Client;  
...  
public void OnWorkItemLinked  
        (IEnumerable<IElement> elements,   
         string serverUri, // TFS server  
         int workItemId)  
{  
  TfsTeamProjectCollection tfs =  
        TfsTeamProjectCollectionFactory  
            .GetTeamProjectCollection(new Uri(serverUri));  
  WorkItemStore workItemStore = new WorkItemStore(tfs);  
  WorkItem item = workItemStore.GetWorkItem(workItemId);  
  item.Open();  
  item.Title = "something";  
  item.Save();  
}   
```  
  
## <a name="accessing-the-work-item-reference-links"></a>Uzyskiwanie dostępu do łączy odwołań elementu roboczego  
 Aby uzyskać dostęp łącza w następujący sposób:  
  
```  
//Get:  
string linkString = element.GetReference(ReferenceConstants.WorkItem);  
// Set:  
element.AddReference(ReferenceConstants.WorkItem, linkString, true);  
  
```  
  
 Format `linkString` jest:  
  
 `string.Format(@"%{0}\{1}#{1}${2}", tfServer, projectCollection, RepositoryGuid, workItem.Id);`  
  
 gdzie:  
  
- Identyfikator URI serwera będzie:  
  
   `http://tfServer:8080/tfs/projectCollection`  
  
   Sprawa jest ważna w `projectCollection`.  
  
- `RepositoryGuid` można otrzymać od połączenia TFS:  
  
  ```csharp  
  TfsTeamProjectCollection tpc = TfsTeamProjectCollectionFactory...;  
  RepositoryGuid= tpc.InstanceId;  
  
  ```  
  
  Aby uzyskać więcej informacji na temat odwołań, zobacz [elementów modelu dołączanie ciągów odwołania do UML](../modeling/attach-reference-strings-to-uml-model-elements.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.TeamFoundation.WorkItemTracking.Client.WorkItemStore?displayProperty=fullName>   
 [Łączenie elementów modeli i elementów roboczych](../modeling/link-model-elements-and-work-items.md)   
 [Dołączanie ciągów odwołania do elementów modelu UML](../modeling/attach-reference-strings-to-uml-model-elements.md)   
 [Definiowanie i instalowanie rozszerzenia modelowania](../modeling/define-and-install-a-modeling-extension.md)   
 [Programowanie za pomocą interfejsu API UML](../modeling/programming-with-the-uml-api.md)
