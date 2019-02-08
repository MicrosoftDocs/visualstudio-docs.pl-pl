---
title: Nawigowanie i aktualizowanie modeli warstw w kodzie programu
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- layer models, navigating in program code
- layer models, updating in program code
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d74501a45fe3f6a40b8b64cd0b1da3f07a69bde1
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55923320"
---
# <a name="navigate-and-update-layer-models-in-program-code"></a>Nawigowanie i aktualizowanie modeli warstw w kodzie programu

W tym artykule opisano elementy i relacje w modelach warstwy, które można znaleźć i zaktualizować przy użyciu kodu programu. Aby uzyskać więcej informacji dotyczących diagramów zależności z punktu widzenia użytkownika, zobacz [diagramy zależności: Odwołanie](../modeling/layer-diagrams-reference.md) i [diagramy zależności: Wytyczne dotyczące](../modeling/layer-diagrams-guidelines.md).

<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer> Modelu opisane w tym temacie jest fasada w bardziej ogólnej <xref:Microsoft.VisualStudio.GraphModel> modelu. Jeśli piszesz [rozszerzenie menu polecenia lub gestu](../modeling/add-commands-and-gestures-to-layer-diagrams.md), użyj `Layer` modelu. Jeśli piszesz [rozszerzenie sprawdzania poprawności warstwy](../modeling/add-custom-architecture-validation-to-layer-diagrams.md), jest łatwiejszy w obsłudze `GraphModel`.

## <a name="transactions"></a>Transakcje

Po zaktualizowaniu modelu należy wziąć pod uwagę zmiany w załączonym `ILinkedUndoTransaction`, które grupy zmian jako jedna transakcja. Jeśli zmiany zakończy się niepowodzeniem, cała transakcja zostanie wycofana. Jeśli użytkownik spowoduje cofnięcie zmian, wszystkie zmiany zostaną cofnięte w ze sobą.

```csharp
using (ILinkedUndoTransaction t =
        LinkedUndoContext.BeginTransaction("a name"))
{
    // Make changes here ....
    t.Commit(); // Don't forget this!
}
```

## <a name="containment"></a>Zawierania

![ILayer i ILayerModel mogą zawierać ILayers.](../modeling/media/layerapi_containment.png)

Warstwy (<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayer>) i warstwy modelu (<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerModel>) może zawierać komentarzy i warstwy.

Warstwy (`ILayer`) mogą być zawarte w modelu warstwy (`ILayerModel`) lub mogą być zagnieżdżone wewnątrz innego `ILayer`.

Aby utworzyć komentarz lub warstwę, należy użyć metod tworzenia odpowiedniego kontenera.

## <a name="dependency-links"></a>Linki zależności

Łącze zależność jest reprezentowany przez obiekt. Może być przejście w dowolnym kierunku:

![ILayerDependencyLink łączy dwie ILayers.](../modeling/media/layerapi_dependency.png)

Aby utworzyć łącze zależności, należy wywołać `source.CreateDependencyLink(target)`.

## <a name="comments"></a>Komentarze

Komentarze mogą być zawarte w warstwy lub warstwy modelu, a także mogą być połączone z dowolnego elementu warstwy:

![Komentarze można dołączyć do dowolnego elementu warstwy.](../modeling/media/layerapi_comments.png)

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

Komentarz utworzyć przez wywołanie metody `CreateComment()` odpowiedniego kontenera.

Utwórz łącze przy użyciu `CreateLink()` na komentarz.

## <a name="layer-elements"></a>Elementy warstwy

Wszystkie typy elementów, które mogą być zawarte w modelu są elementy warstwy:

![zawartość diagram zależności jest ILayerElements.](../modeling/media/layerapi_layerelements.png)

## <a name="properties"></a>Właściwości

Każdy `ILayerElement` zawiera słownik parametrów o nazwie `Properties`. Aby dołączyć dowolnych informacji do dowolnego elementu warstwy, można użyć tego słownika.

## <a name="artifact-references"></a>Odwołania do artefaktu

Odwołanie do artefaktu (<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerArtifactReference>) reprezentuje łącza między warstwą i elementu projektu, np. plik, klasy lub folderu. Użytkownik tworzy artefaktów, podczas tworzenia warstwy lub dodać do niego, przeciągając elementy z Eksploratora rozwiązań, widoku klas lub przeglądarki obiektów na diagram zależności. Warstwę można połączyć dowolną liczbę odwołań artefaktu.

Każdy wiersz w Eksploratorze warstw zawiera odwołanie do artefaktu. Aby uzyskać więcej informacji, zobacz [tworzenie diagramów zależności z kodu](../modeling/create-layer-diagrams-from-your-code.md).

Główne typy i metody zaniepokojona artefaktu odwołania są następujące:

<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerArtifactReference>. Właściwość kategorie wskazuje, jaki rodzaj artefaktu mowa, takich jak klasy, plik wykonywalny lub zestawu. Właściwość kategorii określa, jak identyfikator identyfikuje artefaktu docelowego.

<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ArtifactReferenceExtensions.CreateArtifactReferenceAsync%2A> tworzy odwołanie do artefaktu z <xref:EnvDTE.Project> lub <xref:EnvDTE.ProjectItem>. To jest operacja asynchroniczna. W związku zazwyczaj zawierają wywołania zwrotnego, która jest wywoływana po zakończeniu tworzenia.

Odwołania do artefaktu warstwy różnią się do artefaktów w diagramy przypadków użycia.

## <a name="shapes-and-diagrams"></a>Kształty i diagramy

Dwa obiekty są używane do reprezentowania każdego elementu w modelu warstwy: <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerElement>i <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IShape>. `IShape` Reprezentuje położenia i rozmiaru kształtu na diagramie. W modelach warstwy co `ILayerElement` ma jeden `IShape`i co `IShape` na zależność diagram ma jeden `ILayerElement`. `IShape` jest również używane dla modeli UML. W związku z tym nie każda `IShape` ma element warstwy.

W ten sam sposób <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerModel> jest wyświetlany na jednym <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IDiagram>.

W kodzie polecenia niestandardowego lub program obsługi gestu można uzyskać bieżącego diagramu i bieżącego zaznaczenia kształtów z `DiagramContext` importowania:

```csharp
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

![Każdy ILayerElement jest przedstawiony przez IShape.](../modeling/media/layerapi_shapes.png)

<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IShape> i <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IDiagram> są również używane do wyświetlania modeli UML.

## <a name="see-also"></a>Zobacz też

- [Dodawanie poleceń i gestów do diagramów zależności](../modeling/add-commands-and-gestures-to-layer-diagrams.md)
- [Dodawanie niestandardowej walidacji architektury do diagramów zależności](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)
- [Dodawanie właściwości niestandardowych do diagramów zależności](../modeling/add-custom-properties-to-layer-diagrams.md)
- [Diagramy zależności: Odwołanie](../modeling/layer-diagrams-reference.md)
- [Diagramy zależności: Wytyczne dotyczące](../modeling/layer-diagrams-guidelines.md)
