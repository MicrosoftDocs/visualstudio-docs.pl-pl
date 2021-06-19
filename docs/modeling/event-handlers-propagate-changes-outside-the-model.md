---
title: Programy obsługi zdarzeń propagujące zmiany poza modelem
description: Dowiedz się, że w zestawie SDK wizualizacji i modelowania możesz zdefiniować procedury obsługi zdarzeń magazynu w celu propagowania zmian do zasobów poza magazynem.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
- Domain-Specific Language, events
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 115d26840f321792712392367794e443e41543a2
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388948"
---
# <a name="event-handlers-propagate-changes-outside-the-model"></a>Programy obsługi zdarzeń propagujące zmiany poza modelem

W zestawie SDK wizualizacji i modelowania można zdefiniować procedury obsługi zdarzeń magazynu w celu propagowania zmian do zasobów poza magazynem, takich jak zmienne bez magazynu, pliki, modele w innych magazynach lub inne rozszerzenia Visual Studio magazynu. Procedury obsługi zdarzeń magazynu są wykonywane po zakończeniu transakcji, w której wystąpiło zdarzenie wyzwalające. Są one również wykonywane w operacji cofania lub ponownego wykonania. W związku z tym, w przeciwieństwie do reguł magazynu, zdarzenia magazynu są najbardziej przydatne do aktualizowania wartości, które znajdują się poza magazynem. W przeciwieństwie do zdarzeń .NET procedury obsługi zdarzeń magazynu są rejestrowane w celu nasłuchiwać klasy: nie trzeba rejestrować oddzielnej procedury obsługi dla każdego wystąpienia. Aby uzyskać więcej informacji na temat sposobu wyboru między różnymi sposobami obsługi zmian, zobacz Odpowiadanie na zmiany i [propagacja zmian.](../modeling/responding-to-and-propagating-changes.md)

Powierzchnia graficzna i inne kontrolki interfejsu użytkownika to przykłady zasobów zewnętrznych, które mogą być obsługiwane przez zdarzenia magazynu.

### <a name="to-define-a-store-event"></a>Aby zdefiniować zdarzenie sklepu

1. Wybierz typ zdarzenia, które chcesz monitorować. Aby uzyskać pełną listę, przyjrzyj się właściwościom obiektu <xref:Microsoft.VisualStudio.Modeling.EventManagerDirectory> . Każda właściwość odpowiada typowi zdarzenia. Najczęściej używane typy zdarzeń to:

    - `ElementAdded` — wyzwalane po utworzeniu elementu modelu, linku relacji, kształtu lub łącznika.

    - ElementPropertyChanged — wyzwalany po zmianie `Normal` wartości właściwości domeny. Zdarzenie jest wyzwalane tylko wtedy, gdy nowe i stare wartości nie są równe. Zdarzenia nie można zastosować do właściwości magazynu obliczanego i niestandardowego.

         Nie można go zastosować do właściwości roli, które odpowiadają linkom relacji. Zamiast tego należy `ElementAdded` użyć funkcji do monitorowania relacji domeny.

    - `ElementDeleted` — wyzwalane po usunięciu elementu modelu, relacji, kształtu lub łącznika. Nadal można uzyskać dostęp do wartości właściwości elementu, ale nie będzie on miał relacji z innymi elementami.

2. Dodaj definicję klasy częściowej _dla yourDsl_**DocData** w oddzielnym pliku kodu w **projekcie DslPackage.**

3. Napisz kod zdarzenia jako metodę, jak w poniższym przykładzie. Może to być `static` , chyba że chcesz uzyskać dostęp do `DocData` .

4. Zastąp `OnDocumentLoaded()` , aby zarejestrować program obsługi. Jeśli masz więcej niż jedną program obsługi, możesz zarejestrować je wszystkie w tym samym miejscu.

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

## <a name="use-events-to-make-undoable-adjustments-in-the-store"></a>Używanie zdarzeń do dostosowań z możliwością cofania w magazynie

Zdarzenia magazynu nie są zwykle używane do propagowania zmian wewnątrz magazynu, ponieważ procedura obsługi zdarzeń jest wykonywana po zatwierdzona transakcji. Zamiast tego należy użyć reguły magazynu. Aby uzyskać więcej informacji, zobacz [Reguły propagacji zmian w modelu](../modeling/rules-propagate-changes-within-the-model.md).

Można jednak użyć procedury obsługi zdarzeń, aby wprowadzić dodatkowe aktualizacje do magazynu, jeśli chcesz, aby użytkownik mógł cofnąć dodatkowe aktualizacje niezależnie od oryginalnego zdarzenia. Załóżmy na przykład, że małe litery są standardową konwencją tytułów szemów. Można napisać program obsługi zdarzeń sklepu, który poprawia tytuł do małe litery po wpisaniu go przez użytkownika w wielkich literach. Jednak użytkownik może użyć polecenia Cofnij, aby anulować korektę, przywracając wielkie litery. Drugie cofnięcie spowoduje usunięcie zmiany użytkownika.

Z kolei jeśli napisaliśmy regułę sklepu, aby wykonać tę samą czynność, zmiana użytkownika i korekta byłaby w tej samej transakcji, aby użytkownik nie mógł cofnąć korekty bez utraty oryginalnej zmiany.

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

W przypadku pisania zdarzenia, które aktualizuje magazyn:

- Użyj `store.InUndoRedoOrRollback` polecenia , aby uniknąć zmian w elementach modelu w funkcji Cofnij. Menedżer transakcji ustawi wszystko w magazynie z powrotem do pierwotnego stanu.

- Użyj `store.InSerializationTransaction` funkcji , aby uniknąć dokonywania zmian podczas ładowania modelu z pliku.

- Zmiany będą powodować wyzwolenie dalszych zdarzeń. Upewnij się, że unikasz nieskończonej pętli.

## <a name="store-event-types"></a>Store Event types (Przechowuj typy zdarzeń)

Każdy typ zdarzenia odpowiada kolekcji w Store.EventManagerDirectory. Procedury obsługi zdarzeń można dodawać lub usuwać w dowolnym momencie, ale zazwyczaj jest to dodawanie ich podczas ładowania dokumentu.

|`EventManagerDirectory` Nazwa właściwości|Wykonywane, gdy|
|-|-|
|ElementAdded|Tworzone jest wystąpienie klasy domeny, relacji domeny, kształtu, łącznika lub diagramu.|
|ElementDeleted|Element modelu został usunięty z katalogu elementów magazynu i nie jest już źródłem ani obiektem docelowym żadnej relacji. Element nie jest w rzeczywistości usuwany z pamięci, ale jest zachowywany w przypadku przyszłego cofnięcia.|
|ElementEventsBegun|Wywoływane na końcu transakcji zewnętrznej.|
|ElementEventsEnded|Wywoływane, gdy wszystkie inne zdarzenia zostały przetworzone.|
|ElementMoved|Element modelu został przeniesiony z jednej partycji magazynu do innej.<br /><br /> Nie jest to związane z lokalizacją kształtu na diagramie.|
|ElementPropertyChanged|Wartość właściwości domeny została zmieniona. Jest to wykonywane tylko wtedy, gdy stare i nowe wartości są nierówne.|
|RolePlayerChanged|Jedna z dwóch ról (koniec) relacji odwołuje się do nowego elementu.|
|RolePlayerOrderChanged|W roli z liczebnością większą niż 1 sekwencja linków uległa zmianie.|
|TransactionBeginning||
|TransactionCommitted||
|TransactionRolledBack||

## <a name="see-also"></a>Zobacz też

- [Odpowiadanie na zmiany i propagowanie zmian](../modeling/responding-to-and-propagating-changes.md)
- [Przykładowy kod: Diagramy obwodów](https://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
