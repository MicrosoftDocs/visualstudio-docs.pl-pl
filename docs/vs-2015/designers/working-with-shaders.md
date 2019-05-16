---
title: Praca z cieniowaniem | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 6b2ea1ed-b995-4e75-af19-c68fd37a3bc5
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b912708e7cc2f811e9cd18a24096ef66e128c375
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65690074"
---
# <a name="working-with-shaders"></a>Praca z cieniowaniem
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można użyć projektanta modułu cieniującego opartej na wykresach w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] do efekty cieniowania niestandardowego projektu. Możesz użyć tych programów do cieniowania w sieci Web opartej na DirectX gry lub aplikacji.  
  
## <a name="shaders"></a>Programy do cieniowania  
 A *programu do cieniowania* to program komputera, który wykonuje obliczenia grafiki — na przykład przekształcenia wierzchołek lub piksel kolorowanie — zwykle działa ono na jednostka przetwarzania grafiki (GPU) zamiast procesora CPU. Ponieważ większość etapy potoku grafiki tradycyjnych, funkcja stałej są teraz wykonywane przez programy do cieniowania, można użyć ich do utworzenia potoku, które są specyficzne dla potrzeb swojej aplikacji.  
  
 Najbardziej typowe rodzaje programów do cieniowania są *programów do cieniowania wierzchołków*, który wykonywania wierzchołków obliczeń oraz Zastąp Przekształcanie stałej funkcji i obwody oświetlenia w sprzęt-programowanej grafiki i *pikseli programy do cieniowania*, które wykonują obliczenia każdego piksela, które określić kolor piksela i Zastąp obwody funkcja stała koloru łączenia sprzętu-programowanej grafiki. Sprzęt graficzny nowoczesnego podejścia biznesowego uczyniło jeszcze więcej rodzajów programów do cieniowania możliwe —*programów do cieniowania powłoki*, *programów do cieniowania domeny*, i *programów do cieniowania geometrii* obliczeń graficznych i *programów do cieniowania obliczenia* dla obliczeń i grafiki. Żadna z tych etapów dostępnych nawet w sprzęt-programowanej grafiki. Programy do cieniowania początkowo zostały utworzone przy użyciu języka podobnego do zestawu, podanym danych równoległych (SIMD) oraz instrukcje skoncentrowane na grafiki (skalarnego). Teraz programów do cieniowania są zwykle tworzone za pomocą języków wysokiego poziomu, jak C, takich jak HLSL (język programu do cieniowania poziom).  
  
 Program Shader Designer umożliwia tworzenie programów do cieniowania pikseli interaktywnie zamiast programu, wprowadzając i kompilowania kodu. W projektancie programu do cieniowania programu do cieniowania jest definiowany przez liczbę węzłów, które reprezentują dane, operacji i połączeń między węzły, które reprezentują przepływ wartości danych, a wyniki pośrednie, za pomocą programu do cieniowania. Za pomocą tego podejścia i Podgląd w czasie rzeczywistym w projektancie programu do cieniowania, aby łatwiej wizualizować wykonywanie programu do cieniowania i "wykryć" interesujące zmiany programu do cieniowania za pośrednictwem eksperymentów.  
  
## <a name="dgsl-documents"></a>Dokumenty DGSL  
 Projektant programu do cieniowania zapisuje programów do cieniowania w formacie kierowane wykres modułu cieniującego języka (DGSL), który jest w formacie XML, który jest oparty na przekierowanie Graph Markup Language (DGML). DGSL programów do cieniowania można zastosować bezpośrednio w modelach 3-D w edytorze modeli. Jednak zanim użyjesz modułu cieniującego DGSL w swojej aplikacji, należy go wyeksportować do formatu, który rozumie DirectX — na przykład HLSL.  
  
 Ponieważ DGSL jest zgodny z DGML, można użyć narzędzia, które są przeznaczone do analizowania dokumentów DGML analizować swoje programów do cieniowania z DGSL. Aby uzyskać informacje na temat DGML, zobacz [opis kierowane Graph Markup Language (DGML)](https://msdn.microsoft.com/library/ee842619.aspx).  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Projektant cieniowania](../designers/shader-designer.md)|Opisuje sposób używania [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projektanta modułu cieniującego do pracy z programów do cieniowania.|  
|[Węzły projektanta cieniowania](../designers/shader-designer-nodes.md)|W tym artykule omówiono rodzaje węzły Shader Designer, które można użyć w celu osiągnięcia efekty graficzne.|  
|[Przykłady projektanta cieniowania](../designers/shader-designer-examples.md)|Zawiera łącza do tematów, które pokazują, jak uzyskać typowe efekty graficzne za pomocą projektanta modułu cieniującego.|
