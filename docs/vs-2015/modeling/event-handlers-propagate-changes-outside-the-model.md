---
title: Programy obsługi zdarzeń propagujące zmiany poza modelem | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
- Domain-Specific Language, events
ms.assetid: 0ac8d1e4-239f-4370-ba1d-3769bb38b8a5
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 24ef57b545360cccbf75039b5f64a0f53e636dd8
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60059906"
---
# <a name="event-handlers-propagate-changes-outside-the-model"></a>Programy obsługi zdarzeń propagujące zmiany poza modelem
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W wizualizacji i modelowania SDK, można zdefiniować programy obsługi zdarzeń sklepu propagowanie zmian do zasobów spoza sklepu, takie jak zmienne-store, plików i modeli w innych magazynach lub inne [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozszerzenia. Programy obsługi zdarzeń Store są wykonywane po zakończeniu transakcji, w którym wystąpiło zdarzenie wyzwalania. Są one również wykonywane w operacji cofania i ponawiania. W związku z tym w przeciwieństwie do reguł magazynu zdarzenia magazynu są najbardziej przydatne w przypadku aktualizowania wartości spoza sklepu. W przeciwieństwie do zdarzenia platformy .NET, procedury obsługi zdarzeń w magazynie są zarejestrowane do nasłuchiwania na klasę: nie trzeba zarejestrować oddzielne obsługi dla każdego wystąpienia. Aby uzyskać więcej informacji o tym, jak dokonać wyboru między różne sposoby obsługi zmian, zobacz [reagowania na zagrożenia i propagowanie zmian](../modeling/responding-to-and-propagating-changes.md).  
  
 Powierzchnia graficznego i innych kontrolek interfejsu użytkownika są przykładami zasobów zewnętrznych, które są obsługiwane przez zdarzenia magazynu.  
  
### <a name="to-define-a-store-event"></a>Aby zdefiniować zdarzenia magazynu  
  
1. Wybierz typ zdarzenia, które chcesz monitorować. Aby uzyskać pełną listę, Przyjrzyj się właściwości <xref:Microsoft.VisualStudio.Modeling.EventManagerDirectory>. Każda właściwość odnosi się do typu zdarzenia. Najczęściej używane zdarzenia, które typy to:  
  
   - `ElementAdded` — wyzwalane, gdy element modelu, relacji łączy, kształtu lub połączenia jest tworzony.  
  
   - ElementPropertyChanged — wyzwalane, gdy wartość `Normal` właściwość domeny zostanie zmieniony. Zdarzenie jest wyzwalane tylko wtedy, gdy wartości nowym i starym nie są równe. Nie można zastosować zdarzenie do obliczone i niestandardowe właściwości przechowywania.  
  
        Nie można zastosować do właściwości roli, które odnoszą się do relacji łączy. Zamiast tego należy użyć `ElementAdded` do monitorowania relacji domeny.  
  
   - `ElementDeleted` — wyzwalane po elementu modelu, relacji, kształtu lub łącznik został usunięty. Nadal możesz uzyskać dostępu do wartości właściwości elementu, ale będzie mieć żadnych relacji z innymi elementami.  
  
2. Dodaj definicję klasy częściowej _YourDsl_**DocData** w osobnym pliku kodu w **DslPackage** projektu.  
  
3. Jako metodę jak w poniższym przykładzie, należy napisać kod zdarzenia. Może być `static`, chyba że chcesz uzyskać dostęp do `DocData`.  
  
4. Zastąp `OnDocumentLoaded()` zarejestrować program obsługi. Jeśli masz więcej niż jeden program obsługi, można zarejestrować je w tym samym miejscu.  
  
   Lokalizacja kodu rejestracji nie jest krytyczny. `DocView.LoadView()` jest alternatywną lokalizację.  
  
```  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using Microsoft.VisualStudio.Modeling;  
  
namespace Company.MusicLib  
{  
  partial class MusicLibDocData  
  {  
    // Register store events here or in DocView.LoadView().  
    protected override void OnDocumentLoaded()  
    {  
      base.OnDocumentLoaded(); // Don’t forget this.  
  
      #region Store event handler registration.       
      Store store = this.Store;  
      EventManagerDirectory emd = store.EventManagerDirectory;  
      DomainRelationshipInfo linkInfo = store.DomainDataDirectory  
          .FindDomainRelationship(typeof(ArtistAppearsInAlbum));  
      emd.ElementAdded.Add(linkInfo,   
          new EventHandler<ElementAddedEventArgs>(AddLink));  
      emd.ElementDeleted.Add(linkInfo,   
          new EventHandler<ElementDeletedEventArgs>(RemoveLink));  
  
      #endregion Store event handlers.  
    }  
  
    private void AddLink(object sender, ElementAddedEventArgs e)  
    {  
      ArtistAppearsInAlbum link = e.ModelElement as ArtistAppearsInAlbum;  
      if (link != null)   
            ExternalDatabase.Add(link.Artist.Name, link.Album.Title);  
    }  
    private void RemoveLink(object sender, ElementDeletedEventArgs e)  
    {  
      ArtistAppearsInAlbum link = e.ModelElement as ArtistAppearsInAlbum;  
      if (link != null)   
            ExternalDatabase.Delete(link.Artist.Name, link.Album.Title);  
    }  
  }  
  
}  
  
```  
  
## <a name="using-events-to-make-undoable-adjustments-in-the-store"></a>Korygowanie można cofnąć Store za pomocą zdarzeń  
 Zdarzenia Store nie zwykle służą do propagowanie zmian w magazynie, ponieważ program obsługi zdarzeń jest wykonywana po transakcja została zatwierdzona. Zamiast tego należy użyć reguły magazynu. Aby uzyskać więcej informacji, zobacz [reguły propagowanie zmian w modelu](../modeling/rules-propagate-changes-within-the-model.md).  
  
 Jednak można program obsługi zdarzeń dokonać dodatkowych aktualizacji do magazynu, jeśli chcesz, aby użytkownik będzie mógł cofnąć dodatkowe aktualizacje, niezależnie od oryginalnego zdarzeń. Załóżmy na przykład, czy małych liter standardowej konwencji tytułów albumu. Można napisać program obsługi zdarzenia magazynu, który poprawia tytuł na małe litery, po użytkownik wpisał go napisane wielkimi literami. Jednak użytkownik wystarczą polecenia Cofnij do anulowania poprawkę, przywracanie wielkie litery. Drugi cofania spowoduje usunięcie zmiany przez użytkownika.  
  
 Z drugiej strony, jeśli napiszesz zasadę magazynu, aby zrobić to samo, zmiany użytkownika oraz poprawki będą w ramach jednej transakcji, dzięki czemu użytkownik nie może cofnąć dostosowania bez utraty zmian oryginalnego.  
  
```  
  
partial class MusicLibDocView  
{  
    // Register store events here or in DocData.OnDocumentLoaded().  
    protected override void LoadView()  
    {  
      /* Register store event handler for Album Title property. */  
      // Get reflection data for property:  
      DomainPropertyInfo propertyInfo =   
        this.DocData.Store.DomainDataDirectory  
        .FindDomainProperty(Album.TitleDomainPropertyId);  
      // Add to property handler list:  
      this.DocData.Store.EventManagerDirectory  
        .ElementPropertyChanged.Add(propertyInfo,  
        new EventHandler<ElementPropertyChangedEventArgs>  
             (AlbumTitleAdjuster));  
  
      /*  
      // Alternatively, you can set one handler for   
      // all properties of a class.  
      // Your handler has to determine which property changed.  
      DomainClassInfo classInfo = this.Store.DomainDataDirectory  
           .FindDomainClass(typeof(Album));  
      this.Store.EventManagerDirectory  
          .ElementPropertyChanged.Add(classInfo,  
        new EventHandler<ElementPropertyChangedEventArgs>  
             (AlbumTitleAdjuster));  
       */  
      return base.LoadView();  
    }  
  
// Undoable adjustment after a property is changed.   
// Method can be static since no local access.  
private static void AlbumTitleAdjuster(object sender,  
         ElementPropertyChangedEventArgs e)  
{  
  Album album = e.ModelElement as Album;  
  Store store = album.Store;  
  
  // We mustn't update the store in an Undo:  
  if (store.InUndoRedoOrRollback   
      || store.InSerializationTransaction)  
      return;  
  
  if (e.DomainProperty.Id == Album.TitleDomainPropertyId)  
  {  
    string newValue = (string)e.NewValue;  
    string lowerCase = newValue.ToLowerInvariant();  
    if (!newValue.Equals(lowerCase))  
    {  
      using (Transaction t = store.TransactionManager  
            .BeginTransaction("adjust album title"))  
      {  
        album.Title = lowerCase;  
        t.Commit();  
      } // Beware! This could trigger the event again.  
    }  
  }  
  // else other properties of this class.  
}  
  
```  
  
 Jeśli piszesz zdarzenie, które aktualizuje magazynu:  
  
- Użyj `store.InUndoRedoOrRollback` Aby uniknąć wprowadzania zmian do elementów modelu w cofania. Menedżer transakcji ustawi wszystko w magazynie do stanu pierwotnego.  
  
- Użyj `store.InSerializationTransaction` Aby uniknąć wprowadzania zmian, gdy model jest ładowany z pliku.  
  
- Zmiany spowoduje dalsze zdarzenia wyzwolone. Upewnij się, że należy unikać wejścia w nieskończoną pętlę.  
  
## <a name="store-event-types"></a>Typy zdarzeń Store  
 Każdy typ zdarzenia odpowiada kolekcji w Store.EventManagerDirectory. Można dodawać lub usuwać procedury obsługi zdarzeń w dowolnym czasie, ale jest zwykle, aby dodać je, gdy jest ładowany dokument.  
  
|`EventManagerDirectory` Nazwa właściwości|Kiedy wykonywane|  
|-------------------------------------------|-------------------|  
|ElementAdded|Tworzone jest wystąpienie klasy domeny, relacji domeny, kształt, łącznika lub diagramu.|  
|ElementDeleted|Element modelu została usunięta z katalogu elementów sklepu i nie jest już źródłowych lub docelowych żadnych relacji. Element faktycznie nie zostanie usunięta z pamięci, ale jest zachowane w przypadku przyszłych cofania.|  
|ElementEventsBegun|Wywoływane na końcu transakcji zewnętrznym.|  
|ElementEventsEnded|Wywoływane, gdy zostaną przetworzone wszystkie inne zdarzenia.|  
|ElementMoved|Element modelu została przeniesiona z jednego magazynu partycji do innej.<br /><br /> To nie jest powiązany do lokalizacji pliku kształtu na diagramie.|  
|ElementPropertyChanged|Wartość właściwość domeny została zmieniona. Jest to wykonywane tylko wtedy, gdy starej i nowej wartości są nierówne.|  
|RolePlayerChanged|Jedną z dwóch ról relacji (kończy się) odwołuje się do nowego elementu.|  
|RolePlayerOrderChanged|W roli, których liczebność jest większa niż 1 sekwencja łącza został zmieniony.|  
|TransactionBeginning||  
|TransactionCommitted||  
|TransactionRolledBack||  
  
## <a name="see-also"></a>Zobacz też  
 [Odpowiadanie na zmiany i propagowanie zmian](../modeling/responding-to-and-propagating-changes.md)   
 [Przykładowy kod: Diagramy obwodu](http://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)
