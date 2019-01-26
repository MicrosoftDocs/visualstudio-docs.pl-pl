---
title: Węzły filtrów
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
ms.assetid: f7cae2dc-e9a7-49d4-8be5-58b79868624e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b047bba87ef99916ba83d5cef07f26382755ce6c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54976540"
---
# <a name="filter-nodes"></a>Węzły filtrów

W projektancie programu do cieniowania węzły filtru przekształcania danych wejściowych — na przykład próbkę koloru lub tekstury — na wartość koloru symboli. Te wartości kolorów symboli są często używane w innych — gdy chodzi o fotorealistyczne renderowanie, lub jako składników w innych efektów wizualnych.

## <a name="filter-node-reference"></a>Odwołanie do węzła filtru

|Węzeł|Szczegóły|Właściwości|
|----------|-------------|----------------|
|**Blur**|Rozmywa pikseli tekstury za pomocą funkcji Gaussa.<br /><br /> Możesz użyć tego zmniejszenie szczegóły koloru lub szumu tekstury.<br /><br /> **Dane wejściowe:**<br /><br /> `UV`: `float2`<br /> Współrzędne texel do testowania.<br /><br /> **Dane wyjściowe:**<br /><br /> `Output`: `float4`<br /> Wartość koloru rozmyte.|**Tekstury**<br /> Rejestr tekstury skojarzony z próbnikiem używany podczas Rozmycie.|
|**Zmniejszanie nasycenia**|Zmniejsza ilość koloru w określony kolor.<br /><br /> Usunięcia koloru wartość koloru zbliża się odpowiadającą jej równoważnika na skali.<br /><br /> **Dane wejściowe:**<br /><br /> `RGB`: `float3`<br /> Zmniejsz nasycenie koloru.<br /><br /> `Percent`: `float`<br /> Procent kolor, aby usunąć, wyrażone jako znormalizowaną wartość z zakresu [0, 1].<br /><br /> **Dane wyjściowe:**<br /><br /> `Output`: `float3`<br /> Nasycony kolor.|**Jasności**<br /> Wagi, które są określone dla składników koloru czerwonego, zielonego i niebieskiego.|
|**Wykrywanie krawędzi**|Wykrywa krawędzie tekstury za pomocą wykrywanie krawędzi Canny'ego. Pikseli na krawędzi są wyświetlane jako biały; pikseli na krawędzi nie są wyświetlane jako czarny.<br /><br /> Służy to do określenia krawędzi tekstury, dzięki czemu można użyć dodatkowych efektów traktowanie pikseli na krawędzi.<br /><br /> **Dane wejściowe:**<br /><br /> `UV`: `float2`<br /> Współrzędne texel do testowania.<br /><br /> **Dane wyjściowe:**<br /><br /> `Output`: `float4`<br /> Białe, jeśli teksela znajduje się na krawędzi; w przeciwnym razie czarny.|**Tekstury**<br /> Rejestr tekstury skojarzony z próbnikiem używany podczas wykrywania krawędzi.|
|**Doskonalenie**|Wyostrza teksturę.<br /><br /> Możesz użyć tego, aby wyróżnić szczegółów tekstury.<br /><br /> **Dane wejściowe:**<br /><br /> `UV`: `float2`<br /> Współrzędne texel do testowania.<br /><br /> **Dane wyjściowe:**<br /><br /> `Output`: `float4`<br /> Wartość koloru rozmyte.|**Tekstury**<br /> Rejestr tekstury skojarzony z próbnikiem używany podczas wyostrzania.|