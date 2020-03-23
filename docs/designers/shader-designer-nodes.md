---
title: Węzły Shader Designer
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f5192fbd-c78f-40a8-a4d4-443209610268
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 23877f9b94b498d87a89ae8e657aa2fe52984953
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "72634925"
---
# <a name="shader-designer-nodes"></a>Węzły projektanta modułu cieniującego
Artykuły w tej sekcji dokumentacji zawierają informacje o różnych węzłach Projektanta modułu cieniującego, których można użyć do tworzenia efektów graficznych.

## <a name="nodes-and-node-types"></a>Typy węzłów i węzłów
Projektant modułu cieniującego reprezentuje efekty wizualne jako wykres. Wykresy te są zbudowane z węzłów, które są specjalnie dobrane i połączone w precyzyjny sposób, aby osiągnąć zamierzony efekt. Każdy węzeł reprezentuje informacje lub funkcję matematyczną, a połączenia między nimi reprezentują sposób przepływu informacji przez wykres w celu uzyskania wyniku. Projektant modułu cieniującego udostępnia sześć różnych typów węzłów — filtry, węzły tekstur, parametry, stałe, węzły narzędzia i węzły matematyczne — a kilka pojedynczych węzłów należy do każdego typu. Te węzły i typy węzłów są opisane w innych artykułach w tej sekcji. Aby uzyskać więcej informacji, zobacz łącza na końcu tego dokumentu.

## <a name="node-structure"></a>Struktura węzła
Wszystkie węzły składa się z kombinacji wspólnych elementów. Każdy węzeł ma co najmniej jeden terminal wyjściowy po prawej stronie (z wyjątkiem węzła koloru końcowego, który reprezentuje dane wyjściowe modułu cieniującego). Węzły reprezentujące obliczenia lub samplery tekstur mają zaciski wejściowe po lewej stronie, ale węzły reprezentujące informacje nie mają terminali wejściowych. Zaciski wyjściowe są podłączone do terminali wejściowych w celu przenoszenia informacji z jednego węzła do drugiego.

### <a name="promotion-of-inputs"></a>Promowanie nakładów
Ponieważ Projektant modułu cieniującego musi ostatecznie wygenerować kod źródłowy HLSL, aby efekt mógł być używany w grze lub aplikacji, węzły projektanta modułu cieniującego podlegają regułom promocji typu używanym przez HLSL. Ponieważ sprzęt graficzny działa głównie na wartościach zmiennoprzecinkowych, `int` promowanie `float`typu `float` między `double`różnymi typami — na przykład od do , lub od do — jest rzadkością. Zamiast tego, ponieważ sprzęt graficzny używa tej samej operacji na wielu fragmentach informacji naraz, może wystąpić inny rodzaj promocji, w którym krótszy z wielu wejść jest wydłużony, aby dopasować rozmiar najdłuższego wejścia. Sposób wydłużenia zależy od typu wejścia, a także od samej operacji:

- **Jeśli mniejszy typ jest wartością skalarną, wówczas:**

     Wartość skalarna jest replikowana do wektora, który jest równy rozmiar większe dane wejściowe. Na przykład wejście skalarne 5.0 staje się wektorem (5.0, 5.0, 5.0), gdy największym wejściem operacji jest wektor trzyelementowy, niezależnie od tego, jaka jest operacja.

- **Jeśli mniejszy typ jest wektorem, a operacja jest\*mnożenia ( , /, %, i tak dalej), a następnie:**

     Wartość wektora jest kopiowana do wiodących elementów wektora, który jest równy rozmiar większe dane wejściowe, a końcowe elementy są ustawione na 1,0. Na przykład wejście wektorowe (5.0, 5.0) staje się wektorem (5.0, 5.0, 1.0, 1.0), gdy jest pomnożone przez wektor czteroelementowy. Pozwala to zachować trzeci i czwarty element danych wyjściowych przy użyciu tożsamości mnożenia, 1.0.

- **Jeśli mniejszy typ jest wektorem, a operacja jest addytywna (+, -, i tak dalej), a następnie:**

     Wartość wektora jest kopiowana do wiodących elementów wektora, który jest równy rozmiar większe dane wejściowe, a końcowe elementy są ustawione na 0,0. Na przykład wejście wektorowe (5.0, 5.0) staje się wektorem (5.0, 5.0, 0.0, 0.0) po dodaniu do wektora czteroelementowego. Pozwala to zachować trzeci i czwarty element danych wyjściowych przy użyciu tożsamości dodatku, 0.0.

## <a name="related-topics"></a>Powiązane tematy

|Tytuł|Opis|
|-----------|-----------------|
|[Stałe węzły](../designers/constant-nodes.md)|Opisuje węzły, których można używać do reprezentowania wartości literału i interpolowanych informacji o stanie wierzchołka w obliczeniach modułu cieniującego. Ponieważ stan wierzchołka jest interpolowany i dlatego jest inny dla każdego piksela — każde wystąpienie modułu cieniującego pikseli otrzymuje inną wersję stałej.|
|[Węzły parametrów](../designers/parameter-nodes.md)|Opisuje węzły, których można używać do reprezentowania położenia kamery, właściwości materiału, parametrów oświetlenia, czasu i innych informacji o stanie aplikacji w obliczeniach modułu cieniującego.|
|[Węzły tekstury](../designers/texture-nodes.md)|W tym artykule opisano węzły, za pomocą których można pobierać próbki różnych typów tekstur i geometrii oraz tworzyć lub przekształcać współrzędne tekstury w typowy sposób.|
|[Węzły matematyczne](../designers/math-nodes.md)|W tym artykule opisano węzły, których można używać do wykonywania operacji algebraicznych, logicznych, trygonometrycznych i innych operacji matematycznych, które są mapowane bezpośrednio do instrukcji HLSL.|
|[Węzły narzędzi](../designers/utility-nodes.md)|W tym artykule opisano węzły, których można użyć do wykonywania typowych obliczeń oświetlenia i innych typowych operacji, które nie są mapowane bezpośrednio do instrukcji HLSL.|
|[Węzły filtru](../designers/filter-nodes.md)|W tym artykule opisano węzły, za pomocą których można filtrować tekstury i filtrować kolory.|
