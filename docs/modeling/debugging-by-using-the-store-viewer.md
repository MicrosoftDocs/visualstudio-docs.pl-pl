---
title: Debugowanie za pomocą przeglądarki sklepu
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, store viewer
- Domain-Specific Language, store
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7fb03dd67168867026c77a30bba412076c0b8408
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55945316"
---
# <a name="debugging-by-using-the-store-viewer"></a>Debugowanie za pomocą przeglądarki sklepu
Z podglądem Store można sprawdzić stan *przechowywania* posługują się [!INCLUDE[dsl](../modeling/includes/dsl_md.md)]. Podgląd Store Wyświetla listę wszystkich elementów modelu domeny, które znajdują się w określonym magazynie, wraz z właściwości elementu i łączy między elementami.

## <a name="opening-store-viewer"></a>Otwieranie Store podglądu
 Jeśli jesteś w kompilacji eksperymentalne programu Visual Studio, Zatrzymaj kodu w punkcie przerwania, w których wystąpienie magazynu zawiera informacje o modelu. Następnie otwórz Podgląd Store, wpisując następujące polecenie w **bezpośrednie** okna:

```csharp
Microsoft.VisualStudio.Modeling.Diagnostics.StoreViewer.Show(mystore);
```

> [!NOTE]
>  Należy zastąpić `mystore` nazwą wystąpienia usługi magazynu. Ponadto jeśli dodasz przestrzeni nazw w kodzie, należy wpisać polecenia do wyświetlania podglądu Store bez w pełni kwalifikowaną przestrzeń nazw:
>
>  `using Microsoft.VisualStudio.Modeling.Diagnostics;`
>
>  `...`
>
>  `StoreViewer.Show(mystore);`

 `Show` Metoda ma kilka przeciążeń. Wystąpienie magazynie lub partycji można określić jako parametr.

 Alternatywnie, można umieścić wiersza kodu, który wyświetla podgląd Store w dowolnym miejscu w kodzie gdzie parametr, który jest przekazywany do `Show` metoda znajduje się w zakresie. Ta akcja wyświetla podgląd Store podczas wykonywania wiersza kodu, jak o migawce zawartości magazynu.

### <a name="using-store-viewer"></a>Za pomocą przeglądarki Store
 Po otwarciu przeglądarki Store jest niemodalne okno dialogowe formularzy Windows pojawi się, jak pokazano na następującym rysunku.

 ![](../modeling/media/storeviewer2.png) Podgląd Store

 Podgląd Store ma trzy okienka: okienka po lewej stronie, prawym górnym rogu i prawym dolnym rogu. W okienku po lewej stronie jest typów w widoku drzewa `DomainDataDirectory` elementu członkowskiego magazynu. Rozwiń węzeł partycji, należy kliknąć pozycję elementu właściwości są wyświetlane w okienku w prawym górnym rogu. Jeśli element jest połączony z innymi elementami, dodatkowe elementy są wyświetlane w okienku prawego dolnego rogu. Dwukrotne kliknięcie elementu w okienku prawego dolnego rogu elementu jest wyróżniona w okienku po lewej stronie.

## <a name="see-also"></a>Zobacz też

- [Nawigowanie i aktualizowanie modelu w kodzie programu](../modeling/navigating-and-updating-a-model-in-program-code.md)