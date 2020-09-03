---
title: Debugowanie za pomocą przeglądarki sklepu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, store viewer
- Domain-Specific Language, store
ms.assetid: 0178db2e-ae99-4ed3-9b87-8620fa9fa8e4
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a870c66b1c14dc6ddf3e38fb6e5be8c116be3573
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72654893"
---
# <a name="debugging-by-using-the-store-viewer"></a>Debugowanie za pomocą przeglądarki sklepu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W podglądzie sklepu można przejrzeć stan *magazynu* używanego przez program [!INCLUDE[dsl](../includes/dsl-md.md)] . W podglądzie magazynu są wyświetlane wszystkie elementy modelu domeny, które znajdują się w określonym magazynie, wraz z właściwościami elementów i łączami między elementami.

## <a name="opening-store-viewer"></a>Otwieranie podglądu magazynu
 Gdy jesteś w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] kompilacji eksperymentalnej, Zatrzymaj kod w punkcie przerwania, w którym wystąpienie magazynu zawiera informacje o modelu. Następnie otwórz Podgląd sklepu, wpisując następujące polecenie w oknie **bezpośrednim** :

```
Microsoft.VisualStudio.Modeling.Diagnostics.StoreViewer.Show(mystore);
```

> [!NOTE]
> Należy zamienić na `mystore` nazwę swojego wystąpienia magazynu. Ponadto, jeśli dodasz przestrzeń nazw do kodu, możesz wpisać polecenie, aby wyświetlić podgląd magazynu bez w pełni kwalifikowanej przestrzeni nazw:
>
> `using Microsoft.VisualStudio.Modeling.Diagnostics;`
>
> `…`
>
> `StoreViewer.Show(mystore);`

 `Show`Metoda ma kilka przeciążeń. Możesz określić wystąpienie magazynu lub partycji jako parametr.

 Alternatywnie można umieścić wiersz kodu, który wyświetla podgląd sklepu w dowolnym miejscu w kodzie, gdzie parametr przekazywany do `Show` metody znajduje się w zakresie. Ta akcja wyświetla podgląd magazynu, gdy wiersz kodu jest wykonywany jako migawka zawartości sklepu.

### <a name="using-store-viewer"></a>Korzystanie z podglądu sklepu
 Po otwarciu podglądu sklepu zostanie wyświetlone okno niemodalne Windows Forms, jak pokazano na poniższej ilustracji.

 ![](../modeling/media/storeviewer2.png "storeviewer2") Podgląd magazynu

 Podgląd sklepu ma trzy okienka: lewe okienko, prawym Górne okienko i prawym dolnym rogu. Okienko po lewej stronie jest widokiem drzewa typów w `DomainDataDirectory` składowej magazynu. Po rozwinięciu węzła partycji i kliknięciu elementu właściwości elementu są wyświetlane w prawym górnym okienku. Jeśli element jest połączony z innymi elementami, dodatkowe elementy pojawiają się w prawym dolnym okienku. Po dwukrotnym kliknięciu elementu w prawym dolnym okienku element zostanie wyróżniony w lewym okienku.

## <a name="see-also"></a>Zobacz też
 [Nawigowanie i aktualizowanie modelu w kodzie programu](../modeling/navigating-and-updating-a-model-in-program-code.md)
