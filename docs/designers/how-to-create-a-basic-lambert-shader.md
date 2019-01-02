---
title: 'Instrukcje: Tworzenie podstawowego modułu cieniującego Lamberta'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: ec5c10fb-9600-4240-8280-d59451ea1d68
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 622209951ba3321a8278e0f65058459591af7d38
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53850358"
---
# <a name="how-to-create-a-basic-lambert-shader"></a>Instrukcje: Tworzenie podstawowego cieniowania Lamberta

W tym artykule pokazano, jak używać języka programu do cieniowania wykres kierowany (DGSL) i Projektant programu do cieniowania w celu utworzenia oświetlenia modułu cieniującego, który implementuje klasycznego modelu oświetlenia Lamberta.

## <a name="the-lambert-lighting-model"></a>Modelu oświetlenia Lamberta

Model oświetlenia Lambert dołącza oświetlenia otoczenia i kierunkowe odcień obiektów w scenie 3D. Otoczenia składniki zapewniają podstawowy poziom oświetlenia w scenie 3D. Kierunkowe składniki zapewniają dodatkowe oświetlenia ze źródeł (dalekie) światła kierunkowego. Oświetlenia otoczenia ma wpływ na wszystkie powierzchnie w scenie tak samo, niezależnie od ich orientacji. Dla danego powierzchni jest to produkt koloru otoczenia powierzchni i koloru i intensywności oświetlenia otoczenia na scenie. Światła kierunkowego ma wpływ na co narażonego na ataki w scenie inaczej, zgodnie z orientacją powierzchni względem kierunku po stronie źródła światła. Jest to produkt kolor rozpraszania i orientację powierzchni, a kolor, intensywność i kierunek źródła światła. Powierzchnie, które są spowodowane bezpośrednio do źródła światła otrzymują maksymalny udział i powierzchnie, które są spowodowane bezpośrednio natychmiast otrzymać nie wkład. W ramach modelu oświetlenia Lamberta składnik otoczenia i co najmniej jednego składnika kierunkowe są łączone w celu określenia udział łączny kolor rozpraszania dla każdego punktu w obiekcie.

Przed rozpoczęciem upewnij się, że **właściwości** okna i **przybornika** są wyświetlane.

1. Tworzenie modułu cieniującego DGSL za pomocą którego do pracy. Aby uzyskać informacje dotyczące sposobu dodawania modułu cieniującego DGSL do projektu, zobacz sekcję pierwsze kroki w [Shader Designer](../designers/shader-designer.md).

2. Odłącz **koloru punktu** węzła z **ostateczny kolor** węzła. Wybierz **RGB** terminali z **koloru punktu** węzła, a następnie wybierz **Przerwij linki**. Pozostaw **alfa** terminalu połączone.

3. Dodaj **Lamberta** węzła do wykresu. W **przybornika**w obszarze **narzędzie**, wybierz opcję **Lamberta** i przenieś go do powierzchni projektowej. Węzeł Lamberta oblicza udział łączny kolor rozpraszania piksela na podstawie parametrów otoczenia i rozpraszania oświetlenia.

4. Połącz **koloru punktu** węzeł **Lamberta** węzła. W **wybierz** tryb, Przenieś **RGB** terminali z **koloru punktu** węzeł, aby **kolor rozpraszania** terminali z **Lamberta**  węzła. To połączenie zawiera węzeł Lamberta kolorem rozpraszania interpolowane piksela.

5. Połącz się ostateczny kolor z wartości obliczanej koloru. Przenieś **dane wyjściowe** terminali z **Lamberta** węzeł **RGB** terminali z **ostateczny kolor** węzła.

   Poniższej ilustracji ukończone programu do cieniowania programu graph i wersję zapoznawczą programu do cieniowania, zastosowano do modelu czajniczek.

> [!NOTE]
> Aby lepiej zaprezentować efekt programu cieniującego na tej ilustracji, została określona za pomocą koloru pomarańczowego **MaterialDiffuse** parametr programu do cieniowania. Gry lub aplikacji można Użyj tego parametru, aby podać wartość koloru unikatowy dla każdego obiektu. Informacje o parametrach materiału sekcja Podgląd cieniowania w [Shader Designer](../designers/shader-designer.md).

 ![Wykres modułu cieniującego i wersją zapoznawczą jego wpływu.](../designers/media/digit-lambert-effect-graph.png)

 Niektórych kształtów udostępniać lepsze wersje zapoznawcze niektórych programów do cieniowania. Aby uzyskać więcej informacji na temat programów do cieniowania w projektancie programu do cieniowania w wersji zapoznawczej, zobacz sekcję Podgląd cieniowania w [Shader Designer](../designers/shader-designer.md).

 Poniższa ilustracja przedstawia programu do cieniowania, który jest opisany w tym dokumencie zastosowano do modelu 3D.

 ![Zastosowano do modelu oświetlenia Lamberta.](../designers/media/digit-lambert-effect-result.png)

 Aby uzyskać więcej informacji dotyczących sposobu stosowania programu do cieniowania do modelu 3D, zobacz [jak: Stosowanie cieniowania do modelu 3D](../designers/how-to-apply-a-shader-to-a-3-d-model.md).

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Stosowanie cieniowania do modelu 3D](../designers/how-to-apply-a-shader-to-a-3-d-model.md)
- [Instrukcje: Eksport cieniowania](../designers/how-to-export-a-shader.md)
- [Instrukcje: Tworzenie podstawowego modułu cieniowanie Phong](../designers/how-to-create-a-basic-phong-shader.md)
- [Projektant cieniowania](../designers/shader-designer.md)
- [Węzły projektanta cieniowania](../designers/shader-designer-nodes.md)