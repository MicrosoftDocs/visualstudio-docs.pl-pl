---
title: Programy obsługi zdarzeń propagujące zmiany poza modelem
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
- Domain-Specific Language, events
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fe60767fe61de5c49718f25281d9b547305bbe84
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653797"
---
# <a name="event-handlers-propagate-changes-outside-the-model"></a>Programy obsługi zdarzeń propagujące zmiany poza modelem

W programie Wizualizacja i modelowanie SDK można zdefiniować programy obsługi zdarzeń magazynu do propagowania zmian zasobów poza magazynem, takich jak zmienne spoza magazynu, pliki, modele w innych magazynach lub inne rozszerzenia programu Visual Studio. Procedury obsługi zdarzeń magazynu są wykonywane po zakończeniu transakcji, w której wystąpiło zdarzenie wyzwalające. Są one również wykonywane w operacji cofania lub ponawiania. W związku z tym, w przeciwieństwie do reguł magazynu, zdarzenia ze sklepu są najbardziej przydatne do aktualizowania wartości, które znajdują się poza magazynem. W przeciwieństwie do zdarzeń platformy .NET, programy obsługi zdarzeń magazynu są zarejestrowane w celu nasłuchiwania na klasie: nie ma potrzeby rejestrowania oddzielnej procedury obsługi dla każdego wystąpienia. Aby uzyskać więcej informacji na temat sposobu wybierania różnych sposobów obsługi zmian, zobacz [reagowanie na zmiany i propagowanie zmian](../modeling/responding-to-and-propagating-changes.md).

Graficzna powierzchnia i inne kontrolki interfejsu użytkownika to przykłady zasobów zewnętrznych, które mogą być obsługiwane przez zdarzenia ze sklepu.

### <a name="to-define-a-store-event"></a>Aby zdefiniować zdarzenie magazynu

1. Wybierz typ zdarzenia, które chcesz monitorować. Aby zapoznać się z pełną listą, zapoznaj się z właściwościami <xref:Microsoft.VisualStudio.Modeling.EventManagerDirectory>. Każda właściwość odpowiada typowi zdarzenia. Najczęściej używane typy zdarzeń to:

    - wyzwolone `ElementAdded` po utworzeniu elementu modelu, linku relacji, kształtu lub łącznika.

    - ElementPropertyChanged-wyzwalane, gdy zostanie zmieniona wartość właściwości domeny `Normal`. Zdarzenie jest wyzwalane tylko wtedy, gdy nowe i stare wartości nie są równe. Nie można zastosować zdarzenia do właściwości magazynu obliczeniowego i niestandardowego.

         Nie można jej zastosować do właściwości roli, które odpowiadają linkom relacji. Zamiast tego należy użyć `ElementAdded` do monitorowania relacji domeny.

    - `ElementDeleted`-wyzwolone po usunięciu elementu modelu, relacji, kształtu lub łącznika. Nadal można uzyskać dostęp do wartości właściwości elementu, ale nie będzie on miał żadnych relacji z innymi elementami.

2. Dodaj definicję klasy częściowej dla _YourDsl_**DocData** w osobnym pliku kodu w projekcie **DslPackage** .

3. Napisz kod zdarzenia jako metodę, jak w poniższym przykładzie. Może być `static`, chyba że chcesz uzyskać dostęp do `DocData`.

4. Zastąp `OnDocumentLoaded()`, aby zarejestrować procedurę obsługi. Jeśli masz więcej niż jedną procedurę obsługi, możesz zarejestrować je wszystkie w tym samym miejscu.

Lokalizacja kodu rejestracji nie jest krytyczna. `DocView.LoadView()` jest lokalizacją alternatywną.

```csharp
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
      base.OnDocumentLoaded(); // Don't forget this.

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

## <a name="use-events-to-make-undoable-adjustments-in-the-store"></a>Użyj zdarzeń, aby wprowadzać w sklepie wycofywane korekty

Zdarzenia ze sklepu nie są zwykle używane do propagowania zmian w magazynie, ponieważ program obsługi zdarzeń jest wykonywany po zatwierdzeniu transakcji. Zamiast tego należy użyć reguły sklepu. Aby uzyskać więcej informacji, zobacz [reguły propagowanie zmian w modelu](../modeling/rules-propagate-changes-within-the-model.md).

Można jednak użyć programu obsługi zdarzeń w celu wprowadzenia dodatkowych aktualizacji do magazynu, jeśli użytkownik ma mieć możliwość cofnięcia dodatkowych aktualizacji oddzielnie od oryginalnego zdarzenia. Załóżmy na przykład, że małe litery są zwyczajową Konwencją dla tytułów albumów. Można napisać procedurę obsługi zdarzeń magazynu, która koryguje tytuł małymi literami, gdy użytkownik wpisze ją w Wielkiej litery. Jednak użytkownik może użyć polecenia Cofnij, aby anulować korektę, przywracając wielkie litery. Druga operacja Cofnij spowoduje usunięcie zmiany użytkownika.

Z drugiej strony, jeśli zapisałem regułę sklepu, aby wykonać tę samą czynność, zmiana i korekta użytkownika będzie w tej samej transakcji, dzięki czemu użytkownik nie będzie mógł cofnąć korekty bez utraty pierwotnej zmiany.

```csharp
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

Jeśli piszesz zdarzenie, które aktualizuje Sklep:

- Użyj `store.InUndoRedoOrRollback`, aby uniknąć wprowadzania zmian do elementów modelu w Cofnij. Menedżer transakcji ustawi wszystkie elementy w sklepie z powrotem do stanu pierwotnego.

- Użyj `store.InSerializationTransaction`, aby uniknąć wprowadzania zmian podczas ładowania modelu z pliku.

- Zmiany spowodują wyzwolenie dalszych zdarzeń. Upewnij się, że unikasz pętli nieskończonej.

## <a name="store-event-types"></a>Przechowywanie typów zdarzeń

Każdy typ zdarzenia odpowiada kolekcji w sklepie. EventManagerDirectory. Obsługę zdarzeń można dodać lub usunąć w dowolnym momencie, ale zazwyczaj należy dodać je po załadowaniu dokumentu.

|Nazwa właściwości `EventManagerDirectory`|Wykonywane, gdy|
|-|-|
|ElementAdded|Tworzone jest wystąpienie klasy domeny, relacji domeny, kształtu, łącznika lub diagramu.|
|ElementDeleted|Element modelu został usunięty z katalogu elementów magazynu i nie jest już źródłem ani celem żadnej relacji. Element nie został faktycznie usunięty z pamięci, ale jest zachowywany w przypadku późniejszego cofnięcia.|
|ElementEventsBegun|Wywoływane na końcu zewnętrznej transakcji.|
|ElementEventsEnded|Wywoływane, gdy wszystkie inne zdarzenia zostały przetworzone.|
|ElementMoved|Element modelu został przeniesiony z jednej partycji magazynu do innej.<br /><br /> Nie dotyczy to lokalizacji kształtu na diagramie.|
|ElementPropertyChanged|Wartość właściwości domeny została zmieniona. Jest wykonywane tylko wtedy, gdy stare i nowe wartości są różne.|
|RolePlayerChanged|Jedna z dwóch ról (zakończonych) relacji odwołuje się do nowego elementu.|
|RolePlayerOrderChanged|W roli o liczebności większej niż 1 sekwencja linków została zmieniona.|
|TransactionBeginning||
|TransactionCommitted||
|TransactionRolledBack||

## <a name="see-also"></a>Zobacz też

- [Odpowiadanie na zmiany i propagowanie zmian](../modeling/responding-to-and-propagating-changes.md)
- [Przykładowy kod: diagramy obwodów](https://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]