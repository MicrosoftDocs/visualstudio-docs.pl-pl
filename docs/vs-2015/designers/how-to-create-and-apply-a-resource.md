---
title: Jak utworzyć i zastosować zasób | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
f1_keywords:
- VS.XamlDesigner.CreateResource
- VS.XamlDesigner.EditResource
ms.assetid: 3ff4006d-659d-4073-9a41-06ff85e6cfdf
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7d1fba3b956a492740171bf2ad747e980b41df29
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2020
ms.locfileid: "75851978"
---
# <a name="how-to-create-and-apply-a-resource"></a>Tworzenie i stosowanie zasobów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Style i szablony dla elementów w projektant XAML są przechowywane w jednostkach wielokrotnego użytku o nazwie Resources. Style umożliwiają ustawianie właściwości elementów i ponowne używanie tych ustawień w celu zapewnienia spójnego wyglądu w wielu elementach. [ControlTemplate](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.controltemplate.aspx) definiuje wygląd kontrolki i można go również zastosować jako zasób. Aby uzyskać więcej informacji, zobacz [Szybki Start: kontrolki stylów](https://msdn.microsoft.com/library/windows/apps/xaml/hh465381.aspx) i [Szybki Start: sterowanie szablonami](https://msdn.microsoft.com/library/windows/apps/xaml/hh465374.aspx).

 Za każdym razem, gdy tworzysz nowy zasób z istniejącej właściwości, [stylu](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.style.aspx)lub `ControlTemplate`, okno dialogowe **Tworzenie zasobu** umożliwia definiowanie zasobów na poziomie aplikacji, na poziomie dokumentu lub na poziomie elementu. Te poziomy określają, gdzie można użyć zasobu. Na przykład, jeśli zdefiniujesz zasób na poziomie elementu, zasób może być stosowany tylko do elementu, w którym został utworzony. Istnieje również możliwość przechowywania zasobu w słowniku zasobów, oddzielnym pliku, który można użyć ponownie w innym projekcie.

### <a name="to-create-a-new-resource"></a>Aby utworzyć nowy zasób

1. Gdy plik XAML jest otwarty w projektant XAML, Utwórz element lub wybierz element w oknie konspektu dokumentu.

2. W okno Właściwości wybierz znacznik właściwości, który jest wyświetlany jako symbol pola po prawej stronie wartości właściwości, a następnie wybierz polecenie **Konwertuj na nowy zasób**. Biały znak jest wartością domyślną, a symbol czarnego pudełka zwykle wskazuje, że zastosowany został zasób lokalny.

     Pojawi się odpowiednie okno dialogowego dla tworzenia zasobu. To okno dialogowe pojawia się podczas tworzenia zasobu na podstawie pędzla:

     ![Okno dialogowe Tworzenie zasobu](../designers/media/xaml-create-resource.png "xaml_create_resource")

3. W polu **Nazwa (klucz)** wprowadź nazwę klucza. Jest to nazwa, której można użyć, jeśli chcesz, aby inne elementy odwołują się do zasobu.

4. W obszarze **Definiuj w**wybierz opcję określającą, gdzie ma być zdefiniowany zasób:

    - Aby udostępnić zasób dla dowolnego dokumentu w aplikacji, wybierz **aplikację**.

    - Aby udostępnić zasób tylko do bieżącego dokumentu, wybierz **ten dokument**.

    - Aby udostępnić zasób tylko do elementu, z którego został utworzony zasób lub do jego elementów podrzędnych, wybierz **ten dokument**, a następnie z listy rozwijanej wybierz pozycję *element*: *Nazwa*.

    - Aby zdefiniować zasób w pliku słownika zasobów, który może być ponownie używany w innych projektach, kliknij pozycję **słownik zasobów**, a następnie wybierz istniejący plik słownika zasobów, na przykład **StandardStyles. XAML**, z listy rozwijanej.

5. Wybierz przycisk **OK** , aby utworzyć zasób i zastosować go do elementu, z którego został utworzony.

### <a name="to-apply-a-resource-to-an-element-or-property"></a>Aby zastosować zasób do elementu lub właściwości

1. W oknie Konspekt dokumentu wybierz element, do którego chcesz zastosować zasób.

2. Wykonaj jedną z następujących czynności:

   - Zastosuj zasób do właściwości. W okno Właściwości wybierz znacznik właściwości obok wartości właściwości, wybierz pozycję **zasób lokalny** lub **zasób systemowy**, a następnie wybierz dostępny zasób z wyświetlonej listy.

      Jeśli nie widzisz zasobu, który powinien być widoczny, może to być spowodowane faktem, że typ zasobu nie jest zgodny z typem właściwości.

   - Zastosuj styl lub szablon kontrolki do kontrolki. Otwórz menu kontekstowe dla kontrolki w oknie Konspekt dokumentu, wybierz polecenie **Edytuj szablon** lub **Edytuj dodatkowe szablony**, wybierz pozycję **Zastosuj zasób**, a następnie wybierz nazwę szablonu formantu z wyświetlonej listy.

     > [!NOTE]
     > **Edytowanie szablonu** służy do stosowania szablonów kontrolek. **Edycja dodatkowych szablonów** służy do stosowania innych typów szablonów.

     Zasoby mogą być stosowane wszędzie tam, gdzie są zgodne. Na przykład można zastosować zasób pędzla do właściwości **pierwszego planu** kontrolki <xref:Windows.UI.Xaml.Controls.TextBox>.

### <a name="to-edit-a-resource"></a>Aby edytować zasób

1. Wybierz element w obszarze kompozycji lub w oknie konspektu dokumentu.

2. Wybierz domyślny lub lokalny znacznik właściwości z prawej strony właściwości w okno Właściwości, a następnie wybierz polecenie **Edytuj zasób** , aby otworzyć okno dialogowe **Edytowanie zasobu** .

3. Modyfikuj opcje dla zasobu.

## <a name="see-also"></a>Zobacz też
 [Tworzenie interfejsu użytkownika przy użyciu projektanta XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)
