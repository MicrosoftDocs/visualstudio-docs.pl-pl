---
title: Węzły filtrów
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: f7cae2dc-e9a7-49d4-8be5-58b79868624e
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7627a5df1b3fcc5d26e33353e91f525b8083ccdf
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "72637307"
---
# <a name="filter-nodes"></a>Węzły filtrów

W Projektancie modułu cieniującego węzły filtrów przekształcają dane wejściowe — na przykład próbkę koloru lub tekstury — w wartość koloru w przenośni. Te graficzne wartości kolorów są powszechnie używane w renderowaniu nienamalnym lub jako składniki innych efektów wizualnych.

## <a name="filter-node-reference"></a>Odwołanie do węzła filtru

|Węzeł|Szczegóły|Właściwości|
|----------|-------------|----------------|
|**Rozmycie**|Rozmywa piksele w teksturze za pomocą funkcji Gaussa.<br /><br /> Można użyć tej funkcji, aby zmniejszyć szczegóły kolorów lub szum w teksturze.<br /><br /> **Dane wejściowe:**<br /><br /> `UV`: `float2`<br /> Współrzędne texel do testowania.<br /><br /> **Dane wyjściowe:**<br /><br /> `Output`: `float4`<br /> Niewyraźna wartość koloru.|**Tekstura**<br /> Rejestr tekstur skojarzony z próbnikem używanym podczas rozmycia.|
|**Desaturate**|Zmniejsza ilość koloru w określonym kolorze.<br /><br /> Po usunięciu koloru wartość koloru zbliża się do odpowiednika w skali szarości.<br /><br /> **Dane wejściowe:**<br /><br /> `RGB`: `float3`<br /> Kolor desaturate.<br /><br /> `Percent`: `float`<br /> Procent koloru do usunięcia, wyrażony jako wartość znormalizowana w zakresie [0, 1].<br /><br /> **Dane wyjściowe:**<br /><br /> `Output`: `float3`<br /> Nienasycony kolor.|**Luminancji**<br /> Wagi, które są podane do składników koloru czerwonego, zielonego i niebieskiego.|
|**Wykrywanie krawędzi**|Wykrywa krawędzie w teksturze za pomocą detektora krawędzi Canny. Piksele krawędzi są wyprowadzane jako białe; piksele bez krawędzi są wyprowadzane jako czarne.<br /><br /> Służy do identyfikowania krawędzi w teksturze, dzięki czemu można używać dodatkowych efektów do traktowania pikseli krawędzi.<br /><br /> **Dane wejściowe:**<br /><br /> `UV`: `float2`<br /> Współrzędne texel do testowania.<br /><br /> **Dane wyjściowe:**<br /><br /> `Output`: `float4`<br /> Biały, jeśli texel znajduje się na krawędzi; w przeciwnym razie, czarny.|**Tekstura**<br /> Rejestr tekstur skojarzony z próbnikem używanym podczas wykrywania krawędzi.|
|**Wyostrzanie**|Wyostrza teksturę.<br /><br /> Można użyć tego, aby wyróżnić drobne szczegóły w teksturze.<br /><br /> **Dane wejściowe:**<br /><br /> `UV`: `float2`<br /> Współrzędne texel do testowania.<br /><br /> **Dane wyjściowe:**<br /><br /> `Output`: `float4`<br /> Niewyraźna wartość koloru.|**Tekstura**<br /> Rejestr tekstur skojarzony z próbnikem używanym podczas wyostrzania.|