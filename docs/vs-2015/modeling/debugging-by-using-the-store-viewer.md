---
title: Debugowanie za pomocą przeglądarki Store | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, store viewer
- Domain-Specific Language, store
ms.assetid: 0178db2e-ae99-4ed3-9b87-8620fa9fa8e4
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1a76cd9b726e534271937cb67a8d3f946d4eb477
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63433197"
---
# <a name="debugging-by-using-the-store-viewer"></a>Debugowanie za pomocą przeglądarki sklepu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Z podglądem Store można sprawdzić stan *przechowywania* posługują się [!INCLUDE[dsl](../includes/dsl-md.md)]. Podgląd Store Wyświetla listę wszystkich elementów modelu domeny, które znajdują się w określonym magazynie, wraz z właściwości elementu i łączy między elementami.  
  
## <a name="opening-store-viewer"></a>Otwieranie Store podglądu  
 Podczas pracy w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] eksperymentalne kompilacji, Zatrzymaj kodu w punkcie przerwania, w których wystąpienie magazynu zawiera informacje o modelu. Następnie otwórz Podgląd Store, wpisując następujące polecenie w **bezpośrednie** okna:  
  
```  
Microsoft.VisualStudio.Modeling.Diagnostics.StoreViewer.Show(mystore);  
```  
  
> [!NOTE]
> Należy zastąpić `mystore` nazwą wystąpienia usługi magazynu. Ponadto jeśli dodasz przestrzeni nazw w kodzie, należy wpisać polecenia do wyświetlania podglądu Store bez w pełni kwalifikowaną przestrzeń nazw:  
>   
> `using Microsoft.VisualStudio.Modeling.Diagnostics;`  
>   
> `…`  
>   
> `StoreViewer.Show(mystore);`  
  
 `Show` Metoda ma kilka przeciążeń. Wystąpienie magazynie lub partycji można określić jako parametr.  
  
 Alternatywnie, można umieścić wiersza kodu, który wyświetla podgląd Store w dowolnym miejscu w kodzie gdzie parametr, który jest przekazywany do `Show` metoda znajduje się w zakresie. Ta akcja wyświetla podgląd Store podczas wykonywania wiersza kodu, jak o migawce zawartości magazynu.  
  
### <a name="using-store-viewer"></a>Za pomocą przeglądarki Store  
 Po otwarciu przeglądarki Store jest niemodalne okno dialogowe formularzy Windows pojawi się, jak pokazano na następującym rysunku.  
  
 ![](../modeling/media/storeviewer2.png "storeviewer2")  
Podgląd Store  
  
 Podgląd Store ma trzy okienka: okienka po lewej stronie, prawym górnym rogu i prawym dolnym rogu. W okienku po lewej stronie jest typów w widoku drzewa `DomainDataDirectory` elementu członkowskiego magazynu. Rozwiń węzeł partycji, należy kliknąć pozycję elementu właściwości są wyświetlane w okienku w prawym górnym rogu. Jeśli element jest połączony z innymi elementami, dodatkowe elementy są wyświetlane w okienku prawego dolnego rogu. Dwukrotne kliknięcie elementu w okienku prawego dolnego rogu elementu jest wyróżniona w okienku po lewej stronie.  
  
## <a name="see-also"></a>Zobacz też  
 [Nawigowanie i aktualizowanie modelu w kodzie programu](../modeling/navigating-and-updating-a-model-in-program-code.md)
