---
title: Praca z obrazami i teksturami
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: b9fbc8fa-66d1-4055-8460-24d8b8fbe43e
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 110cbbb01f5b86d462a9a5f196735fd4d477fb10
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589867"
---
# <a name="work-with-textures-and-images"></a>Praca z teksturami i obrazami

Edytor obrazów w programie Visual Studio służy do tworzenia i modyfikowania tekstur i obrazów. Edytor obrazów obsługuje bogate tekstury i formaty obrazów, takie jak te, które są używane w tworzeniu aplikacji DirectX.

> [!NOTE]
> Edytor obrazów nie obsługuje obrazów o niskich kolorach, takich jak ikony lub kursory. Aby utworzyć lub zmodyfikować te rodzaje obrazów, użyj [Edytora obrazów dla ikon (C++)](/cpp/windows/image-editor-for-icons).

## <a name="textures-and-images"></a>Tekstury i obrazy

Tekstury i obrazy to na poziomie podstawowym tylko tabele danych, które są używane do dostarczania szczegółów wizualnych w aplikacjach graficznych. Rodzaj szczegółów, który zapewnia teksturę lub obraz, zależy od sposobu jego użycia, ale typowe przykłady są próbkami kolorów, wartościami alfa (przezroczystości), wartościami normalnymi powierzchni i wartościami wysokości. Podstawową różnicą między teksturą a obrazem jest to, że tekstura ma być używana razem z reprezentacją kształtu — zazwyczaj modelu 3D — do wyrażania pełnego obiektu lub sceny, ale obraz jest zazwyczaj samodzielną reprezentacją obiektu lub sceny.

Każda tekstura może być zakodowana i skompresowana na wiele sposobów, które są ortogonalne do typu danych, które posiada tekstura, lub do wymiarowości lub "kształtu" tekstury. Jednak różne metody kodowania i kompresji dają lepsze wyniki dla różnych rodzajów danych.

Za pomocą Edytora obrazów można tworzyć i modyfikować tekstury i obrazy w sposób przypominający inne edytory obrazów. Edytor obrazów zapewnia również mipmapping i inne funkcje do użytku z grafiką 3D i obsługuje wiele wysoce skompresowanych, przyspieszonych sprzętowo formatów tekstur, które obsługuje DirectX.

Typowe rodzaje tekstur obejmują:

### <a name="texture-maps"></a>Mapy tekstur

Mapy tekstur zawierają wartości kolorów, które są zorganizowane jako macierz jedno-, dwu- lub trójwymiarowa. Są one używane do zapewnienia szczegółów koloru obiektu, którego dotyczy problem. Kolory są często kodowane przy użyciu kanałów kolorów RGB (czerwony, zielony, niebieski) i mogą zawierać czwarty kanał alfa, który reprezentuje przezroczystość. Rzadziej kolory mogą być kodowane w innym schemacie kolorów lub czwarty kanał może zawierać dane inne niż alfa — na przykład wysokość.

### <a name="normal-maps"></a>Normalne mapy

Normalne mapy zawierają normalsy powierzchni. Służą one do zapewnienia szczegółów oświetlenia na dotkniętym obiekcie. Normalsy są często kodowane przy użyciu składników koloru czerwonego, zielonego i niebieskiego do przechowywania wymiarów x, y i z wektora. Istnieją jednak inne kodowania — na przykład kodowanie oparte na współrzędnych biegunowych.

### <a name="height-maps"></a>Mapy wysokości

Mapy wysokości zawierają dane dotyczące pola wysokości. Są one używane do zapewnienia formy szczegółów geometrycznych obiektu, którego dotyczy luka — przy użyciu kodu modułu cieniującego do obliczenia pożądanego efektu — lub w celu zapewnienia punktów danych dla zastosowań takich jak generowanie terenu. Wartości wysokości są często kodowane przy użyciu jednego kanału w teksturze.

### <a name="cube-maps"></a>Mapy sześcianów

Mapy modułów mogą zawierać różne typy danych — na przykład kolory lub normalsy — ale są zorganizowane jako sześć tekstur na twarzach modułu. Z tego powodu mapy modułu nie są próbkowane przez dostarczanie współrzędnych tekstury, ale przez dostarczanie wektora, którego pochodzenie jest środkiem modułu; próbka jest pobierana w miejscu, w którym wektor przecina sześcian. Mapy modułów służą do przybliżenia środowiska, które może być używane do obliczania odbić — jest to nazywane *mapowaniem środowiska*— lub w celu zapewnienia tekstury obiektom sferycznym o mniejszym zniekształceniu niż podstawowe, dwuwymiarowe tekstury.

## <a name="related-topics"></a>Powiązane tematy

|Tytuł|Opis|
|-----------|-----------------|
|[Edytor obrazów](../designers/image-editor.md)|W tym artykule opisano sposób korzystania z Edytora obrazów do pracy z teksturami i obrazami.|
|[Przykłady edytora obrazów](../designers/how-to-create-a-basic-texture.md)|Zawiera łącza do tematów, które pokazują, jak używać Edytora obrazów do wykonywania typowych zadań przetwarzania obrazu.|
