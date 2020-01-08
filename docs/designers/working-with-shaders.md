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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75589776"
---
# <a name="work-with-shaders"></a>Praca z cieniowaniem

Możesz użyć projektanta cieniowania opartego na grafie w programie Visual Studio, aby zaprojektować niestandardowe efekty cieniowania. Można używać tych programów do cieniowania w grach lub aplikacji opartych na programie DirectX.

## <a name="shaders"></a>Programy do cieniowania

Program do *cieniowania* jest programem komputerowym, który wykonuje obliczenia grafiki — na przykład przekształceń wierzchołków lub kolorowania pikseli — jest zazwyczaj uruchamiany na procesorze graficznym (GPU), a nie w procesorach. Ze względu na to, że większość etapów tradycyjnego potoku grafiki o stałej funkcji jest teraz wykonywana przez programy do cieniowania, można użyć ich do utworzenia potoku, który jest specyficzny dla potrzeb aplikacji.

Najbardziej typowymi rodzajami programów do cieniowania są programy do *cieniowania wierzchołków*, które wykonują obliczenia na wierzchołku i zastępują stałe funkcje transformacji i oświetlenia w nieprogramowalnym sprzęcie graficznym, i *cieniowania pikseli*, które wykonują obliczenia w pikselach, które określają kolor piksela i zastępują stałe-funkcyjne obwody łączenia z nieprogramowalnym sprzętem graficznym. Nowoczesny sprzęt graficzny oferuje jeszcze więcej rodzajów programów do cieniowania, programów do cieniowania*kadłuba*, programów do cieniowania *domen*i *cieniowania geometrycznego* na potrzeby obliczeń graficznych i *cieniowania* obliczeń dla niegraficznych obliczeń. Żaden z tych etapów nie jest jeszcze dostępny w nieprogramowalnym sprzęcie graficznym. Programy do cieniowania zostały pierwotnie utworzone przy użyciu języka podobnego do zestawu, który udostępnia instrukcje SIMD (Data-Parallel) i zorientowane na grafiki (iloczyn kropki). Teraz programy do cieniowania są zwykle tworzone przy użyciu wysokiej klasy języków, takich jak HLSL (język cieniowania wysokiego poziomu).

Projektanta programu do cieniowania można użyć do interaktywnego tworzenia programów do cieniowania pikseli zamiast wprowadzania i kompilowania kodu. W projektancie cieniowania, cieniowanie jest definiowane przez wiele węzłów, które reprezentują dane i operacje, oraz połączenia między węzłami, które reprezentują przepływ wartości danych i wyniki pośrednie za pośrednictwem programu do cieniowania. Korzystając z tej metody i podglądu w czasie rzeczywistym w projektancie cieniowania, można łatwiej wizualizować wykonywanie modułu cieniującego i "odkrywać" interesujące wahania programu do cieniowania za pośrednictwem eksperymentów.

## <a name="dgsl-documents"></a>DGSL dokumenty

Projektant programu do cieniowania zapisuje programy do cieniowania w formacie DGSL (Direct Graph Markup Language), który jest formatem XML opartym na module DGML Można zastosować cieniowanie DGSL bezpośrednio do modeli 3D w edytorze modeli. Jednak zanim będzie można użyć modułu cieniującego DGSL w aplikacji, należy wyeksportować go do formatu, który obsługuje program DirectX — na przykład HLSL.

Ponieważ DGSL jest zgodny z DGML, można użyć narzędzi przeznaczonych do analizowania dokumentów DGML do analizowania programów do cieniowania DGSLów. Aby uzyskać informacje na temat DGML, zobacz [Opis języka Directed Graph Markup Language (dgml)](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Projektant cieniowania](../designers/shader-designer.md)|Opisuje, jak używać projektanta cieniowania programu Visual Studio do pracy z narzędziami do cieniowania.|
|[Węzły projektanta cieniowania](../designers/shader-designer-nodes.md)|W tym artykule omówiono rodzaje węzłów projektanta modułu cieniującego, których można użyć do osiągnięcia efektów graficznych.|
|[Przykłady projektanta cieniowania](../designers/how-to-create-a-basic-color-shader.md)|Zawiera łącza do tematów, które pokazują, jak używać projektanta cieniowania do osiągnięcia typowych efektów graficznych.|
