---
title: 'Porady: tworzenie cieniowania tekstury podstawowej'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 5af113fb-6415-4be0-8b23-10fddb10e80a
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ac74155b8de4669d959d9b14e9be20ada2ec51d9
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75589477"
---
# <a name="how-to-create-a-basic-texture-shader"></a>Instrukcje: Tworzenie cieniowania tekstury podstawowej

W tym artykule pokazano, jak używać projektanta programu do cieniowania i języka ukierunkowanego programu Graph (DGSL) w celu utworzenia cieniowania z jedną teksturą. Ten program do cieniowania ustawia końcowy kolor bezpośrednio na wartości RGB i alfa, które są próbkowane ze tekstury.

## <a name="create-a-basic-texture-shader"></a>Tworzenie cieniowania tekstury podstawowej

Można zaimplementować podstawowe, jednoteksturowe cieniowanie, pisząc kolor i alfa próbki tekstury bezpośrednio do końcowego koloru wyjściowego.

Przed rozpoczęciem upewnij się, że wyświetlane jest okno **Właściwości** i **Przybornik** .

1. Utwórz program do cieniowania DGSL. Aby dowiedzieć się, jak dodać cieniowanie DGSL do projektu, zobacz sekcję Wprowadzenie w [projektancie cieniowania](../designers/shader-designer.md).

2. Usuń węzeł **koloru punktu** . W obszarze tryb **wyboru** wybierz węzeł **Kolor punktu** , a następnie na pasku menu wybierz polecenie **Edytuj** > **Usuń**. Powoduje to powolne miejsce dla węzła, który jest dodawany w następnym kroku.

3. Dodaj **przykładowy węzeł tekstury** do grafu. W **przyborniku**, w obszarze **tekstura**wybierz pozycję **tekstura próbki** i przenieś ją na powierzchnię projektu.

4. Dodaj węzeł **współrzędnej tekstury** do grafu. W **przyborniku**, w obszarze **tekstura**wybierz pozycję **koordynuj współrzędne** i przenieś ją na powierzchnię projektu.

5. Wybierz teksturę, która ma zostać zastosowana. W obszarze tryb **wyboru** wybierz węzeł **przykład tekstury** , a następnie w oknie **Właściwości** Określ teksturę, która ma być używana przy użyciu właściwości **filename** .

6. Udostępnienie tekstury publicznie. Wybierz węzeł **przykład tekstury** , a następnie w oknie **Właściwości** ustaw właściwość **dostęp** na **publiczną**. Teraz można ustawić teksturę z innego narzędzia, takiego jak **Edytor modelu**.

7. Połącz Współrzędne tekstury z przykładem tekstury. W trybie **wyboru** Przenieś Terminal **wyjściowy** węzła **współrzędnej tekstury** do terminalu **UV** węzła **przykładu tekstury** . To połączenie służy do próbkowania tekstury na określonych współrzędnych.

8. Połącz próbkę tekstury z kolorem końcowym. Przenieś Terminal **RGB** z węzła **przykład tekstury** do terminalu **RGB** **końcowego węzła Color** , a następnie przenieś Terminal **alfa** węzła **przykładowego tekstury** do terminalu **alfa** **końcowego węzła koloru** .

Na poniższej ilustracji przedstawiono ukończony wykres modułu cieniującego i Podgląd cieniowania zastosowany do modułu.

> [!NOTE]
> Na tej ilustracji, płaszczyzna jest używana jako kształt podglądu i określono teksturę, aby lepiej zademonstrować efekt cieniowania.

![Graf cieniowania i podgląd jego efektu](../designers/media/digit-texture-effect.png)

Niektóre kształty mogą zapewniać lepszy Podgląd niektórych programów do cieniowania. Aby uzyskać więcej informacji na temat podglądu programów do cieniowania w projektancie cieniowania, zobacz [Projektant cieniowania](../designers/shader-designer.md) .

## <a name="see-also"></a>Zobacz także

- [Instrukcje: stosowanie cieniowania do modelu 3D](../designers/how-to-apply-a-shader-to-a-3-d-model.md)
- [Edytor obrazów](../designers/image-editor.md)
- [Projektant cieniowania](../designers/shader-designer.md)
- [Węzły projektanta cieniowania](../designers/shader-designer-nodes.md)
