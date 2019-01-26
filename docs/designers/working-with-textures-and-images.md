---
title: Praca z obrazami i teksturami
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: b9fbc8fa-66d1-4055-8460-24d8b8fbe43e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fd520d6a07722063ce1cc5f3c08e4592dbe08351
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55011003"
---
# <a name="work-with-textures-and-images"></a>Praca z teksturami i obrazami

Edytor obrazów w programie Visual Studio do tworzenia i modyfikowania teksturami i obrazami. Edytor obrazów obsługuje zaawansowane formatów tekstur i obrazów, takich jak te, które są używane w rozwoju aplikacji DirectX.

> [!NOTE]
> Edytor obrazów nie obsługuje obrazy niska color, takich jak ikony i kursory. Aby utworzyć lub zmodyfikować te rodzaje obrazów, użyj [edytor obrazów dla ikon (C++)](/cpp/windows/image-editor-for-icons).

## <a name="textures-and-images"></a>Obrazami i teksturami

Tekstury i obrazy są na poziomie podstawowym, po prostu tabele danych, które są używane do visual szczegółowych informacji w aplikacjach grafiki. Rodzaj szczegółów, który zapewnia obrazu lub tekstury zależy od tego, jak są używane, ale koloru próbek, wartości alfa (przezroczystości), normalne powierzchni i wysokość wartości są typowe przykłady. Główną różnicą między Tekstura i obraz jest, że tekstury jest przeznaczone do użycia wraz z reprezentacją kształtu — zwykle modelu 3D — express kompletnym obiektem lub sceny, ale obraz jest zazwyczaj reprezentację autonomicznej obiekt lub scenę.

Wszelkich tekstur można zakodowane i skompresowane na wiele sposobów, będące prostopadły do typu danych, który przechowuje tekstury lub wymiary lub "kształt" tekstury. Jednak inne kodowanie i metody kompresji przynieść lepsze wyniki dla różnych rodzajów elementów danych.

Tworzenie i modyfikowanie obrazami i teksturami metodami, które przypominają inne edytory obrazów, można użyć edytora obrazów. Edytor obrazów również udostępnia mipmapping i inne funkcje do użycia z grafiką 3D i obsługuje wiele formatów tekstury wysoce skompresowany, przyspieszanych sprzętowo, które obsługuje program DirectX.

Typowe rodzaje tekstury obejmują:

### <a name="texture-maps"></a>Map tekstur

Mapy tekstury zawierają wartości kolorów, które są zorganizowane w postaci jedno-, dwu- lub trójwymiarowe macierzy. Służą one, aby udostępnić szczegóły koloru na zainfekowanym obiektu. Kolory często są kodowane za pomocą kanałów koloru RGB (czerwony, zielony, niebieski) i może zawierać czwarty kanał alfa, reprezentujący przezroczystości. Rzadziej, kolory, może być zakodowany za pomocą inny schemat kolorów lub czwarty kanału może zawierać danych innych niż alfa — na przykład, wysokość.

### <a name="normal-maps"></a>Map normalnych

Mapy normalne zawierają normalne powierzchni. Służą one do szczegółowych oświetlenia, których to dotyczy obiektu. Normalne często są kodowane za pomocą składników koloru czerwonego, zielonego i niebieskiego do przechowywania x, y i z wymiarów wektora. Jednak istnieją inne kodowanie — na przykład w przypadku kodowania, które są oparte na Współrzędne biegunowe.

### <a name="height-maps"></a>Wysokość mapy

Wysokość mapy zawiera wysokość pola danych. Służą one do dodania formy szczegółów geometrycznych dotyczy obiektu — przy użyciu kodu programu do cieniowania do obliczenia pożądanego efektu — lub w celu zapewnienia punkty danych do celów takich jak Generowanie terenu. Wysokość wartości najczęściej są zakodowane przy użyciu kanału jednego tekstury.

### <a name="cube-maps"></a>Mapy modułu

Cubemaps mogą zawierać różne typy danych — na przykład kolorów lub normalne —, ale są zorganizowane w postaci sześciu tekstury na powierzchni modułu. W związku z tym mapy modułu nie są próbkowane przez podanie współrzędnych tekstury, ale poprzez dostarczenie wektor której źródłem jest środek modułu; próbki w punkcie, w którym wektora przecina modułu. Cubemaps służą do zapewniania przybliżeniem środowiska, który może służyć do obliczenia odbić — jest to nazywane *mapowanie środowiska*— lub w celu zapewnienia teksturę dla kulistego obiektów z mniejszymi zniekształceniami niż podstawowy, można podać dwuwymiarową tekstury.

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Edytor obrazów](../designers/image-editor.md)|Opisuje sposób używania edytora obrazów do pracy z teksturami i obrazami.|
|[Przykłady edytora obrazów](../designers/image-editor-examples.md)|Zawiera łącza do tematów, które pokazują, jak używać edytora obrazów do wykonywania typowych obraz zadania przetwarzania.|