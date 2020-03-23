---
title: 'Porady: tworzenie i modyfikacja poziomów MIP'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f64d4369-2307-4175-a39a-2e45506f7fa1
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 793d730df3942608451e7dbc329819b98c451973
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "76113283"
---
# <a name="how-to-create-and-modify-mip-levels"></a>Jak: Tworzenie i modyfikowanie poziomów MIP
W tym dokumencie pokazano, jak używać **Edytora obrazów** do generowania i modyfikowania *poziomów MIP* dla poziomu szczegółowości (LoD).

## <a name="generating-mip-levels"></a>Generowanie poziomów MIP
*Mipmapping* to technika, która służy do zwiększania szybkości renderowania i zmniejszania artefaktów aliasowania na teksturowanych obiektach przez wstępne obliczanie i przechowywanie kilku kopii tekstury w różnych rozmiarach. Każda kopia, która jest nazywana poziomem MIP, jest o połowę szerokością i wysokością poprzedniej kopii. Gdy tekstura jest renderowana na powierzchni obiektu, automatycznie wybierany jest poziom MIP, który najbardziej odpowiada obszarowi przestrzeni ekranu powierzchni teksturowanej. Oznacza to, że sprzęt graficzny nie musi filtrować ponadgabarytowych tekstur, aby zachować stałą jakość obrazu. Chociaż koszt pamięci przechowywania poziomów MIP jest o 33 procent więcej niż w przypadku samej oryginalnej tekstury, wydajność i jakość obrazu uzasadniają to.

#### <a name="to-generate-mip-levels"></a>Aby wygenerować poziomy MIP

1. Zacznij od podstawowej tekstury, jak opisano w [jak: Tworzenie podstawowej tekstury](../designers/how-to-create-a-basic-texture.md). Aby uzyskać najlepsze wyniki, należy określić teksturę, która ma szerokość i wysokość, które mają moc dwóch rozmiarów, na przykład 256, 512, 1024 i tak dalej.

2. Generowanie poziomów MIP. Na pasku narzędzi **Tryb edytora obrazów** wybierz pozycję **Zaawansowane** > **narzędzia generują** > **mips**.

     Zwróć uwagę, że przyciski **Przejdź do następnego poziomu mip** i **Przejdź do poprzedniego poziomu Mip** są teraz wyświetlane na pasku narzędzi **Tryb edytora obrazów.** Jeśli zostanie wyświetlone okno **Właściwości,** należy również zauważyć, że właściwości tylko do odczytu **Mip Level** i **Liczba poziomów Mip** są teraz wyświetlane we właściwościach obrazu.

## <a name="modifying-mip-levels"></a>Modyfikowanie poziomów MIP
Aby uzyskać efekty specjalne lub zwiększyć jakość obrazu na określonych poziomach szczegółowości, można zmodyfikować każdy poziom MIP indywidualnie. Na przykład można nadać obiektowi teksturowanemu inny wygląd w dużej odległości (większa odległość odpowiada mniejszym poziomom MIP) lub można zapewnić, że tekstury zawierające tekst lub symbole pozostaną czytelne nawet przy mniejszych poziomach MIP.

#### <a name="to-modify-an-individual-mip-level"></a>Aby zmodyfikować indywidualny poziom mip

1. Wybierz poziom MIP, który chcesz zmodyfikować. Na **pasku** narzędzi Tryb edytora obrazów użyj przycisków **Przejdź do następnego poziomu MIP** i **Przejdź do poprzedniego poziomu MIP,** aby przejść między poziomami MIP.

2. Po wybraniu poziomu MIP, który chcesz zmodyfikować, można użyć narzędzi do rysowania, aby go zmodyfikować bez zmiany zawartości innych poziomów MIP. Narzędzia do rysowania są dostępne na pasku narzędzi **Edytor obrazów.** Po wybraniu narzędzia można zmienić jego właściwości w oknie **Właściwości.** Aby uzyskać informacje o narzędziach do rysowania i ich właściwościach, zobacz [Edytor obrazów](../designers/image-editor.md).

> [!NOTE]
> Jeśli nie trzeba modyfikować zawartości poszczególnych poziomów MIP — jak to zrobić, aby osiągnąć pewne efekty — zaleca się generowanie mipmaps z tekstury źródłowej w czasie kompilacji. Pomaga to zapewnić, że poziomy MIP pozostają zsynchronizowane z teksturą źródłową, ponieważ modyfikacje poziomu MIP nie są automatycznie propagowane na inne poziomy. Aby uzyskać więcej informacji na temat generowania mipmaps w czasie kompilacji, zobacz [Jak: Eksportowanie tekstury zawierającej mipmaps](../designers/how-to-export-a-texture-that-contains-mipmaps.md).

## <a name="see-also"></a>Zobacz też

- [Instrukcje: tworzenie tekstury podstawowej](../designers/how-to-create-a-basic-texture.md)
