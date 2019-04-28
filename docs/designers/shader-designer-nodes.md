---
title: Węzły Shader Designer
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f5192fbd-c78f-40a8-a4d4-443209610268
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7bd7282a0826f10a0438f95164600419e0784a2a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62844232"
---
# <a name="shader-designer-nodes"></a>Węzły projektanta cieniowania
Artykuły w tej sekcji dokumentacji zawierają informacje dotyczące różnych węzłów programu Shader Designer używanych do tworzenia efektów grafiki.

## <a name="nodes-and-node-types"></a>Węzłów oraz typy węzłów
 Program Shader Designer przedstawia efektów wizualnych jako wykres. Te wykresy są kompilowane z węzłów, które są specjalnie wybranych i połączone w dokładne sposobów osiągnięcia zamierzony efekt. Każdy węzeł odpowiada fragment informacji lub funkcji matematycznych, a przepływ informacji za pośrednictwem programu graph w celu uzyskania wyniku połączenia między nimi. Projektant programu do cieniowania udostępnia sześć różnych typów węzłów — filtry, węzły tekstury, parametry, stałe, narzędzie węzłów i węzły matematyczne — i kilka poszczególne węzły należą do każdego typu. W innych artykułach w tej sekcji opisano tych węzłów oraz typy węzłów. Aby uzyskać więcej informacji zobacz linki na końcu tego dokumentu.

## <a name="node-structure"></a>Struktura węzła
 Wszystkie węzły składają się z kombinacji wspólne elementy. Każdy węzeł ma co najmniej jedno wyjście terminala na bok po prawej stronie (z wyjątkiem węzeł ostateczny kolor, który reprezentuje dane wyjściowe programu do cieniowania). Węzły, które reprezentują obliczeń lub próbki tekstury mają wejściowy terminale na swoich stronach po lewej stronie, ale węzły, które reprezentują informacje mają nie terminale danych wejściowych. Terminale dane wyjściowe są połączone z danych wejściowych terminale przenieść informacje z jednego węzła do drugiego.

### <a name="promotion-of-inputs"></a>Podwyższanie poziomu danych wejściowych
 Ponieważ program Shader Designer ostatecznie należy wygenerować kod źródłowy języka HLSL, tak, aby skutki mogą być używane w grach i aplikacjach, węzły Shader Designer podlegają reguły promocji typu, które używa HLSL. Ponieważ sprzęt graficzny działa przede wszystkim na wartości zmiennoprzecinkowe, wpisz podwyższania poziomu między różnymi typami — na przykład z `int` do `float`, lub z `float` do `double`— jest mało prawdopodobna. Zamiast tego ponieważ sprzęt graficzny korzysta z tej samej operacji na wiele rodzajów informacji naraz, inny rodzaj podwyższania poziomu mogą wystąpić, w którym krótszy liczby danych wejściowych jest zwiększany, aby był zgodny z rozmiarem najdłużej danych wejściowych. Jak jest zwiększany jest zależna od typu danych wejściowych, a także od samego operacji:

- **Jeśli mniejszych typów jest wartość skalarną, wtedy:**

     Wartości skalarnych są replikowane do wektora, który jest równy rozmiar większych dane wejściowe. Na przykład skalarnej wprowadzanie 5.0 staje się wektora (w wersji 5.0, 5.0, 5.0) podczas największych dane wejściowe operacji są Wektor trzech elementowej, niezależnie od tego, co to jest operacja.

- **Czy mniejszy typ wektora, a operacja jest mnożenia (\*, /, % i tak dalej), następnie:**

     Wartość wektora jest kopiowana do wiodących elementów wektora, który jest równy rozmiar większych dane wejściowe, a końcowe elementy są ustawione na 1.0. Na przykład wektor danych wejściowych (w wersji 5.0, 5.0) staje się wektora (w wersji 5.0, 5.0, 1.0, 1.0) po przemnożeniu wektor czterech elementu. Pozwala to zachować trzecia i czwarta elementy danych wyjściowych za pomocą tożsamości mnożenia, 1.0.

- **Czy mniejszy typ wektora, a operacja jest dodawania (+,-, i tak dalej), następnie:**

     Wartość wektora jest kopiowana do wiodących elementów wektora, który jest równy rozmiar większych dane wejściowe, a końcowe elementy są ustawione na 0,0. Na przykład wektor danych wejściowych (w wersji 5.0, 5.0) staje się wektora (w wersji 5.0, 5.0, 0.0, 0.0) po dodaniu do czterech elementów wektora. Pozwala to zachować trzecia i czwarta elementy danych wyjściowych za pomocą tożsamości dodatku, od 0,0.

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Stałe węzły](../designers/constant-nodes.md)|W tym artykule opisano węzły, które służą do reprezentowania wartości literałów i interpolowane informacji o stanie wierzchołków w obliczeniach cieniowania. Ponieważ wierzchołek stanu są interpolowane — i dlatego jest inny dla każdego piksela — każde wystąpienie programu do cieniowania pikseli odbiera nieco innej stałej.|
|[Węzły parametrów](../designers/parameter-nodes.md)|W tym artykule opisano węzły, które służą do reprezentowania położenie kamery, właściwości materiału, parametry oświetlenia, czas i inne informacje stan aplikacji w obliczeniach cieniowania.|
|[Węzły tekstury](../designers/texture-nodes.md)|W tym artykule opisano węzły, które można użyć przykładowy różne typy tekstury i geometrii i do utworzenia i przekształcenia współrzędnych tekstury w typowych sposobów.|
|[Węzły matematyczne](../designers/math-nodes.md)|W tym artykule opisano węzły, które można użyć do wykonania algebraicznych, logiki trygonometryczne i inne operacje matematyczne, mapowane bezpośrednio do instrukcji HLSL.|
|[Węzły narzędzi](../designers/utility-nodes.md)|W tym artykule opisano węzły, których można wykonywać typowe obliczenia udziału oświetlenia i innymi typowymi operacjami, które nie są mapowane bezpośrednio do instrukcji HLSL.|
|[Węzły filtrów](../designers/filter-nodes.md)|W tym artykule opisano węzły, które można użyć do wykonania filtrowania tekstur i filtrowanie kolor.|
