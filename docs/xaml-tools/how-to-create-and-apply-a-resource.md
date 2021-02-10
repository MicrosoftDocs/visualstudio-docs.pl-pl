---
title: Tworzenie i stosowanie zasobów
description: Dowiedz się, jak utworzyć i zastosować zasób w projektant XAML tak, aby można było przechowywać i ponownie używać stylów i szablonów dla elementów.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- VS.XamlDesigner.CreateResource
- VS.XamlDesigner.EditResource
ms.assetid: 3ff4006d-659d-4073-9a41-06ff85e6cfdf
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b6c6c243896370cc97b8a85d5de520c4c033d49b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99971612"
---
# <a name="how-to-create-and-apply-a-resource"></a>Tworzenie i stosowanie zasobów

Style i szablony dla elementów w projektant XAML są przechowywane w jednostkach wielokrotnego użytku o nazwie Resources. Style umożliwiają ustawianie właściwości elementów i ponowne używanie tych ustawień w celu zapewnienia spójnego wyglądu w wielu elementach. [ControlTemplate](xref:Windows.UI.Xaml.Controls.ControlTemplate) definiuje wygląd kontrolki i można go również zastosować jako zasób. Aby uzyskać więcej informacji, zobacz Style i [Szablony kontrolek](/windows/uwp/design/controls-and-patterns/control-templates) [XAML](/windows/uwp/design/controls-and-patterns/xaml-styles) .

Za każdym razem, gdy tworzysz nowy zasób z istniejącej właściwości, [stylu](xref:Windows.UI.Xaml.Style)lub [ControlTemplate](xref:Windows.UI.Xaml.Controls.ControlTemplate), okno dialogowe **Tworzenie zasobu** umożliwia definiowanie zasobów na poziomie aplikacji, na poziomie dokumentu lub na poziomie elementu. Te poziomy określają, gdzie można użyć zasobu. Na przykład, jeśli zdefiniujesz zasób na poziomie elementu, zasób może być stosowany tylko do elementu, w którym został utworzony. Możesz również zapisać zasób w [słowniku zasobów](/windows/uwp/design/controls-and-patterns/resourcedictionary-and-xaml-resource-references), czyli osobnym pliku, którego można użyć ponownie w innym projekcie.

## <a name="create-a-new-resource"></a>Tworzenie nowego zasobu

1. Gdy plik XAML jest otwarty w projektant XAML, Utwórz element lub wybierz element w oknie konspektu dokumentu.

2. W oknie **Właściwości** wybierz znacznik właściwości, który jest wyświetlany jako symbol pola po prawej stronie wartości właściwości, a następnie wybierz polecenie **Konwertuj na nowy zasób**. Biały znak Box wskazuje wartość domyślną, a symbol czarnego pudełka zazwyczaj wskazuje, że zastosowany został zasób lokalny.

     Pojawi się odpowiednie okno dialogowego dla tworzenia zasobu. To okno dialogowe pojawia się podczas tworzenia zasobu na podstawie pędzla:

     ![Okno dialogowe Tworzenie zasobu](../designers/media/xaml_create_resource.png)

3. W polu **Nazwa (klucz)** wprowadź nazwę klucza. Jest to nazwa, której można użyć, jeśli chcesz, aby inne elementy odwołują się do zasobu.

4. W obszarze **Definiuj w** wybierz opcję określającą, gdzie ma być zdefiniowany zasób:

    - Aby udostępnić zasób dla dowolnego dokumentu w aplikacji, wybierz **aplikację**.

    - Aby udostępnić zasób tylko do bieżącego dokumentu, wybierz **ten dokument**.

    - Aby udostępnić zasób tylko do elementu, z którego został utworzony zasób lub do jego elementów podrzędnych, wybierz **ten dokument**, a następnie z listy rozwijanej wybierz pozycję **element**: **Nazwa**.

    - Aby zdefiniować zasób w pliku [słownika zasobów](/windows/uwp/design/controls-and-patterns/resourcedictionary-and-xaml-resource-references) , który może być ponownie używany w innych projektach, kliknij pozycję **słownik zasobów**. Następnie wybierz istniejący plik słownika zasobów, na przykład **StandardStyles. XAML**, z listy rozwijanej.

5. Wybierz przycisk **OK** , aby utworzyć zasób i zastosować go do elementu, z którego został utworzony.

## <a name="apply-a-resource-to-an-element-or-property"></a>Zastosuj zasób do elementu lub właściwości

1. W oknie Konspekt dokumentu wybierz element, do którego chcesz zastosować zasób.

2. Wykonaj jedną z następujących czynności:

   - Zastosuj zasób do właściwości. W oknie **Właściwości** wybierz znacznik właściwości obok wartości właściwości, wybierz pozycję **zasób lokalny** lub **zasób systemowy**, a następnie wybierz dostępny zasób z wyświetlonej listy.

      Jeśli nie widzisz zasobu, który powinien być widoczny, może to być spowodowane faktem, że typ zasobu nie jest zgodny z typem właściwości.

   - Zastosuj styl lub szablon kontrolki do kontrolki. Otwórz menu dostępne po kliknięciu prawym przyciskiem myszy (menu kontekstowe) kontrolki w oknie Konspekt dokumentu, wybierz polecenie **Edytuj szablon** lub **Edytuj dodatkowe szablony**, wybierz pozycję **Zastosuj zasób**, a następnie wybierz nazwę szablonu formantu z wyświetlonej listy.

     > [!NOTE]
     > **Edytuj szablon** stosuje szablony kontrolek. **Edycja dodatkowych szablonów** dotyczy innych typów szablonów.

     Zasoby można stosować wszędzie tam, gdzie są one zgodne. Na przykład można zastosować zasób pędzla do właściwości **pierwszego planu** kontrolki [TextBox](xref:Windows.UI.Xaml.Controls.TextBox) .

## <a name="edit-a-resource"></a>Edytowanie zasobu

1. Wybierz element w obszarze kompozycji lub w oknie konspektu dokumentu.

2. Wybierz domyślny lub lokalny znacznik właściwości z prawej strony właściwości w oknie **Właściwości** , a następnie wybierz polecenie **Edytuj zasób** , aby otworzyć okno dialogowe **Edytowanie zasobu** .

3. Modyfikuj opcje dla zasobu.

## <a name="see-also"></a>Zobacz też

- [Tworzenie interfejsu użytkownika przy użyciu projektanta XAML](../xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)
