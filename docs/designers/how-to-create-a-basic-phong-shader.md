---
title: 'Instrukcje: Tworzenie podstawowego modułu cieniowanie Phong'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c7c69da8-142b-4d3b-9be9-4be0d5970b25
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 131afbaf4fcbdf5456a6276a36c551a47b663eec
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62897788"
---
# <a name="how-to-create-a-basic-phong-shader"></a>Instrukcje: Tworzenie podstawowego cieniowania Phonga

W tym artykule pokazano, jak używać języka programu do cieniowania wykres kierowany (DGSL) i Projektant programu do cieniowania w celu utworzenia oświetlenia modułu cieniującego, który implementuje Klasyczny model oświetlenie Phong.

## <a name="the-phong-lighting-model"></a>Model oświetlenie Phong

Model oświetlenie Phong rozszerza modelu oświetlenia Lamberta obejmujący odblasków wyróżnianie, która symuluje właściwości odbijające powierzchni. Odblasków składnik udostępnia dodatkowe oświetlenia z tego samego kierunkowe źródła światła, które są używane w modelu oświetlenia Lamberta, ale jej udziału ostateczny kolor jest przetwarzany inaczej. Wyróżnianie odblasków ma wpływ na co narażonego na ataki w scenie inaczej, na podstawie relacji między kierunku widoku, kierunek światła źródeł i orientację powierzchni. Jest to produkt koloru odblasków, moc odblasku i orientację powierzchni, a kolor, intensywność i kierunek źródła światła. Powierzchnie, które odzwierciedlają źródło światła bezpośrednio w przeglądarce otrzymują maksymalny udział odblasków i powierzchnie, które odzwierciedlają po stronie źródła światła od obserwatora otrzymywać nie materiałów przekazywanych. W obszarze model Phong oświetlenia co najmniej jednego składnika odblasków są łączone w celu określenia koloru i intensywność światła odblasków wyróżnianie dla każdego punktu w obiekcie i następnie są dodawane do wyniku modelu oświetlenia Lamberta, aby wygenerować ostateczny koloru piksela .

Aby uzyskać więcej informacji na temat modelu oświetlenia Lamberta zobacz [jak: Tworzenie podstawowego cieniowania Lamberta](../designers/how-to-create-a-basic-lambert-shader.md).

Przed rozpoczęciem upewnij się, że **właściwości** okna i **przybornika** są wyświetlane.

1. Tworzenie modułu cieniującego Lamberta zgodnie z opisem w [jak: Tworzenie podstawowego cieniowania Lamberta](../designers/how-to-create-a-basic-lambert-shader.md).

2. Odłącz **Lamberta** węzła z **ostateczny kolor** węzła. Wybierz **RGB** terminali z **Lamberta** węzła, a następnie wybierz **Przerwij linki**. To sprawia, że miejsce na węzeł, który zostanie dodany do następnego kroku.

3. Dodaj **Dodaj** węzła do wykresu. W **przybornika**w obszarze **matematyczne**, wybierz opcję **Dodaj** i przenieś go do powierzchni projektowej.

4. Dodaj **Specular** węzła do wykresu. W **przybornika**w obszarze **narzędzie**, wybierz opcję **Specular** i przenieś go do powierzchni projektowej.

5. Dodaj udział odblasków. Przenieś **dane wyjściowe** terminali z **Specular** węzeł, aby **X** terminali z **Dodaj** węzeł, a następnie przenieść **danych wyjściowych**  terminali z **Lamberta** węzeł **Y** terminali z **Dodaj** węzła. Te połączenia łączyć wkładów całkowita kolor rozpraszania i odblasków dla piksela.

6. Połącz się ostateczny kolor z wartości obliczanej koloru. Przenieś **dane wyjściowe** terminali z **Dodaj** węzeł **RGB** terminali z **ostateczny kolor** węzła.

   Poniższej ilustracji ukończone programu do cieniowania programu graph i wersję zapoznawczą programu do cieniowania, zastosowano do modelu czajniczek.

> [!NOTE]
> Aby lepiej zaprezentować efekt programu cieniującego na tej ilustracji, została określona za pomocą koloru pomarańczowego **MaterialDiffuse** parametr programu do cieniowania i wyszukiwanie metal zakończenia została określona za pomocą **MaterialSpecular** i **MaterialSpecularPower** parametrów. Informacje o parametrach materiału sekcja Podgląd cieniowania w [Shader Designer](../designers/shader-designer.md).

 ![Wykres modułu cieniującego i podgląd efektów jej](../designers/media/digit-lighting-graph.png)

 Niektórych kształtów udostępniać lepsze wersje zapoznawcze niektórych programów do cieniowania. Aby uzyskać więcej informacji na temat programów do cieniowania w projektancie programu do cieniowania w wersji zapoznawczej, zobacz sekcję Podgląd cieniowania w [Shader Designer](../designers/shader-designer.md)

 Poniższa ilustracja przedstawia programu do cieniowania, który jest opisany w tym dokumencie zastosowano do modelu 3D. **MaterialSpecular** właściwość jest ustawiona na (1,00 0,50, 0.20 lub nowszej, 0,00), a jego **MaterialSpecularPower** właściwość jest ustawiona na 16.

> [!NOTE]
> **MaterialSpecular** właściwość określa jawnego zakończenia materiału powierzchni. Powierzchni połysku wysokiej, takich jak szkło lub plastiku zwykle odblasków kolor, który jest jasny cień bieli. Powierzchnia metalowych zwykle mają kolor odblasku, który znajduje się w pobliżu jej kolor rozpraszania. Powierzchnia satynowa Zakończ zwykle mają kolor odblasku ciemny odcień szarości.
>
> **MaterialSpecularPower** właściwość określa, jak intensywne są światłem odbitym. Wysoka uprawnień odblasków symulować bardziej matowe, zlokalizowany więcej wyróżnia. Bardzo niskie uprawnień odblasków symulować intensywne, polegających na usuwaniu najważniejsze funkcje, które oversaturate i Ukryj kolor całej powierzchni.

 ![Oświetlenie Phong zastosowano do modelu](../designers/media/digit-lighting-model.png)

 Aby uzyskać więcej informacji dotyczących sposobu stosowania programu do cieniowania do modelu 3D, zobacz [jak: Stosowanie cieniowania do modelu 3D](../designers/how-to-apply-a-shader-to-a-3-d-model.md).

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Stosowanie cieniowania do modelu 3D](../designers/how-to-apply-a-shader-to-a-3-d-model.md)
- [Instrukcje: Eksport cieniowania](../designers/how-to-export-a-shader.md)
- [Instrukcje: Tworzenie podstawowego cieniowania Lamberta](../designers/how-to-create-a-basic-lambert-shader.md)
- [Projektant cieniowania](../designers/shader-designer.md)
- [Węzły projektanta cieniowania](../designers/shader-designer-nodes.md)