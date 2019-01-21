---
title: Opcje, Edytor tekstu HTML (formularze sieci Web), formatowanie
ms.date: 1/15/2019
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.HTML.Format
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 109c40bc555985efe4a305a749890dac0e2f7f22
ms.sourcegitcommit: d0b02affd24e66efed924c197824f35f823e3240
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/21/2019
ms.locfileid: "54417788"
---
# <a name="options-text-editor-html-web-forms-formatting"></a>Opcje, Edytor tekstu HTML (formularze sieci Web), formatowanie

Użyj **formatowanie** Strona opcji, aby ustawić opcje projektu HTML formatowanie kodu w edytorze kodu. Dostępu do tej strony, na pasku menu wybierz **narzędzia** > **opcje**, a następnie rozwiń węzeł **edytora tekstów** > **HTML (formularze sieci Web)**   >  **Formatowanie**.

## <a name="capitalization"></a>wielkość liter

Jeśli te opcje są zaznaczone, widok źródła i edytory XML dotyczą domyślny format wielkości liter nazw elementów i atrybutów po uprzednim utworzeniu elementy i podczas automatycznego formatowania. **Zastosuj automatyczne formatowanie** ustawienia określają czas występuje, w których automatycznego ponownego formatowania.

> [!WARNING]
> Kod XML jest rozróżniana wielkość liter. Ustawienie przypadek domyślny może mieć wpływ na parsery XML.

### <a name="uielement-list"></a>Lista elementów interfejsu użytkownika

**Tag serwerowy, atrybuty Server**

Te opcje określają, jak jest pisany wielką literą znaczniki dla kontrolki serwera sieci Web.

|Opcja|Wynik|
|---------------------------------|------------------------------|
|**Jak wprowadzono**|Element jest dokładnie tak, jak możesz wprowadzić.|
|**wielkie litery**|Nazwy elementów są ponownie sformatowany na wielkie litery.|
|**Małe litery**|Nazwy elementów są ponownie sformatowany na małe litery.|
|**Definicja zestawu**|Element przypadek jest określany przez jak element jest zdefiniowany w klasie odpowiedniego typu.|


**Tag kliencki, atrybuty klienta**

Te opcje określają automatyczne formatowanie zmian nazw atrybutów HTML i właściwości na wielkie lub małe litery, czy pozostaną, tak jak zostały wprowadzone.

|Opcja|Wynik|
|---------------------------------|------------------------------|
|**Jak wprowadzono**|Atrybut jest dokładnie tak, jak możesz wprowadzić.|
|**wielkie litery**|Nazwy atrybutów są ponownie sformatowany na wielkie litery.|
|**Małe litery**|Nazwy atrybutów są ponownie sformatowany na małe litery.|


## <a name="automatic-formatting-options"></a>Opcje formatowania automatycznego

Te opcje spowodować, że edytor widok źródła dodać lub usunąć fizycznego podziały wierszy podczas automatycznego formatowania. Można również określić, czy edytor dodaje atrybutów w cudzysłowie.

> [!NOTE]
> Te ustawienia nie należy zmieniać biały znak w znaczników XML.

### <a name="uielement-list"></a>Lista elementów interfejsu użytkownika

- **Wstaw cudzysłowy wartości atrybutów podczas pisania**

   Gdy ta opcja jest zaznaczona, Edytor automatycznie umieszcza atrybutów w cudzysłowie, jak podczas pisania (na przykład: ID="Select1"). Usuń zaznaczenie tej opcji, jeśli wolisz ręcznie wstawiania znaków cudzysłowu do znaczników.


   > [!NOTE]
   > Czy ta opcja jest zaznaczona, zostaną zachowane wszystkie istniejące znaki cudzysłowu w znaczników; znaki cudzysłowu, nigdy nie są usuwane.

- **Wstaw cudzysłowy wartości atrybutów podczas formatowania**

   Gdy ta opcja jest zaznaczona, automatyczne formatowanie dodaje wartości atrybutów w cudzysłowie (na przykład: ID="Select1").

   > [!NOTE]
   > Czy ta opcja jest zaznaczona, wszystkie istniejące znaki cudzysłowu w znaczników są zachowywane.

- **Automatyczne wstawianie tagów**

   Gdy ta opcja jest zaznaczona, Edytor automatycznie tworzy tagu zamykającego (na przykład  **\</b >**) podczas zamykania otwierający tag.

## <a name="tag-wrapping"></a>Zawijanie tagów

Te opcje określają, czy edytor dzielony tagów na linie jeśli one wykracza poza o określonej długości.

### <a name="uielement-list"></a>Lista elementów interfejsu użytkownika

- **Zawijaj tagi, po przekroczeniu określonej długości**

   Po wybraniu edytora przerywa znaczniki w liniach, jeśli tag wykracza poza długość określoną w **długość** pola tekstowego. Ta akcja jest wykonywana tylko wtedy, gdy formatowanie tagów, nie w momencie pisania nowego tagu.

   > [!NOTE]
   > Podaną wartość jest używana jako wartość minimalną. Edytor nie rozdziel poszczególne atrybuty.

- **Długość**

   Określa liczbę znaków wyświetlanych w wierszu przed zawijania. To pole wejściowe jest wyłączone, chyba że **Zawijaj tagi, gdy zostanie przekroczona określona długość** pole wyboru zostało zaznaczone.

- **Opcje związane z tagami**

   Wyświetla **opcjami określonymi dla tagów** okno dialogowe, które pozwala ustawić opcje formatowania dla poszczególnych tagów lub grup tagów.

## <a name="see-also"></a>Zobacz także

- [Ogólne, Środowisko, Opcje — okno dialogowe](../../ide/reference/general-environment-options-dialog-box.md)