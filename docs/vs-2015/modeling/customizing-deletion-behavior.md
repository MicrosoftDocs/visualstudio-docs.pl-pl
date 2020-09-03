---
title: Dostosowywanie zachowania dotyczącego usuwania | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.deletebehavior
helpviewer_keywords:
- Domain-Specific Language, deletion
ms.assetid: c6bf088d-52c6-4817-af45-ddae745bb5a9
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9d0dcfc5724e87d57d2803b9b64a6eb121314b99
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655043"
---
# <a name="customizing-deletion-behavior"></a>Dostosowywanie zachowania dotyczącego usuwania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Usunięcie elementu zwykle powoduje również usunięcie powiązanych elementów. Wszystkie połączone z nim relacje i wszystkie elementy podrzędne są usuwane. Takie zachowanie nazywa się *usuwaniem propagacji*. Można dostosować propagację usuwania, na przykład w celu rozmieszczenia dodatkowych powiązanych elementów. Pisząc kod programu, można sprawić, aby Propagacja usuwania zależała od stanu modelu. Można także spowodować, że inne zmiany będą wykonywane w odpowiedzi na usunięcie.

 Ten temat zawiera następujące sekcje:

- [Domyślne zachowanie usuwania](#default)

- [Ustawianie opcji propagowania usuwania roli](#property)

- [Zastępowanie zamknięcia usuwania](#closure) — Użyj tej techniki, w której usuwanie może prowadzić do usunięcia sąsiednich elementów.

- [Przy użyciu funkcji onDelete i](#ondeleting) OnAbort — Użyj tych metod, w których odpowiedź może obejmować inne akcje, takie jak aktualizowanie wartości wewnątrz lub na zewnątrz magazynu.

- [Reguły usuwania](#rules) — używanie reguł do propagowania aktualizacji dowolnego rodzaju w sklepie, w przypadku których jedna zmiana może prowadzić do innych operacji.

- [Zdarzenia usuwania](#rules) — używanie zdarzeń ze sklepu do propagowania aktualizacji poza magazynem, na przykład do innych [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] dokumentów.

- Cofnij [scalanie](#unmerge) — Użyj operacji cofania scalania, aby cofnąć operację scalania, która dołączyła element podrzędny do jego elementu nadrzędnego.

## <a name="default-deletion-behavior"></a><a name="default"></a> Domyślne zachowanie usuwania
 Domyślnie następujące reguły regulują propagację usuwania:

- Jeśli element zostanie usunięty, wszystkie osadzone elementy również zostaną usunięte. Elementy osadzone to te, które są obiektami docelowymi relacji osadzania, dla których ten element jest źródłem. Na przykład jeśli istnieje relacja osadzania z **albumu** do **piosenki**, po usunięciu określonego albumu wszystkie jego utwory również zostaną usunięte.

     Z kolei usunięcie utworu nie powoduje usunięcia tego albumu.

- Domyślnie usuwanie nie jest propagowane wraz z relacjami odwołań. Jeśli istnieje relacja odwołania **ArtistPlaysOnAlbum** z **albumu** do **wykonawcy**, usunięcie albumu nie powoduje usunięcia żadnego z nich i żadnego z nich.

     Jednak usuwanie jest propagowane wraz z niektórymi wbudowanymi relacjami. Na przykład po usunięciu elementu modelu jego kształt na diagramie również zostaje usunięty. Element i kształt są powiązane z `PresentationViewsSubject` relacją odwołania.

- Każda relacja, która jest połączona z elementem, w roli źródłowej lub docelowej, jest usuwana. Właściwość roli elementu w roli przeciwległej nie zawiera już usuniętego elementu.

## <a name="setting-the-propagate-delete-option-of-a-role"></a><a name="property"></a> Ustawianie opcji propagowania usuwania roli
 Można spowodować propagowanie operacji usuwania przy użyciu relacji odwołania lub osadzonego elementu podrzędnego z elementem nadrzędnym.

#### <a name="to-set-delete-propagation"></a>Aby ustawić propagację usuwania

1. Na diagramie definicji DSL wybierz *rolę* , do której ma zostać usunięta Propagacja. Rola jest reprezentowana przez wiersz po lewej lub po prawej stronie pola relacji domeny.

    Na przykład jeśli chcesz określić, że po każdym usunięciu albumu, powiązane artyści również zostaną usunięte, a następnie wybierz rolę połączoną z wykonawcą klasy domeny.

2. W okno Właściwości ustaw właściwość **propagowanie usuwania** .

3. Naciśnij klawisz F5 i sprawdź, czy:

   - Po usunięciu wystąpienia tej relacji element w wybranej roli również zostanie usunięty.

   - Po usunięciu elementu z przeciwległej roli wystąpienia tej relacji zostaną usunięte, a powiązane elementy w tej roli zostaną usunięte.

   W oknie **Szczegóły DSL** można także zobaczyć opcję **propagowanie usuwania** . Wybierz klasę domeny, a następnie w oknie Szczegóły DSL Otwórz stronę **zachowanie usuwania** , klikając przycisk po stronie okna. Opcja **Propaguj** jest wyświetlana dla przeciwległej roli każdej relacji. Kolumna **Usuń styl** wskazuje, czy opcja **Propaguj** jest ustawiona domyślnie, ale nie ma żadnego oddzielnego efektu.

## <a name="delete-propagation-by-using-program-code"></a>Usuwanie propagacji przy użyciu kodu programu
 Opcje w pliku definicji DSL pozwalają tylko określić, czy usunięcie propaguje do bezpośredniego sąsiada. Aby zaimplementować bardziej skomplikowany schemat do usuwania propagacji, można napisać kod programu.

> [!NOTE]
> Aby dodać kod programu do definicji DSL, Utwórz oddzielny plik kodu w projekcie **DSL** i Zapisz definicje częściowe, aby rozszerzyć klasy w folderze wygenerowanego kodu. Aby uzyskać więcej informacji, zobacz [pisanie kodu w celu dostosowywania języka specyficznego dla domeny](../modeling/writing-code-to-customise-a-domain-specific-language.md).

## <a name="defining-a-delete-closure"></a><a name="closure"></a> Definiowanie zamknięcia usuwania
 Operacja usuwania używa klasy _YourModel_**DeleteClosure** , aby określić, które elementy należy usunąć. Wywołuje `ShouldVisitRelationship()` i `ShouldVisitRolePlayer()` wielokrotnie, przenosząc Graf relacji. Można zastąpić te metody. ShouldVisitRolePlayer jest dostarczany z tożsamością linku i elementem w jednej z ról linku. Powinna zwracać jedną z następujących wartości:

- **VisitorFilterResult. Yes**— element powinien zostać usunięty i Analizator powinien wykonać próbę wykonania innych linków elementu.

- **VisitorFilterResult. DoNotCare** — nie należy usuwać elementu, chyba że inne odpowiedzi na zapytania, które powinny zostać usunięte.

- **VisitorFilterResult. Never** — nie można usunąć elementu, nawet jeśli inna kwerenda odpowiada **tak**, a Analizator nie powinien próbować innych linków elementu.

```
// When a musician is deleted, delete their albums with a low rating.
// Override methods in <YourDsl>DeleteClosure in DomainModel.cs
partial class MusicLibDeleteClosure
{
  public override VisitorFilterResult ShouldVisitRolePlayer
    (ElementWalker walker, ModelElement sourceElement, ElementLink elementLink,
    DomainRoleInfo targetDomainRole, ModelElement targetRolePlayer)
  {
    ArtistAppearsInAlbum link = elementLink as ArtistAppearsInAlbum;
    if (link != null
       && targetDomainRole.RolePlayer.Id == Album.DomainClassId)
    {
      // Count other unvisited links to the Album of this link.
      if (ArtistAppearsInAlbum.GetLinksToArtists(link.Album)
              .Where(linkAlbumArtist =>
                     linkAlbumArtist != link &&
                     !walker.Visited(linkAlbumArtist))
              .Count() == 0)
      {
        // Should delete this role player:
        return VisitorFilterResult.Yes;
      }
      else
        // Don’t delete unless another relationship deletes it:
        return VisitorFilterResult.DoNotCare;
    }
    else
    {
      // Test for and respond to other relationships and roles here.

      // Not the relationship or role we’re interested in.
      return base.ShouldVisitRolePlayer(walker, sourceElement,
             elementLink, targetDomainRole, targetRolePlayer);
    }
  }
}

```

 Technika zamykania zapewnia, że zestaw elementów i linków do usunięcia jest określany przed rozpoczęciem usuwania. Analizator łączy również wyniki zamknięcia z innymi częściami modelu.

 Jednak w technice przyjęto, że usunięcie ma wpływ tylko na jego sąsiadów na grafie relacji: nie można użyć tej metody do usunięcia elementu w innej części modelu. Nie można jej użyć, jeśli chcesz dodać elementy lub wprowadzić inne zmiany w odpowiedzi na usunięcie.

## <a name="using-ondeleting-and-ondeleted"></a><a name="ondeleting"></a> Korzystanie z funkcji onDelete i po usunięciu
 Można przesłonić `OnDeleting()` lub `OnDeleted()` albo w klasie domeny, albo w relacji domeny.

1. <xref:Microsoft.VisualStudio.Modeling.ModelElement.OnDeleting%2A> jest wywoływana, gdy element zostanie usunięty, ale zanim jego relacje zostały odłączone. Nadal jest nawigować do i z innych elementów i nadal znajduje się w `store.ElementDirectory` .

    Jeśli kilka elementów jest usuniętych w tym samym czasie, to po usunięciu zostanie wywołane wszystkie przed wykonaniem operacji usuwania.

    `IsDeleting` ma wartość true.

2. <xref:Microsoft.VisualStudio.Modeling.ModelElement.OnDeleted%2A> jest wywoływana, gdy element został usunięty. Pozostaje w stercie środowiska CLR, aby można było wykonać operację cofania w razie potrzeby, ale nie jest on połączony z innymi elementami i został usunięty z `store.ElementDirectory` . W przypadku relacji role nadal odwołują się do starych graczy ról.`IsDeleted` ma wartość true.

3. Po usunięciu elementu i po jego usunięciu są wywoływane, gdy użytkownik wywołuje polecenie Cofnij po utworzeniu obiektu, a wcześniejsze usunięcie zostanie powtórzone w ciągu wykonywania ponownie. Użyj `this.Store.InUndoRedoOrRollback` , aby uniknąć aktualizowania elementów sklepu w takich przypadkach. Aby uzyskać więcej informacji, zobacz [How to: use Transactions to updateing model](../modeling/how-to-use-transactions-to-update-the-model.md).

   Na przykład poniższy kod usuwa album, gdy ostatni utwór podrzędny jest usuwany:

```

// Delete the parent Album when the last Song is deleted.
// Override methods in the embedding relationship between Album and Song:
partial class AlbumHasSongs
{
  protected override void OnDeleted()
  {
    base.OnDeleted();
    // Don't perform in-store actions in undo:
    if (this.Store.InUndoRedoOrRollback) return;
    // Relationship source and target still work:
    // Don't bother if source is already on its way out:
    if (!this.Album.IsDeleting && !this.Album.IsDeleted)
    {
      if (this.Album.Songs.Count == 0)
      {
        this.Album.Delete();
} } } }

```

 Jest często bardziej przydatny do wyzwalania po usunięciu relacji niż element roli, ponieważ działa to zarówno po usunięciu elementu, jak i po usunięciu relacji. Jednak dla relacji odwołania można chcieć propagować usuwanie po usunięciu powiązanego elementu, ale nie w przypadku usunięcia relacji. Ten przykład umożliwia usunięcie albumu, gdy jego ostatni wykonawca zostanie usunięty, ale nie odpowiada, jeśli relacje zostały usunięte:

```
using System.Linq; ...
// Assumes a many-many reference relationship
// between Artist and Album.
partial class Artist
{
  protected override void OnDeleting()
  {
    base.OnDeleting();
    if (this.Store.InUndoRedoOrRollback) return;
    List<Album> toDelete = new List<Album>();
    foreach (Album album in this.Albums)
    {
      if (album.Artists.Where(artist => !artist.IsDeleting)
                        .Count() == 0)
      {
        toDelete.Add(album);
      }
    }
    foreach (Album album in toDelete)
    {
      album.Delete();
} } }

```

 Po wykonaniu <xref:Microsoft.VisualStudio.Modeling.ModelElement.Delete%2A> na elemencie zostanie wywołane polecenie onDelete, które zostało usunięte. Te metody są zawsze wykonywane wewnętrznie — to oznacza, bezpośrednio przed i po rzeczywistym usunięciu. Jeśli kod usuwa dwa lub więcej elementów, po ich usunięciu i onDelete zostanie wywołane zamienianie na wszystkie z nich.

## <a name="deletion-rules-and-events"></a><a name="rules"></a> Reguły usuwania i zdarzenia
 Jako alternatywę dla programów obsługi OnDelete można definiować reguły usuwania i zdarzenia usuwania.

1. **Usuwanie** i **usuwanie** reguł jest wyzwalane tylko w transakcji, a nie w operacji cofania ani ponawiania. Można ustawić, aby były umieszczane w kolejce do wykonania na końcu transakcji, w której jest wykonywane usuwanie. Usuwanie reguł jest zawsze wykonywane przed wszystkimi usuniętymi regułami, które znajdują się w kolejce.

     Użyj reguł, aby propagować zmiany, które mają wpływ tylko na elementy w sklepie, w tym relacje, elementy diagramu i ich właściwości. Typowo, reguła usuwania służy do propagowania usuwania, a reguła usuwania służy do tworzenia elementów zastępczych i relacji.

     Aby uzyskać więcej informacji, zobacz [reguły propagowanie zmian w modelu](../modeling/rules-propagate-changes-within-the-model.md).

2. **Usunięte** zdarzenie magazynu jest wywoływane na końcu transakcji i jest wywoływane po cofnięciu lub ponowieniu. W związku z tym może służyć do propagowania usunięć do obiektów spoza magazynu, takich jak pliki, wpisy w bazie danych lub inne obiekty w programie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

     Aby uzyskać więcej informacji, zobacz [programy obsługi zdarzeń propagują zmiany poza modelem](../modeling/event-handlers-propagate-changes-outside-the-model.md).

    > [!WARNING]
    > Po usunięciu elementu można uzyskać dostęp do jego wartości właściwości domeny, ale nie można nawigować w linki relacji. Jednak w przypadku ustawienia usuniętego zdarzenia w relacji można także uzyskać dostęp do dwóch elementów, które były swoimi graczami roli. W związku z tym, jeśli chcesz odpowiedzieć na usunięcie elementu modelu, ale chcesz uzyskać dostęp do elementu, do którego został on połączony, ustaw zdarzenie usuwania dla relacji zamiast z klasy domeny elementu modelu.

### <a name="example-deletion-rules"></a>Przykładowe reguły usuwania

```
[RuleOn(typeof(Album), FireTime = TimeToFire.TopLevelCommit)]
internal class AlbumDeletingRule : DeletingRule
{
  public override void ElementDeleting(ElementDeletingEventArgs e)
  {
    base.ElementDeleting(e);
    // ...perform tasks to propagate imminent deletion
  }
}
[RuleOn(typeof(Album), FireTime = TimeToFire.TopLevelCommit)]
internal class AlbumDeletedRule : DeleteRule
{
  public override void ElementDeleted(ElementDeletedEventArgs e)
  {
    base.ElementDeleted(e);
    // ...perform tasks such as creating new elements
  }
}

// The rule must be registered:
public partial class MusicLibDomainModel
{
  protected override Type[] GetCustomDomainModelTypes()
  {
    List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());
    types.Add(typeof(AlbumDeletingRule));
    types.Add(typeof(AlbumDeletedRule));
    // If you add more rules, list them here.
    return types.ToArray();
  }
}

```

### <a name="example-deleted-event"></a>Przykład usuniętego zdarzenia

```
partial class NestedShapesSampleDocData
{
  protected override void OnDocumentLoaded(EventArgs e)
  {
    base.OnDocumentLoaded(e);
    DomainRelationshipInfo commentRelationship =
          this.Store.DomainDataDirectory
          .FindDomainRelationship(typeof(CommentsReferenceComponents));

    this.Store.EventManagerDirectory.ElementDeleted.Add(commentRelationship,
      new EventHandler<ElementDeletedEventArgs>(CommentLinkDeleted));
  }

  private void CommentLinkDeleted (object sender, ElementDeletedEventArgs e)
  {
    CommentsReferenceComponents link = e.ModelElement as CommentsReferenceComponents;
    Comment comment = link.Comment;
    Component component = link.Subject;
    if (comment.IsDeleted)
    {
      // The link was deleted because the comment was deleted.
      System.Windows.Forms.MessageBox.Show("Removed comment on " + component.Name);
    }
    else
    {
      // It was just the link that was deleted - the comment itself remains.
      System.Windows.Forms.MessageBox.Show("Removed comment link to "
           + component.Name);
    }
  }
}

```

## <a name="unmerge"></a><a name="unmerge"></a> Anuluj scalenie
 Operacja dołączania elementu podrzędnego do jego elementu nadrzędnego jest nazywana *scalaniem*. Występuje po utworzeniu nowego elementu lub grupy elementów z przybornika lub przeniesieniu z innej części modelu lub skopiowaniu ze schowka. Oprócz tworzenia relacji osadzania między elementem nadrzędnym i jego nowym elementem podrzędnym, operacja scalania może również skonfigurować dodatkowe relacje, utworzyć elementy pomocnicze i ustawić wartości właściwości w elementach. Operacja scalania jest hermetyzowana w dyrektywie scalania elementów (EMD).

 EMD również hermetyzuje uzupełniające *niescalanie* lub `MergeDisconnect` operację. Jeśli masz klaster elementów, który został skonstruowany przy użyciu scalania, zaleca się użycie skojarzonej operacji unscalenia w celu usunięcia z niej elementu, jeśli chcesz pozostawić pozostałe elementy w spójnym stanie. Operacja rozscalania zwykle używa technik opisanych w poprzednich sekcjach.

 Aby uzyskać więcej informacji, zobacz [Dostosowywanie tworzenia i przenoszenia elementów](../modeling/customizing-element-creation-and-movement.md).

## <a name="see-also"></a>Zobacz też
 [Dostosowywanie zachowania kopiowania](../modeling/customizing-copy-behavior.md) [dostosowanie tworzenia elementu i przenoszenie](../modeling/customizing-element-creation-and-movement.md) [kodu w celu dostosowania języka specyficznego dla domeny](../modeling/writing-code-to-customise-a-domain-specific-language.md)
