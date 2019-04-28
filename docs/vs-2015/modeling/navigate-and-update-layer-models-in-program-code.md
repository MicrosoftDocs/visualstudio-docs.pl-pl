---
title: Nawigowanie i aktualizowanie modeli warstw w kodzie programu | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- layer models, navigating in program code
- layer models, updating in program code
ms.assetid: c60edc87-33ee-4964-a954-40069f9febf3
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 05a7b50c15c3bc1953e4be3d13809fd9db64f052
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63435015"
---
# <a name="navigate-and-update-layer-models-in-program-code"></a>Nawigowanie i aktualizowanie modeli warstw w kodzie programu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym temacie opisano elementy i relacje w modelach warstwy, które można znaleźć i zaktualizować przy użyciu kodu programu. Aby uzyskać więcej informacji dotyczących diagramów warstw z punktu widzenia użytkownika, zobacz [diagramy warstw: Odwołanie](../modeling/layer-diagrams-reference.md) i [diagramy warstw: Wytyczne dotyczące](../modeling/layer-diagrams-guidelines.md).  
  
 <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer> Modelu opisane w tym temacie jest fasada w bardziej ogólnej <xref:Microsoft.VisualStudio.GraphModel> modelu. Jeśli piszesz [rozszerzenie menu polecenia lub gestu](../modeling/add-commands-and-gestures-to-layer-diagrams.md), użyj `Layer` modelu. Jeśli piszesz [rozszerzenie sprawdzania poprawności warstwy](../modeling/add-custom-architecture-validation-to-layer-diagrams.md), jest łatwiejszy w obsłudze `GraphModel`.  
  
## <a name="transactions"></a>Transakcje  
 Po zaktualizowaniu modelu należy wziąć pod uwagę zmiany w załączonym `ILinkedUndoTransaction`. Grupuje zmiany jako jedna transakcja. Jeśli zmiany zakończy się niepowodzeniem, cała transakcja zostanie wycofana. Jeśli użytkownik spowoduje cofnięcie zmian, wszystkie zmiany zostaną cofnięte ze sobą.  
  
 Aby uzyskać więcej informacji, zobacz [aktualizacji modelu UML łącza za pomocą transakcji](../modeling/link-uml-model-updates-by-using-transactions.md).  
  
```  
using (ILinkedUndoTransaction t =  
        LinkedUndoContext.BeginTransaction("a name"))  
{   
    // Make changes here ....  
    t.Commit(); // Don't forget this!  
}  
```  
  
## <a name="containment"></a>Zawierania  
 ![ILayer i ILayerModel mogą zawierać ILayers. ](../modeling/media/layerapi-containment.png "LayerApi_Containment")  
  
 Warstwy (<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayer>) i warstwy modelu (<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerModel>) może zawierać komentarzy i warstwy.  
  
 Warstwy (`ILayer`) mogą być zawarte w modelu warstwy (`ILayerModel`) lub mogą być zagnieżdżone wewnątrz innego `ILayer`.  
  
 Aby utworzyć komentarz lub warstwę, należy użyć metod tworzenia odpowiedniego kontenera.  
  
## <a name="dependency-links"></a>Linki zależności  
 Łącze zależność jest reprezentowany przez obiekt. Może być przejście w dowolnym kierunku:  
  
 ![An ILayerDependencyLink connects two ILayers.](../modeling/media/layerapi-dependency.png "LayerApi_Dependency")  
  
 Aby utworzyć łącze zależności, należy wywołać `source.CreateDependencyLink(target)`.  
  
## <a name="comments"></a>Komentarze  
 Komentarze mogą być zawarte w warstwy lub warstwy modelu, a także mogą być połączone z dowolnego elementu warstwy:  
  
 ![Komentarze można dołączyć do dowolnego elementu warstwy. ](../modeling/media/layerapi-comments.png "LayerApi_Comments")  
  
 Komentarz można połączyć dowolną liczbę elementów, w tym none.  
  
 Aby uzyskać komentarze, które są dołączone do elementu warstwy, użyj:  
  
```csharp  
ILayerModel model = diagram.GetLayerModel();   
IEnumerable<ILayerComment> comments =   
   model.Comments.Where(comment =>   
      comment.Links.Any(link => link.Target == layerElement));  
  
```  
  
> [!CAUTION]
> `Comments` Właściwość `ILayer` pobiera komentarze, które są zawarte w `ILayer`. Serwer nie uzyska komentarze, które są połączone.  
  
 Komentarz można utworzyć za pomocą wywołania `CreateComment()` odpowiedniego kontenera.  
  
 Utwórz łącze przy użyciu `CreateLink()` na komentarz.  
  
## <a name="layer-elements"></a>Elementy warstwy  
 Wszystkie typy elementów, które mogą być zawarte w modelu są elementy warstwy:  
  
 ![Zawartość diagramu warstwy są ILayerElements. ](../modeling/media/layerapi-layerelements.png "LayerApi_LayerElements")  
  
## <a name="properties"></a>Właściwości  
 Każdy `ILayerElement` zawiera słownik parametrów o nazwie `Properties`. Aby dołączyć dowolnych informacji do dowolnego elementu warstwy, można użyć tego słownika.  
  
## <a name="artifact-references"></a>Odwołania do artefaktu  
 Odwołanie do artefaktu (<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerArtifactReference>) reprezentuje łącza między warstwą i elementu projektu, np. plik, klasy lub folderu. Użytkownik tworzy artefaktów, podczas tworzenia warstwy lub dodać do niego, przeciągając elementy z Eksploratora rozwiązań, widoku klas lub przeglądarki obiektów na diagram warstwy. Warstwę można połączyć dowolną liczbę odwołań artefaktu.  
  
 Każdy wiersz w Eksploratorze warstw zawiera odwołanie do artefaktu. Aby uzyskać więcej informacji, zobacz [tworzenie diagramów warstw z kodu](../modeling/create-layer-diagrams-from-your-code.md).  
  
 Główne typy i metody zaniepokojona artefaktu odwołania są następujące:  
  
 <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerArtifactReference>. Właściwość kategorie wskazuje, jaki rodzaj artefaktu mowa, takich jak klasy, plik wykonywalny lub zestawu. Kategorie określają, jak identyfikator identyfikuje artefaktu docelowego.  
  
 <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ArtifactReferenceExtensions.CreateArtifactReferenceAsync%2A> tworzy odwołanie do artefaktu z <xref:EnvDTE.Project> lub <xref:EnvDTE.ProjectItem>. To jest operacja asynchroniczna. W związku zazwyczaj zawierają wywołania zwrotnego, która jest wywoływana po zakończeniu tworzenia.  
  
 Nie należy mylić odwołania do artefaktu warstwy z artefaktów w diagramy przypadków użycia.  
  
## <a name="shapes-and-diagrams"></a>Kształty i diagramy  
 Dwa obiekty są używane do reprezentowania każdego elementu w modelu warstwy: <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerElement>i <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IShape>. `IShape` Reprezentuje położenia i rozmiaru kształtu na diagramie. W modelach warstwy co `ILayerElement` ma jeden `IShape`i co `IShape` na warstwie diagram ma jeden `ILayerElement`. `IShape` jest również używane dla modeli UML. W związku z tym nie każda `IShape` ma element warstwy.  
  
 W ten sam sposób <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerModel> jest wyświetlany na jednym <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IDiagram>.  
  
 W kodzie polecenia niestandardowego lub program obsługi gestu można uzyskać bieżącego diagramu i bieżącego zaznaczenia kształtów z `DiagramContext` importowania:  
  
```  
public class ... {  
[Import]  
    public IDiagramContext DiagramContext { get; set; }  
...  
public void ... (...)   
{ IDiagram diagram = this.DiagramContext.CurrentDiagram;  
  ILayerModel model = diagram.GetLayerModel();  
  if (model != null)  
  { foreach (ILayer layer in model.Layers) { ... }}  
  foreach (IShape selected in diagram.SelectedShapes)  
  { ILayerElement element = selected.GetLayerElement();  
    if (element != null) ... }}  
```  
  
 ![Każdy ILayerElement jest przedstawiony przez IShape. ](../modeling/media/layerapi-shapes.png "LayerApi_Shapes")  
  
 <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IShape> i <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IDiagram> są również używane do wyświetlania modeli UML. Aby uzyskać więcej informacji, zobacz [wyświetlanie modelu UML na diagramach](../modeling/display-a-uml-model-on-diagrams.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Dodawanie poleceń i gestów do diagramów warstw](../modeling/add-commands-and-gestures-to-layer-diagrams.md)   
 [Dodawanie niestandardowej walidacji architektury do diagramów warstw](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)   
 [Dodawanie właściwości niestandardowych do diagramów warstw](../modeling/add-custom-properties-to-layer-diagrams.md)   
 [Diagramy warstw: Odwołanie](../modeling/layer-diagrams-reference.md)   
 [Diagramy warstw: Wytyczne dotyczące](../modeling/layer-diagrams-guidelines.md)   
 [Rozszerzanie modeli i diagramów UML](../modeling/extend-uml-models-and-diagrams.md)
