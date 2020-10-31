---
title: 'Porady: tworzenie podstawowego modułu cieniującego Lamberta'
description: Dowiedz się, jak używać projektanta programów do cieniowania i języka ukierunkowanego programu do cieniowania wykresów, aby utworzyć cieniowanie oświetlenia implementujące klasyczny model oświetlenia Lamberta.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: ec5c10fb-9600-4240-8280-d59451ea1d68
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f1677de15006dcf3bbe2f7a6b925be247518f752
ms.sourcegitcommit: a731a9454f1fa6bd9a18746d8d62fe2e85e5ddb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2020
ms.locfileid: "93134527"
---
# <a name="how-to-create-a-basic-lambert-shader"></a>Instrukcje: tworzenie podstawowego cieniowania Lamberta

W tym artykule pokazano, jak używać projektanta programu do cieniowania i języka ukierunkowanego programu Graph (DGSL) do tworzenia cieniowania oświetlenia implementującego klasyczny model oświetlenia Lamberta.

## <a name="the-lambert-lighting-model"></a>Model oświetlenia Lamberta

Model oświetlenia Lamberta obejmuje oświetlenie otoczenia i kierunkowego w celu cieniowania obiektów w scenie 3D. Składniki otoczenia zapewniają podstawowy poziom oświetlenia sceny 3W. Składniki kierunkowe zapewniają dodatkowe oświetlenie ze źródeł światła kierunkowego (daleko w dół). Oświetlenie otoczenia ma równo wpływ na wszystkie powierzchnie sceny, niezależnie od ich orientacji. Dla danej powierzchni jest to produkt otoczenia koloru powierzchni oraz kolor i intensywność oświetlenia otoczenia w scenie. Oświetlenie kierunkowe ma inne znaczenie w zależności od orientacji powierzchni względem kierunku źródła światła. Jest to iloczyn rozpraszanego koloru i orientacji powierzchni oraz kolor, intensywność i kierunek źródeł światła. Powierzchnie, które są bezpośrednio skierowane do źródła światła, otrzymują maksymalny udział i powierzchnie, które nie są bezpośrednio otrzymywane bez udziału. W modelu oświetlenia Lamberta, składnik otoczenia i jeden lub więcej elementów kierunkowych są połączone, aby określić całkowity udział kolorów rozpraszania dla każdego punktu w obiekcie.

Przed rozpoczęciem upewnij się, że wyświetlane jest okno **Właściwości** i **Przybornik** .

1. Utwórz program do cieniowania DGSL, który będzie działał. Aby dowiedzieć się, jak dodać cieniowanie DGSL do projektu, zobacz sekcję Wprowadzenie w [projektancie cieniowania](../designers/shader-designer.md).

2. Odłącz węzeł **koloru punktu** od końcowego węzła **koloru** . Wybierz Terminal **RGB** w węźle **Kolor punktu** , a następnie wybierz polecenie **Przerwij linki** . Pozostaw podłączony Terminal **Alpha** .

3. Dodaj węzeł **Lamberta** do grafu. W **przyborniku** , w obszarze **Narzędzia** , wybierz pozycję **Lamberta** i przenieś ją na powierzchnię projektu. Węzeł Lamberta oblicza całkowity udział kolorów w pikselach na podstawie parametrów oświetlenia otoczenia i rozpraszania.

4. Połącz węzeł **koloru punktu** z węzłem **Lamberta** . W trybie **wyboru** Przenieś Terminal **RGB** węzła **koloru punktu** do terminalu **koloru rozpraszania** węzła **Lamberta** . To połączenie udostępnia węzeł Lamberta z interpolowanym kolorem rozpraszania pikseli.

5. Połącz obliczoną wartość koloru z końcowym kolorem. Przenieś Terminal **wyjściowy** węzła **Lamberta** do terminalu **RGB** **końcowego węzła Color** .

   Na poniższej ilustracji przedstawiono ukończony wykres modułu cieniującego i Podgląd cieniowania zastosowany do modelu czajniczek.

> [!NOTE]
> Aby lepiej zademonstrować efekt cieniowania na tej ilustracji, kolor pomarańczowy został określony przy użyciu parametru **MaterialDiffuse** cieniowania. Gra lub aplikacja może użyć tego parametru, aby podać unikatową wartość koloru dla każdego obiektu. Aby uzyskać informacje o parametrach materiału, zobacz sekcję podglądy programów do cieniowania w [projektancie cieniowania](../designers/shader-designer.md).

![Wykres programu do cieniowania i podgląd jego efektu.](../designers/media/digit-lambert-effect-graph.png)

Niektóre kształty mogą zapewniać lepszy Podgląd niektórych programów do cieniowania. Aby uzyskać więcej informacji na temat podglądu programów do cieniowania w projektancie cieniowania, zobacz sekcję podglądy programów do cieniowania w [projektancie cieniowania](../designers/shader-designer.md).

Na poniższej ilustracji przedstawiono cieniowanie opisane w tym dokumencie, stosowane do modelu 3W.

![Oświetlenie Lamberta zastosowane do modelu.](../designers/media/digit-lambert-effect-result.png)

Aby uzyskać więcej informacji na temat sposobu stosowania cieniowania do modelu 3D, zobacz [How to: Apply a Shader to a model 3D](../designers/how-to-apply-a-shader-to-a-3-d-model.md).

## <a name="see-also"></a>Zobacz też

- [Instrukcje: Stosowanie cieniowania do modelu 3D](../designers/how-to-apply-a-shader-to-a-3-d-model.md)
- [Instrukcje: Eksportowanie cieniowania](../designers/how-to-export-a-shader.md)
- [Instrukcje: Tworzenie podstawowego cieniowania podstawowego Phong](../designers/how-to-create-a-basic-phong-shader.md)
- [Projektant programu do cieniowania](../designers/shader-designer.md)
- [Węzły projektanta cieniowania](../designers/shader-designer-nodes.md)
