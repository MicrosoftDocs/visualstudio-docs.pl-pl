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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589477"
---
# <a name="how-to-create-a-basic-texture-shader"></a>Instrukcje: tworzenie cieniowania tekstury podstawowej

W tym artykule pokazano, jak utworzyć moduł cieniujący z jedną teksturą za pomocą projektanta modułu cieniującego i języka cieniowania wykresu kierowanego (DGSL). Ten moduł cieniujący ustawia końcowy kolor bezpośrednio do RGB i wartości alfa, które są próbkowane z tekstury.

## <a name="create-a-basic-texture-shader"></a>Tworzenie cieniowania tekstury podstawowej

Można zaimplementować podstawowy moduł cieniujący o pojedynczej teksturze, zapisując wartości kolorów i alfa próbki tekstury bezpośrednio do końcowego koloru wyjściowego.

Przed rozpoczęciem upewnij się, że są wyświetlane okno **Właściwości** i **Przybornik.**

1. Utwórz moduł cieniujący DGSL do pracy. Aby uzyskać informacje dotyczące dodawania modułu cieniującego DGSL do projektu, zobacz sekcję Wprowadzenie w [Projektancie modułu cieniującego](../designers/shader-designer.md).

2. Usuń węzeł **Kolor punktu.** W trybie **wyboru** wybierz węzeł **Kolor punktu,** a następnie na pasku menu wybierz pozycję **Edytuj** > **usuń**. Dzięki temu miejsce na węzeł, który jest dodawany w następnym kroku.

3. Dodaj węzeł **próbki tekstury** do wykresu. W **przyborniku**w obszarze **Tekstura**wybierz pozycję **Próbka tekstury** i przenieś ją na powierzchnię projektową.

4. Dodaj węzeł **współrzędnych tekstury** do wykresu. W **przyborniku**w obszarze **Tekstura**wybierz pozycję **Współrzędna tekstury** i przenieś ją na powierzchnię projektową.

5. Wybierz teksturę do zastosowania. W trybie **wyboru** wybierz węzeł **Próbkowanie tekstury,** a następnie w oknie **Właściwości** określ teksturę, której chcesz użyć, używając właściwości **Nazwa pliku.**

6. Udostępnij teksturę publicznie. Wybierz węzeł **Przykład tekstury,** a następnie w oknie **Właściwości** ustaw właściwość **Dostęp** na **Publiczne**. Teraz można ustawić teksturę z innego narzędzia, takiego jak **Edytor modeli**.

7. Połącz współrzędne tekstury z próbką tekstury. W trybie **wyboru** przenieś terminal **wyjściowy** węzła **Współrzędności tekstury** do terminalu **UV** **węzła Próbka tekstury.** To połączenie próbki tekstury w określonych współrzędnych.

8. Połącz próbkę tekstury z końcowym kolorem. Przenieś terminal **RGB** **węzła Próbkowanie tekstury** do terminalu **RGB** **węzła Kolor końcowy,** a następnie przenieś terminal **Alfa** **węzła Próbkowanie tekstury** do terminalu **Alfa** **węzła Kolor końcowy.**

Na poniższej ilustracji przedstawiono ukończony wykres modułu cieniującego i podgląd modułu cieniującego zastosowanego do modułu.

> [!NOTE]
> Na tej ilustracji płaszczyzna jest używana jako kształt podglądu, a tekstura została określona, aby lepiej zademonstrować efekt modułu cieniującego.

![Wykres modułu cieniującego i podgląd jego efektu](../designers/media/digit-texture-effect.png)

Niektóre kształty mogą zapewniać lepsze podglądy niektórych modułów cieniowania. Aby uzyskać więcej informacji na temat wyświetlania podglądu modułów cieniucych w Projektancie modułów cieniucych, zobacz [Projektant modułów cieniucych](../designers/shader-designer.md)

## <a name="see-also"></a>Zobacz też

- [Instrukcje: stosowanie cieniowania do modelu 3D](../designers/how-to-apply-a-shader-to-a-3-d-model.md)
- [Edytor obrazów](../designers/image-editor.md)
- [Projektant modułu cieniującego](../designers/shader-designer.md)
- [Węzły projektanta modułu cieniującego](../designers/shader-designer-nodes.md)
