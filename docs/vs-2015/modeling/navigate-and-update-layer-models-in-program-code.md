---
title: Nawigowanie i aktualizowanie modeli warstw w kodzie programu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- layer models, navigating in program code
- layer models, updating in program code
ms.assetid: c60edc87-33ee-4964-a954-40069f9febf3
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 88ab52f1b06e6a2da94d17225bdb26ecec358a6c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668574"
---
# <a name="navigate-and-update-layer-models-in-program-code"></a>Nawigowanie i aktualizowanie modeli warstw w kodzie programu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym temacie opisano elementy i relacje w modelach warstw, które można nawigować i aktualizować przy użyciu kodu programu. Aby uzyskać więcej informacji na temat diagramów warstwy z punktu widzenia użytkownika, zobacz [diagramy warstwowe: odwołania](../modeling/layer-diagrams-reference.md) i [diagramy warstwowe: wytyczne](../modeling/layer-diagrams-guidelines.md).

 `Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer`Model opisany w tym temacie jest elewacją dla bardziej ogólnego <xref:Microsoft.VisualStudio.GraphModel> modelu. Jeśli piszesz [polecenie menu lub rozszerzenie gestu](../modeling/add-commands-and-gestures-to-layer-diagrams.md), użyj `Layer` modelu. Jeśli piszesz [rozszerzenie warstwy sprawdzania poprawności](../modeling/add-custom-architecture-validation-to-layer-diagrams.md), łatwiej jest użyć `GraphModel` .

## <a name="transactions"></a>Transakcje
 Podczas aktualizowania modelu należy rozważyć zawrzeć zmiany w `ILinkedUndoTransaction` . Spowoduje to zagrupowanie zmian w jednej transakcji. W przypadku niepowodzenia zmiany cała transakcja zostanie wycofana. Jeśli użytkownik wycofa zmianę, wszystkie zmiany zostaną cofnięte.

 Aby uzyskać więcej informacji, zobacz [łączenie aktualizacji modelu UML przy użyciu transakcji](../modeling/link-uml-model-updates-by-using-transactions.md).

```
using (ILinkedUndoTransaction t =
        LinkedUndoContext.BeginTransaction("a name"))
{
    // Make changes here ....
    t.Commit(); // Don't forget this!
}
```

## <a name="containment"></a>Zawieranie
 ![ILayer i ILayerModel mogą zawierać ILayers.](../modeling/media/layerapi-containment.png "LayerApi_Containment")

 Warstwy ([ILayer](/previous-versions/ff644251(v=vs.140))) i model warstwy ([ILayerModel](/previous-versions/ff643069(v=vs.140))) mogą zawierać komentarze i warstwy.

 Warstwa ( `ILayer` ) może być zawarta w modelu warstwy ( `ILayerModel` ) lub może być zagnieżdżona w innym `ILayer` .

 Aby utworzyć komentarz lub warstwę, użyj metod tworzenia w odpowiednim kontenerze.

## <a name="dependency-links"></a>Linki zależności
 Łącze zależności jest reprezentowane przez obiekt. Można go nawigować w dowolnym kierunku:

 ![ILayerDependencyLink łączy dwa ILayers.](../modeling/media/layerapi-dependency.png "LayerApi_Dependency")

 Aby utworzyć łącze zależności, wywołaj polecenie `source.CreateDependencyLink(target)` .

## <a name="comments"></a>Komentarze
 Komentarze mogą być zawarte w warstwach lub modelu warstwy i mogą być również połączone z dowolnym elementem warstwy:

 ![Komentarze mogą być dołączane do dowolnego elementu warstwy.](../modeling/media/layerapi-comments.png "LayerApi_Comments")

 Komentarz może być połączony z dowolną liczbą elementów, łącznie z brakiem.

 Aby uzyskać komentarze dołączone do elementu warstwy, użyj:

```csharp
ILayerModel model = diagram.GetLayerModel();
IEnumerable<ILayerComment> comments =
   model.Comments.Where(comment =>
      comment.Links.Any(link => link.Target == layerElement));

```

> [!CAUTION]
> `Comments`Właściwość `ILayer` Pobiera komentarze, które są zawarte w `ILayer` . Nie otrzymuje komentarzy, które są z nim połączone.

 Utwórz komentarz wywołujący `CreateComment()` dla odpowiedniego kontenera.

 Utwórz link, używając `CreateLink()` na komentarzu.

## <a name="layer-elements"></a>Elementy warstwy
 Wszystkie typy elementów, które mogą być zawarte w modelu, są elementami warstwy:

 ![Zawartość diagramu warstwowego to ILayerElements.](../modeling/media/layerapi-layerelements.png "LayerApi_LayerElements")

## <a name="properties"></a>Właściwości
 Każdy `ILayerElement` z nich ma słownik ciągów o nazwie `Properties` . Tego słownika można użyć do dołączenia dowolnych informacji do dowolnego elementu warstwy.

## <a name="artifact-references"></a>Odwołania artefaktów
 Odwołanie artefaktu ([ILayerArtifactReference](/previous-versions/ff644536(v=vs.140))) reprezentuje łącze między warstwą a elementem projektu, takim jak plik, Klasa lub folder. Użytkownik tworzy artefakty podczas tworzenia warstwy lub dodawania do niej, przeciągając elementy z Eksplorator rozwiązań, Widok klasy lub Przeglądarka obiektów do diagramu warstwowego. Dowolna liczba odwołań artefaktów może być połączona z warstwą.

 Każdy wiersz w Eksploratorze warstwy wyświetla odwołanie artefaktu. Aby uzyskać więcej informacji, zobacz [Tworzenie diagramów warstwy na podstawie kodu](../modeling/create-layer-diagrams-from-your-code.md).

 Główne typy i metody z odwołaniami artefaktów są następujące:

 [ILayerArtifactReference](/previous-versions/ff644536(v=vs.140)). Właściwość Categories wskazuje, jaki rodzaj artefaktu jest przywoływany, taki jak Klasa, plik wykonywalny lub zestaw. Kategorie określają, jak identyfikator identyfikuje artefakt docelowy.

 [ArtifactReferenceExtensions. CreateArtifactReferenceAsync](/previous-versions/ff695840(v=vs.140)) tworzy odwołanie artefaktu z <xref:EnvDTE.Project> lub <xref:EnvDTE.ProjectItem> . To jest operacja asynchroniczna. W związku z tym, zazwyczaj podajesz wywołanie zwrotne, które jest wywoływane po zakończeniu tworzenia.

 Odwołań artefaktów warstwy nie należy mylić z artefaktami w diagramach przypadków użycia.

## <a name="shapes-and-diagrams"></a>Kształty i diagramy
 Dwa obiekty są używane do reprezentowania każdego elementu w modelu warstwy: `ILayerElement` a i [IShape](/previous-versions/ee806673(v=vs.140)). `IShape`Reprezentuje położenie i rozmiar kształtu na diagramie. W modelach warstw każdy `ILayerElement` ma jeden `IShape` , a każdy `IShape` na diagramie warstwy ma jeden `ILayerElement` . `IShape` jest również używany dla modeli UML. W związku z tym, nie każdy `IShape` ma elementu warstwy.

 W ten sam sposób `ILayerModel` jest wyświetlany w jednym [IDiagram](/previous-versions/ee789658(v=vs.140)).

 W kodzie niestandardowego polecenia lub uchwytu gestu można pobrać bieżący diagram i bieżące zaznaczenie kształtów z `DiagramContext` importowania:

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

 ![Każdy ILayerElement jest prezentowany przez IShape.](../modeling/media/layerapi-shapes.png)

 [IShape](/previous-versions/ee806673(v=vs.140)) i [IDiagram](/previous-versions/ee789658(v=vs.140)) są również używane do wyświetlania modeli UML. Aby uzyskać więcej informacji, zobacz [Wyświetlanie modelu UML na diagramach](../modeling/display-a-uml-model-on-diagrams.md).

## <a name="see-also"></a>Zobacz też

- [Dodawanie poleceń i gestów do diagramów warstw](../modeling/add-commands-and-gestures-to-layer-diagrams.md)
- [Dodawanie niestandardowej walidacji architektury do diagramów warstw](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)
- [Dodawanie właściwości niestandardowych do diagramów warstw](../modeling/add-custom-properties-to-layer-diagrams.md)
- [Diagramy warstw: informacje](../modeling/layer-diagrams-reference.md)
- [Diagramy warstw: wskazówki](../modeling/layer-diagrams-guidelines.md)
- [Rozszerzanie modeli i diagramów UML](../modeling/extend-uml-models-and-diagrams.md)
