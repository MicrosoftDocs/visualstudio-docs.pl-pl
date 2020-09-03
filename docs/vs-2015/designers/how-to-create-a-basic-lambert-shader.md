---
title: 'Instrukcje: Tworzenie podstawowego modułu cieniującego Lamberta | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: ec5c10fb-9600-4240-8280-d59451ea1d68
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 038b3e7db7f1e3b79ee3e41b6e256216a39b91bd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664556"
---
# <a name="how-to-create-a-basic-lambert-shader"></a>Porady: tworzenie podstawowego modułu cieniującego Lamberta
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym dokumencie przedstawiono sposób użycia projektanta programu do cieniowania i języka ukierunkowanego programu Graph (DGSL) w celu utworzenia cieniowania oświetlenia implementującego klasyczny model oświetlenia Lamberta.

 W tym dokumencie przedstawiono następujące działania:

- Dodawanie węzłów do wykresu cieniowania

- Odłączanie węzłów

- Łączenie węzłów

## <a name="the-lambert-lighting-model"></a>Model oświetlenia Lamberta
 Model oświetlenia Lamberta obejmuje oświetlenie otoczenia i kierunkowego w celu cieniowania obiektów w scenie 3-D. Składniki otoczenia zapewniają podstawowy poziom oświetlenia w scenie 3-D. Składniki kierunkowe zapewniają dodatkowe oświetlenie ze źródeł światła kierunkowego (daleko w dół). Oświetlenie otoczenia ma równo wpływ na wszystkie powierzchnie sceny, niezależnie od ich orientacji. Dla danej powierzchni jest to produkt otoczenia koloru powierzchni oraz kolor i intensywność oświetlenia otoczenia w scenie. Oświetlenie kierunkowe ma inne znaczenie w zależności od orientacji powierzchni względem kierunku źródła światła. Jest to iloczyn rozpraszanego koloru i orientacji powierzchni oraz kolor, intensywność i kierunek źródeł światła. Powierzchnie, które są bezpośrednio skierowane do źródła światła, otrzymują maksymalny udział i powierzchnie, które nie są bezpośrednio otrzymywane bez udziału. W modelu oświetlenia Lamberta, składnik otoczenia i jeden lub więcej elementów kierunkowych są połączone, aby określić całkowity udział kolorów rozpraszania dla każdego punktu w obiekcie.

 Przed rozpoczęciem upewnij się, że wyświetlane jest okno **Właściwości** i **Przybornik** .

#### <a name="to-create-a-lambert-shader"></a>Aby utworzyć cieniowanie Lamberta

1. Utwórz program do cieniowania DGSL. Aby dowiedzieć się, jak dodać cieniowanie DGSL do projektu, zobacz sekcję Wprowadzenie w [projektancie cieniowania](../designers/shader-designer.md).

2. Odłącz węzeł **koloru punktu** od końcowego węzła **koloru** . Wybierz Terminal **RGB** w węźle **Kolor punktu** , a następnie wybierz polecenie **Przerwij linki**. Pozostaw podłączony Terminal **Alpha** .

3. Dodaj węzeł **Lamberta** do grafu. W **przyborniku**, w obszarze **Narzędzia**, wybierz pozycję **Lamberta** i przenieś ją na powierzchnię projektu. Węzeł Lamberta oblicza całkowity udział kolorów w pikselach na podstawie parametrów oświetlenia otoczenia i rozpraszania.

4. Połącz węzeł **koloru punktu** z węzłem **Lamberta** . W trybie **wyboru** Przenieś Terminal **RGB** węzła **koloru punktu** do terminalu **koloru rozpraszania** węzła **Lamberta** . To połączenie udostępnia węzeł Lamberta z interpolowanym kolorem rozpraszania pikseli.

5. Połącz obliczoną wartość koloru z końcowym kolorem. Przenieś Terminal **wyjściowy** węzła **Lamberta** do terminalu **RGB** **końcowego węzła Color** .

   Na poniższej ilustracji przedstawiono ukończony wykres modułu cieniującego i Podgląd cieniowania zastosowany do modelu czajniczek.

> [!NOTE]
> Aby lepiej zademonstrować efekt cieniowania na tej ilustracji, kolor pomarańczowy został określony przy użyciu parametru **MaterialDiffuse** cieniowania. Gra lub aplikacja może użyć tego parametru, aby podać unikatową wartość koloru dla każdego obiektu. Aby uzyskać informacje o parametrach materiału, zobacz sekcję podglądy programów do cieniowania w [projektancie cieniowania](../designers/shader-designer.md).

 ![Wykres programu do cieniowania i podgląd jego efektu.](../designers/media/digit-lambert-effect-graph.png "Cyfra-Lamberta-Effect-Graph")

 Niektóre kształty mogą zapewniać lepszy Podgląd niektórych programów do cieniowania. Aby uzyskać więcej informacji na temat podglądu programów do cieniowania w projektancie cieniowania, zobacz sekcję podglądy programów do cieniowania w [projektancie cieniowania](../designers/shader-designer.md).

 Na poniższej ilustracji przedstawiono program do cieniowania opisany w tym dokumencie, stosowany do modelu 3-D.

 ![Oświetlenie Lamberta zastosowane do modelu.](../designers/media/digit-lambert-effect-result.png "Cyfra — wynik Lamberta")

 Aby uzyskać więcej informacji na temat sposobu stosowania cieniowania do modelu 3-D, zobacz [How to: Apply a Shader to a 3-d model](../designers/how-to-apply-a-shader-to-a-3-d-model.md).

## <a name="see-also"></a>Zobacz też
 [Instrukcje: Stosowanie cieniowania do modelu 3-D](../designers/how-to-apply-a-shader-to-a-3-d-model.md) [instrukcje: eksportowanie programu do cieniowania](../designers/how-to-export-a-shader.md) [instrukcje: Tworzenie podstawowego](../designers/how-to-create-a-basic-phong-shader.md) [Shader Designer](../designers/shader-designer.md) [węzła projektanta](../designers/shader-designer-nodes.md) cieniowania podstawowego phongego programu do cieniowania
