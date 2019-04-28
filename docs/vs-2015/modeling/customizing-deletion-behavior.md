---
title: Dostosowywanie zachowania dotyczącego usuwania | Dokumentacja firmy Microsoft
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: fa7db2f55a89bd6c542bff0cf30ee058e339f15c
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63433287"
---
# <a name="customizing-deletion-behavior"></a>Dostosowywanie zachowania dotyczącego usuwania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Usuwanie elementu zwykle powoduje, że powiązanych elementów można również usunąć. Wszystkie relacje dołączone do niego, a wszystkie elementy podrzędne są usuwane. To zachowanie jest o nazwie *Usuń propagacji*. Można dostosować propagacji delete, na przykład aby rozmieścić, że dodatkowe powiązane elementy zostaną usunięte. Pisząc kod programu, można wprowadzić propagacji delete zależą od stanu modelu. Może również spowodować inne zmiany w odpowiedzi na usunięcie.  
  
 Ten temat zawiera następujące sekcje:  
  
- [Domyślne zachowanie usunięcia](#default)  
  
- [Ustawianie opcji Propaguj usuwanie roli](#property)  
  
- [Zastępowanie zamknięcia Usuń](#closure) — Użyj tej techniki, w którym usunięcie może prowadzić do usunięcia między sąsiednimi elementami.  
  
- [Przy użyciu OnDeleting i OnDeleted](#ondeleting) — użycia tych metod, w którym odpowiedź może obejmować inne akcje, takie jak aktualizowanie wartości lub spoza sklepu.  
  
- [Reguły usuwania](#rules) — Użyj reguł propagacji aktualizacji do dowolnego rodzaju, w magazynie, gdzie jednej zmiany może prowadzić do innych osób.  
  
- [Usunięcie zdarzenia](#rules) — zdarzenia magazynu Użyj propagacji aktualizacji poza magazynu, na przykład do innych [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] dokumentów.  
  
- [Rozdziel](#unmerge) — użyj operacji Rozdziel do cofania operacji scalania, który dołączony element podrzędny do elementu nadrzędnego.  
  
## <a name="default"></a> Domyślne zachowanie usunięcia  
 Domyślnie Usuń propagacji decydują następujące reguły:  
  
- Jeśli element zostanie usunięty, również zostaną usunięte wszystkie elementy osadzone. Osadzone elementy są te, które są elementy docelowe relacji, dla których ten element jest źródło osadzenia. Na przykład, jeśli istnieje relacja osadzania z **albumu** do **utworu**, a następnie usunięcie określonego albumu jego utwory również zostaną usunięte.  
  
     Z drugiej strony usunięcie utwór nie powoduje usunięcia albumu.  
  
- Domyślnie usunięcie nie propaguje wzdłuż relacje odniesienia. Jeśli istnieje relacja odwołania **ArtistPlaysOnAlbum** z **albumu** do **wykonawcy**, usunięcie albumu nie powoduje usunięcia żadnych powiązanych wykonawcy i usuwanie wykonawca nie Usuń wszelkie albumu.  
  
     Jednak usunięcie propagować wzdłuż niektórych wbudowanych relacji. Na przykład gdy element modelu zostanie usunięty, jego kształt na diagramie są także usuwane. Element i kształt, które są powiązane przez `PresentationViewsSubject` odwoływać się do relacji.  
  
- Każda relacja, która jest podłączony do elementu w roli źródłowej lub docelowej zostaną usunięte. Właściwości roli elementu wskazywanego przez rolę odwrotną nie zawiera już usuniętego elementu.  
  
## <a name="property"></a> Ustawianie opcji Propaguj usuwanie roli  
 Może spowodować usunięcie Propagacja wzdłuż relacja odwołania lub z osadzonych obiektów podrzędnych z jego elementu nadrzędnego.  
  
#### <a name="to-set-delete-propagation"></a>Aby ustawić propagacji delete  
  
1. Na diagramie definicji DSL zaznacz *roli* do której należy propagacji do usunięcia. Rola jest reprezentowany przez linię po lewej stronie lub z prawej strony pola relacji domeny.  
  
    Na przykład jeśli chcesz określić, że natychmiast po usunięciu albumu wykonawców powiązanych również zostaną usunięte, a następnie wybierz rolę podłączone do klasy domeny wykonawcy.  
  
2. W oknie właściwości ustaw **propaguje usunąć** właściwości.  
  
3. Naciśnij klawisz F5, a następnie upewnij się, że:  
  
   - Usunięcie wystąpienia tej relacji do elementu w wybranej roli, również zostaną usunięte.  
  
   - Po usunięciu elementu na rolę odwrotną wystąpienia tej relacji zostaną usunięte, a powiązane elementy w tej roli zostaną usunięte.  
  
   Można również wyświetlić **propaguje Usuń** opcji **szczegóły języka DSL** okna. Zaznacz klasę domeny, a następnie w oknie Szczegóły języka DSL Otwórz **zachowanie usuwaniu** strony, klikając przycisk na stronie okna. **Propagacja** opcja jest wyświetlana przeciwny roli każdej relacji. **Usuń styl** kolumna wskazuje, czy **Propagacja** opcja jest na ustawienie domyślne, ale nie ma żadnego efektu oddzielne.  
  
## <a name="delete-propagation-by-using-program-code"></a>Usuń propagacji przy użyciu kodu programu  
 Opcje w pliku definicji DSL umożliwiają tylko wybrać, czy usunięcie propaguje do natychmiastowego sąsiada. Aby zaimplementować bardziej złożone schemat propagacji delete, można pisać kod programu.  
  
> [!NOTE]
> Aby dodać kod programu do swojej definicji DSL, Utwórz plik osobnego kodu w **Dsl** projektu, a następnie zapisz definicje częściowe rozszerzyć klasy w folderze wygenerowany kod. Aby uzyskać więcej informacji, zobacz [pisanie kodu pod kątem dostosowywania języka specyficznego dla domeny](../modeling/writing-code-to-customise-a-domain-specific-language.md).  
  
## <a name="closure"></a> Definiowanie zamknięcia Delete  
 Operacja usunięcia używa klasy _YourModel_**DeleteClosure** ustalenie, które elementy, aby usunąć, biorąc pod uwagę wartości początkowe. Wywołuje `ShouldVisitRelationship()` i `ShouldVisitRolePlayer()` wielokrotnie, zalet Graf relacji. Można zastąpić tych metod. ShouldVisitRolePlayer znajduje się za pomocą tożsamości łącze i element w jednej z ról łącza. Powinien zostać zwrócony jeden z następujących wartości:  
  
- **VisitorFilterResult.Yes**— element powinien zostać usunięty, i walker należy kontynuować do wypróbowania elementu przez inne łącza.  
  
- **VisitorFilterResult.DoNotCare** — element nie powinny być usuwane, chyba że inne zapytanie odpowiedzi na to, że go usunąć.  
  
- **VisitorFilterResult.Never** — element nie należy usuwać, nawet wtedy, gdy inne zapytanie odpowiedzi **tak**, i nie walker elementu przez inne łącza.  
  
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
  
 Technika zamknięcia gwarantuje, że zestaw elementów i łącza do usunięcia jest określana, przed rozpoczęciem usuwania. Walker również łączy wyniki Twojego zamknięcia z tymi z innymi częściami modelu.  
  
 Jednak technika przyjęto założenie, które usunięcia wpływa tylko jego sąsiadami na wykresie relacje: nie można użyć tej metody można usunąć elementu w innej części modelu. Nie można używać go, jeśli chcesz dodać elementy, lub wprowadzić inne zmiany w odpowiedzi na usunięcie.  
  
## <a name="ondeleting"></a> Przy użyciu OnDeleting i OnDeleted  
 Można zastąpić `OnDeleting()` lub `OnDeleted()` klasy domeny lub w relacji domeny.  
  
1. <xref:Microsoft.VisualStudio.Modeling.ModelElement.OnDeleting%2A> jest wywoływana, gdy element ma zostać usunięty, ale zanim odłączony relacje. Nadal można nawigować do i z innych elementów i nadal znajduje się w `store.ElementDirectory`.  
  
    Usunięcie kilku elementów w tym samym czasie OnDeleting jest wywoływana dla wszystkich z nich przed wykonaniem operacji usuwania.  
  
    `IsDeleting` ma wartość true.  
  
2. <xref:Microsoft.VisualStudio.Modeling.ModelElement.OnDeleted%2A> jest wywoływana, gdy element został usunięty. Pozostaje w stosie CLR, aby cofania mogą być wykonywane, jeśli jest to wymagane, ale jest rozłączony od innych elementów i usunięty z `store.ElementDirectory`. W przypadku relacji role nadal odwoływać się do starej obiekty pełniące role.`IsDeleted` ma wartość true.  
  
3. OnDeleting i OnDeleted są wywoływane, gdy użytkownik wywołuje cofania po utworzeniu elementu i wcześniejsze usunięcie jest powtarzany w ponawiania. Użyj `this.Store.InUndoRedoOrRollback` w celu uniknięcia aktualizowania elementów Sklepu w tych przypadkach. Aby uzyskać więcej informacji, zobacz [jak: Użycie transakcji do aktualizacji modelu](../modeling/how-to-use-transactions-to-update-the-model.md).  
  
   Na przykład poniższy kod usuwa albumu po usunięciu jej ostatniego elementu podrzędnego utworu:  
  
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
  
 Jest często bardziej przydatne do wyzwalacza przed usunięciem relacji od elementu roli, ponieważ to działa zarówno, gdy element zostanie usunięty, a po usunięciu samą relację. W przypadku relacji odwołania może być do propagowania usunięcie po usunięciu elementów powiązanych, ale nie w przypadku, gdy zostanie usunięty sam relacji. W tym przykładzie usuwa albumu podczas jego ostatniej wykonawcy mającym swój wkład zostanie usunięty, ale nie odpowiada, jeśli relacje zostaną usunięte:  
  
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
  
 Jeśli wykonujesz <xref:Microsoft.VisualStudio.Modeling.ModelElement.Delete%2A> w elemencie OnDeleting i OnDeleted zostanie wywołana. Te metody są zawsze wykonywane wbudowane — oznacza to, bezpośrednio przed i po usunięciu rzeczywistych. Jeśli Twój kod usuwa co najmniej dwa elementy, OnDeleting i OnDeleted zostanie wywołana w zmiany na wszystkich z nich z osobna.  
  
## <a name="rules"></a> Reguły usuwania i zdarzenia  
 Jako alternatywę do obsługi OnDelete można zdefiniować reguły usuwania i usuwania zdarzenia.  
  
1. **Usuwanie** i **Usuń** zasady są wyzwalane tylko w ramach transakcji, a nie w cofania i ponawiania. Można ustawić je do umieszczone w kolejce do wykonania na końcu transakcji, w którym odbywa się usunięcie. Usuwanie reguły są zawsze wykonywane przed wszystkie reguły usuniętych, które znajdują się w kolejce.  
  
     Przy użyciu reguł propagujące zmiany, które wpływają na tylko elementy w magazynie, w tym relacje, elementami diagramu i ich właściwości. Zazwyczaj reguły usuwanie jest używany do propagowania usunięcia, a reguła usuwania służy do tworzenia, zamieniania elementów i relacji.  
  
     Aby uzyskać więcej informacji, zobacz [reguły propagowanie zmian w modelu](../modeling/rules-propagate-changes-within-the-model.md).  
  
2. **Usunięto** magazyn zdarzeń jest wywoływany pod koniec transakcji i jest wywoływana po cofania i ponawiania. W związku z tym można jej do propagowania usunięcia obiektów poza magazynu, takich jak pliki, wpisów bazy danych lub innych obiektów w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
     Aby uzyskać więcej informacji, zobacz [obsługi propagowanie zmian poza Model zdarzeń](../modeling/event-handlers-propagate-changes-outside-the-model.md).  
  
    > [!WARNING]
    > Po usunięciu elementu dostęp można uzyskać wartości właściwości domeny, ale nie można nawigować relacji łączy. Jednak jeśli ustawisz to zdarzenie usunięte na relacji, można także przejść dwa elementy, które były jej obiekty pełniące role. W związku z tym jeśli chcesz odpowiedzieć na usunięcie elementu modelu, ale chcesz uzyskiwanie dostępu do elementu, do którego został połączony nastavit zdarzenie usuwania relacji, a nie klasę domeny elementu modelu.  
  
### <a name="example-deletion-rules"></a>Przykład usunięcia reguły  
  
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
  
### <a name="example-deleted-event"></a>Przykładowe zdarzenie usunięte  
  
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
  
## <a name="unmerge"></a> Rozdziel  
 Operacja, która dołącza element podrzędny do elementu nadrzędnego jest nazywany *scalania*. Występuje, gdy nowy element lub utworzone z przybornika lub przeniesione z inną częścią modelu lub kopiowane ze Schowka grupy elementów. Oraz utworzenie relacji osadzania między nadrzędnym a jego nowy element podrzędny, operacji scalania można również skonfigurować dodatkowe relacje, tworzyć elementy pomocnicze i ustaw wartości właściwości w elementach. Operacja scalania jest hermetyzowany w dyrektywie scalania elementów (EMD).  
  
 Również EMD hermetyzuje uzupełniające *Rozdziel* lub `MergeDisconnect` operacji. W przypadku klastra elementów, który został skonstruowany przy użyciu scalanie zalecane jest użycie skojarzonego Rozdziel do usunięcia elementu z niego, jeśli chcesz pozostawić wszystkie pozostałe elementy w spójnym stanie. Operacja Rozdziel zazwyczaj będzie używać metod opisanych w poprzednich sekcjach.  
  
 Aby uzyskać więcej informacji, zobacz [Dostosowywanie tworzenia i przesuwania elementu](../modeling/customizing-element-creation-and-movement.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Dostosowywanie zachowania dotyczącego kopiowania](../modeling/customizing-copy-behavior.md)   
 [Dostosowywanie tworzenia i przesuwania elementu](../modeling/customizing-element-creation-and-movement.md)   
 [Pisanie kodu pod kątem dostosowywania języka specyficznego dla domeny](../modeling/writing-code-to-customise-a-domain-specific-language.md)
