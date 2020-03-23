---
title: Praca z cieniowaniem
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 6b2ea1ed-b995-4e75-af19-c68fd37a3bc5
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b7ccb4f838c702cb1843d5c0f44dd7f54219f27a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589776"
---
# <a name="work-with-shaders"></a>Praca z cieniowaniem

Projektanta modułu cieniującego opartego na wykresie w programie Visual Studio służy do projektowania niestandardowych efektów modułu cieniującego. Za pomocą tych modułów cieniującego można używać w grze lub aplikacji opartej na technologii DirectX.

## <a name="shaders"></a>Programy do cieniowania

Moduł *cieniujący* to program komputerowy, który wykonuje obliczenia grafiki — na przykład przekształcenia wierzchołków lub kolorowanie pikseli — i zazwyczaj działa na procesorze graficznym (GPU) zamiast procesora CPU. Ponieważ większość etapów potoku grafiki tradycyjnej, stałej funkcji są teraz wykonywane przez programy cieniowania, można ich użyć do utworzenia potoku, który jest specyficzny dla potrzeb aplikacji.

Najczęstszymi rodzajami modułów cieniowania są *moduły cieniujące wierzchołków,* które wykonują obliczenia na wierzchołek i zastępują obwody transformacji i oświetlenia o stałej funkcji w nieprogramowalnym sprzęcie graficznym oraz *moduły cieniujące piksele,* które wykonują obliczenia na piksel, które określają kolor piksela i zastępują obwody kombajny kolorów o stałej funkcji w nieprogramowalnym sprzęcie graficznym. Nowoczesny sprzęt graficzny umożliwił jeszcze więcej rodzajów shaderów:*cieniowanie kadłubów,* *shadery domen*i *moduły cieniującego geometrii* do obliczeń graficznych oraz *moduły cieniowania obliczeniowe* do obliczeń innych niż graficzne. Żaden z tych etapów nie jest nawet dostępny w nieprogramowalnym sprzęcie graficznym. Moduły cieniowania zostały pierwotnie utworzone przy użyciu języka podobnego do zestawu, który dostarczył instrukcje dotyczące równoległego (SIMD) i grafiki (produkt kropkowy). Teraz moduły cieniowania są zazwyczaj tworzone przy użyciu języków wysokiego poziomu, takich jak język C, takich jak HLSL (Język cieniowania wysokiego poziomu).

Projektanta modułu cieniującego można użyć do interaktywnego tworzenia modułów cieniowania pikseli, a nie przez wprowadzanie i kompilowanie kodu. W Projektancie modułu cieniującego moduł cieniujący jest definiowany przez szereg węzłów, które reprezentują dane i operacje, oraz połączenia między węzłami reprezentującymi przepływ wartości danych i wyników pośrednich za pośrednictwem modułu cieniującego. Korzystając z tego podejścia i podglądu w czasie rzeczywistym w Projektancie modułu cieniującego, można łatwiej wizualizować wykonywanie modułu cieniującego i "odkrywać" ciekawe odmiany modułu cieniującego poprzez eksperymentowanie.

## <a name="dgsl-documents"></a>Dokumenty DGSL

Projektant modułu cieniującego zapisuje moduły cieniowania w formacie DGSL (Directed Graph Shader Language), który jest formatem XML opartym na reżyserii języka znaczników wykresu (DGML). Moduły cieniowania DGSL można zastosować bezpośrednio do modeli 3D w Edytorze modeli. Jednak zanim będzie można użyć modułu cieniującego DGSL w aplikacji, należy wyeksportować go do formatu, który directx rozumie — na przykład HLSL.

Ponieważ DGSL jest zgodny z DGML, można użyć narzędzi, które są przeznaczone do analizowania dokumentów DGML do analizowania modułów cieniujących DGSL. Aby uzyskać informacje na temat DGML, zobacz [Opis języka bezpośredniego znacznika wykresu (DGML)](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

## <a name="related-topics"></a>Powiązane tematy

|Tytuł|Opis|
|-----------|-----------------|
|[Projektant modułu cieniującego](../designers/shader-designer.md)|W tym artykule opisano, jak używać Projektanta modułu cieniującego programu Visual Studio do pracy z modułami cieniu.|
|[Węzły projektanta modułu cieniującego](../designers/shader-designer-nodes.md)|W tym artykule omówiono rodzaje węzłów projektanta modułów cieniowania, których można użyć do uzyskania efektów graficznych.|
|[Przykłady projektanta modułu cieniującego](../designers/how-to-create-a-basic-color-shader.md)|Zawiera łącza do tematów, które pokazują, jak używać Projektanta modułu cieniującego do osiągnięcia typowych efektów graficznych.|
