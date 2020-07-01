---
title: Węzły Shader Designer
ms.date: 11/04/2016
ms.topic: overview
ms.assetid: f5192fbd-c78f-40a8-a4d4-443209610268
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 75d13aaf5d5b4257ff6ec7c2efc52adbdca7df92
ms.sourcegitcommit: f27084e64c79e6428746a20dda92795df996fb31
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85768787"
---
# <a name="shader-designer-nodes"></a>Węzły projektanta cieniowania
Artykuły w tej sekcji dokumentacji zawierają informacje o różnych węzłach projektanta programu do cieniowania, których można użyć do tworzenia efektów graficznych.

## <a name="nodes-and-node-types"></a>Węzły i typy węzłów
Projektant cieniowania reprezentuje efekty wizualne jako Graf. Wykresy te są tworzone z węzłów, które zostały specjalnie wybrane i połączone z precyzyjnymi sposobami w celu osiągnięcia zamierzonego efektu. Każdy węzeł reprezentuje element informacji lub funkcję matematyczną, a połączenia między nimi przedstawiają sposób, w jaki informacje są przekazywane przez Graf w celu utworzenia wyniku. Projektant programu do cieniowania udostępnia sześć różnych typów węzłów — filtry, węzły tekstury, parametry, stałe, węzły narzędzi i węzły matematyczne — a kilka pojedynczych węzłów należy do każdego typu. Te węzły i typy węzłów zostały opisane w innych artykułach w tej sekcji. Aby uzyskać więcej informacji, zobacz linki na końcu tego dokumentu.

## <a name="node-structure"></a>Struktura węzłów
Wszystkie węzły składają się z kombinacji wspólnych elementów. Każdy węzeł ma co najmniej jeden terminal wyjściowy po prawej stronie (z wyjątkiem końcowego węzła koloru, który reprezentuje dane wyjściowe programu do cieniowania). Węzły reprezentujące obliczenia lub próbniki tekstury mają terminale wejściowe po lewej stronie, ale węzły reprezentujące informacje nie mają terminali wejściowych. Terminale wyjściowe są połączone z terminalami wejściowymi, aby przenieść informacje z jednego węzła do drugiego.

### <a name="promotion-of-inputs"></a>Promocja wejść
Ponieważ projektant programu do cieniowania musi ostatecznie wygenerować kod źródłowy HLSL, dzięki czemu efekt może być używany w grze lub aplikacji, węzły projektanta cieniowania podlegają regułom podwyższania poziomu, które są używane przez HLSL. Ponieważ sprzęt graficzny działa głównie na wartościach zmiennoprzecinkowych, należy wpisać promocję między różnymi typami — na przykład od `int` do `float` , lub z `float` do `double` — jest to nietypowe. Zamiast tego, ponieważ sprzęt graficzny używa tej samej operacji na wielu informacjach jednocześnie, może wystąpić różne rodzaje podwyższania poziomu, w których krótsza liczba danych wejściowych jest wydłuża w celu dopasowania do rozmiaru najdłuższych danych wejściowych. Sposób jego wydłużenia zależy od typu danych wejściowych, a także od samej operacji:

- **Jeśli mniejszy typ jest wartością skalarną, wówczas:**

     Wartość skalarna jest replikowana do wektora, który jest równy rozmiarowi większej ilości danych wejściowych. Na przykład dane wejściowe skalarne 5,0 są wektorem (5,0, 5,0, 5,0), gdy największe wejście operacji jest wektorem trzech elementów, niezależnie od tego, co to jest operacja.

- **Jeśli mniejszym typem jest wektor, a operacja jest mnożenia ( \* ,/,% i tak dalej), a następnie:**

     Wartość wektora jest kopiowana do wiodących elementów wektora, który jest równy rozmiarowi większych danych wejściowych, a końcowe elementy są ustawione na 1,0. Na przykład dane wejściowe wektora (5,0, 5,0) staną się wektorami (5,0, 5,0, 1,0, 1,0), gdy jest mnożona przez wektor czterech elementów. Pozwala to zachować trzeci i czwarty element danych wyjściowych przy użyciu tożsamości mnożenia, 1,0.

- **Jeśli mniejszym typem jest wektor, a operacja jest dodatkiem (+,-, itd.), wówczas:**

     Wartość wektora jest kopiowana do wiodących elementów wektora, który jest równy rozmiarowi większych danych wejściowych, a końcowe elementy są ustawione na 0,0. Na przykład dane wejściowe wektora (5,0, 5,0) staną się wektorami (5,0, 5,0, 0,0, 0,0), gdy zostanie dodana do wektora czterech elementów. Pozwala to zachować trzeci i czwarty element danych wyjściowych przy użyciu tożsamości dodatku 0,0.

## <a name="related-topics"></a>Powiązane tematy

|Tytuł|Opis|
|-----------|-----------------|
|[Stałe węzły](../designers/constant-nodes.md)|Opisuje węzły, których można użyć do reprezentowania wartości literału i interpolowane informacje o stanie wierzchołka w obliczeniach cieniowania. Ponieważ stan wierzchołka jest interpolowany, w związku z czym jest różny dla każdego piksela — każde wystąpienie programu do cieniowania pikseli otrzymuje inną wersję stałej.|
|[Węzły parametrów](../designers/parameter-nodes.md)|Opisuje węzły, których można użyć do reprezentowania położenia kamery, właściwości materiału, parametrów oświetlenia, godziny i innych informacji o stanie aplikacji w obliczeniach cieniowania.|
|[Węzły tekstury](../designers/texture-nodes.md)|Opisuje węzły, których można użyć do próbkowania różnych typów tekstury i geometrie, oraz do tworzenia lub przekształcania współrzędnych tekstury w typowy sposób.|
|[Węzły matematyczne](../designers/math-nodes.md)|Opisuje węzły, których można użyć do wykonywania algebraicznych, logiki, trygonometrycznych i innych operacji matematycznych, które są mapowane bezpośrednio do instrukcji HLSL.|
|[Węzły narzędzi](../designers/utility-nodes.md)|Opisuje węzły, których można użyć do wykonywania typowych obliczeń oświetlenia i innych typowych operacji, które nie są mapowane bezpośrednio na instrukcje HLSL.|
|[Węzły filtrów](../designers/filter-nodes.md)|Opisuje węzły, których można użyć do wykonywania filtrowania tekstury i filtrowania kolorów.|
