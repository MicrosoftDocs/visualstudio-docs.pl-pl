---
title: Tworzenie i stosowanie zasobów
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VS.XamlDesigner.CreateResource
- VS.XamlDesigner.EditResource
ms.assetid: 3ff4006d-659d-4073-9a41-06ff85e6cfdf
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f9eee42d9e3a48f77153e5bd94f72a975ab27843
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/28/2019
ms.locfileid: "66263395"
---
# <a name="how-to-create-and-apply-a-resource"></a>Tworzenie i stosowanie zasobów

Style i szablony dla elementów w Projektancie XAML są przechowywane w jednostkach wielokrotnego użytku, o nazwie zasoby. Style umożliwiają ustawianie właściwości elementu i ponownie użyć tych ustawień, aby uzyskać spójny wygląd między wieloma elementami. A [ControlTemplate](/uwp/api/Windows.UI.Xaml.Controls.ControlTemplate) definiuje wygląd formantu i mogą być również stosowane jako zasób. Aby uzyskać więcej informacji, zobacz [Szybki Start: Style formantów](http://go.microsoft.com/fwlink/?LinkID=248239) i [Szybki Start: Kontrolowanie szablony](http://go.microsoft.com/fwlink/?LinkID=247982).

Zawsze, gdy tworzysz nowy zasób z istniejącej właściwości [styl](/uwp/api/Windows.UI.Xaml.Style), lub `ControlTemplate`, **Utwórz zasób** okno dialogowe pozwala na zdefiniowanie zasobu na poziomie aplikacji w poziomie dokumentu lub na poziomie elementu. Te poziomy określają, w którym może korzystać z zasobów. Na przykład jeśli zdefiniujesz zasób na poziomie elementu, zasób może być stosowane tylko do elementu, na którym został utworzony. Istnieje również możliwość przechowywania zasobu w [słownik zasobów](/windows/uwp/design/controls-and-patterns/resourcedictionary-and-xaml-resource-references), które jest oddzielnym pliku, który można użyć ponownie w innym projekcie.

## <a name="create-a-new-resource"></a>Utwórz nowy zasób

1. Plik XAML jest otwarty w Projektancie XAML Utwórz element lub wybierz element w okno konspektu dokumentu.

2. W **właściwości** oknie Wybierz znacznik właściwości, która pojawia się jako symbol pole po prawej stronie wartości właściwości, a następnie wybierz **Konwertuj na nowy zasób**. Symbol białe pola wskazuje wartość domyślną, a symbol czarne pole zazwyczaj wskazuje, że zastosowano zasobu lokalnego.

     Pojawi się odpowiednie okno dialogowego dla tworzenia zasobu. To okno dialogowe pojawia się podczas tworzenia zasobu z pędzla:

     ![Utwórz zasób — okno dialogowe](../designers/media/xaml_create_resource.png)

3. W **nazwa (klucz)** wprowadź nazwę klucza. Jest to nazwa, do którego można użyć, jeśli chcesz, aby inne elementy, aby odwoływać się do zasobu.

4. W obszarze **zdefiniować w**, wybierz opcję określającą, którym ma być zdefiniowany zasób:

    - Aby udostępnić zasób do każdego dokumentu w aplikacji, wybierz opcję **aplikacji**.

    - Aby udostępnić zasób do bieżącego dokumentu, wybierz opcję **w tym dokumencie**.

    - Aby udostępnić zasób tylko element z której utworzono zasób lub jego elementy podrzędne, wybierz **w tym dokumencie**, a na liście rozwijanej wybierz **elementu**: **nazwy** .

    - Aby zdefiniować zasób w [słownik zasobów](/windows/uwp/design/controls-and-patterns/resourcedictionary-and-xaml-resource-references) pliku, który może być ponownie używane w innych projektach, kliknij przycisk **słownik zasobów**. Wybierz istniejący plik słownika zasobów, takich jak **StandardStyles.xaml**, na liście rozwijanej.

5. Wybierz **OK** przycisk, aby utworzyć zasób i zastosować go do elementu, z którego została utworzona.

## <a name="apply-a-resource-to-an-element-or-property"></a>Stosowanie zasobu do elementu lub właściwości

1. Okno konspektu dokumentu wybierz element, do której chcesz zastosować do zasobu.

2. Wykonaj jedną z następujących czynności:

   - Stosowanie zasobów do właściwości. W **właściwości** oknie Wybierz znacznik właściwości obok wartości właściwości, wybierz pozycję **zasobu lokalnego** lub **zasób systemowy**, a następnie wybierz zasób dostępny z wyświetlonej listy.

      Jeśli nie widzisz zasobów, która powinna się pojawić, może to być, ponieważ typ zasobu nie jest zgodny z typem właściwości.

   - Stosowanie zasobu szablon stylu lub kontrolki do formantu. Otwórz menu kliknij prawym przyciskiem myszy (menu kontekstowe) dla formantu w oknie konspekt dokumentu, wybierz opcję **Edytuj szablon** lub **Edytuj dodatkowe szablony**, wybierz **Zastosuj zasób**, a następnie wybierz nazwę szablonu kontrolki z wyświetlonej listy.

     > [!NOTE]
     > **Edytuj szablon** stosuje szablon kontrolki. **Edytuj dodatkowe szablony** mają zastosowanie inne typy szablonów.

     Zasoby można zastosować, wszędzie tam, gdzie są one zgodne. Na przykład można zastosować zasób pędzla **pierwszego planu** właściwość <xref:Windows.UI.Xaml.Controls.TextBox> kontroli.

## <a name="edit-a-resource"></a>Edytuj zasób

1. Wybierz element, w obszarze kompozycji lub w oknie konspekt dokumentu.

2. Wybierz znacznik właściwości domyślne lub lokalnych z prawej strony właściwości w **właściwości** okna, a następnie wybierz **Edytuj zasób** otworzyć **Edytuj zasób** okno dialogowe.

3. Modyfikowanie opcji dla zasobu.

## <a name="see-also"></a>Zobacz także

- [Tworzenie interfejsu użytkownika przy użyciu projektanta XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)
