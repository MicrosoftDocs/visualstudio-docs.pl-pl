---
title: Praca z teksturami i obrazami | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: b9fbc8fa-66d1-4055-8460-24d8b8fbe43e
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 93813aa734c615e7f045c98c776e600be4ee3fab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663938"
---
# <a name="working-with-textures-and-images"></a>Praca z obrazami i teksturami
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz użyć edytora obrazów w programie, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Aby utworzyć i zmodyfikować tekstury i obrazy. Edytor obrazów obsługuje bogate formaty tekstury i obrazów, takie jak te, które są używane w programowaniu aplikacji DirectX.

> [!NOTE]
> Edytor obrazów nie obsługuje obrazów o małym kolorze, takich jak ikony lub kursory. Aby tworzyć lub modyfikować te rodzaje obrazów, użyj [edytora obrazu dla ikon](https://msdn.microsoft.com/library/586d2b8b-0348-4883-a85d-1ff0ddbf14dd).

## <a name="textures-and-images"></a>Tekstury i obrazy
 Tekstury i obrazy są, na poziomie podstawowym, tylko tabele danych, które są używane do zapewniania wizualnych szczegółów w aplikacjach graficznych. Rodzaj szczegółów, które zapewnia teksturę lub obraz, zależy od tego, w jaki sposób jest używany, ale przykłady kolorów, wartości alfa (przezroczystość), normalne wartości powierzchni i wysokość są typowymi przykładami. Podstawowa różnica między teksturą a obrazem polega na tym, że tekstura jest przeznaczona do użycia razem z reprezentacją kształtu — zazwyczaj jest to model trójwymiarowy — do wyrażania kompletnego obiektu lub sceny, ale obraz jest zazwyczaj autonomiczną reprezentacją obiektu lub sceny.

 Typowe rodzaje tekstur obejmują:

 Mapy tekstury map tekstury zawierają wartości kolorów, które są zorganizowane jako macierz Jednowymiarowa, dwulub 3-wymiarową. Są one używane do podania szczegółów koloru dla obiektu, którego to dotyczy. Kolory są powszechnie kodowane przy użyciu kanałów RGB (czerwony, zielony, niebieski) i mogą zawierać czwarty kanał, alfa, który reprezentuje przezroczystość. Mniej często kolory mogą być zakodowane w innym schemacie kolorów lub czwarty kanał może zawierać dane inne niż alfa — na przykład wysokość.

 Normalne mapy normalne mapy zawierają normalne. Są one używane do zapewnienia szczegółowych informacji o oświetleniu danego obiektu. Normalne są zazwyczaj kodowane przy użyciu czerwonych, zielonych i niebieskich składników koloru do przechowywania wymiarów x, y i z wektora. Istnieją jednak inne kodowania, na przykład kodowanie, które opierają się na współrzędnych biegunowych.

 Mapy wysokości mapy wysokooci zawierają dane pól wysokości. Są one używane do zapewnienia postaci geometrycznej szczegółów dla danego obiektu, przy użyciu kodu modułu cieniującego do obliczenia żądanego efektu lub zapewnienia punktów danych do użycia, takich jak generacja terenu. Wartości wysokości są powszechnie kodowane przy użyciu jednego kanału w tekstury.

 Mapy modułów mapy modułów mogą zawierać różne typy danych — na przykład kolory lub normalne, ale są zorganizowane jako sześć tekstur na powierzchniach modułu. W związku z tym mapy modułów nie są próbkowane przez dostarczenie współrzędnych tekstury, ale przez dostarczenie wektora, którego źródłem jest środek modułu; próbka jest wykonywana w punkcie, w którym wektor przecina moduł. Mapy modułów służą do zapewnienia przybliżenia środowiska, którego można użyć do obliczenia odbić — jest to nazywane *mapowaniem środowiska*— lub w celu zapewnienia tekstury dla obiektów sferycznych o mniejszej zniekształceniu niż w przypadku warstw podstawowych.

 Wszelka tekstura może być zakodowana i skompresowana na wiele sposobów, które są ortogonalne do typu danych, które są przechowywane tekstury, lub do zwymiarowania lub "kształtu" tekstury. Jednak różne metody kodowania i kompresji dają lepsze wyniki dla różnych rodzajów danych.

 Korzystając z edytora obrazów, można tworzyć i modyfikować tekstury i obrazy w sposób podobny do innych edytorów obrazów. Edytor obrazów udostępnia również mipmapping i inne funkcje do użycia z grafikami trójwymiarowymi oraz obsługuje wiele wysoce skompresowanych, przyspieszanych sprzętowo formatów tekstury obsługiwanych przez technologię DirectX.

## <a name="related-topics"></a>Powiązane tematy

|Tytuł|Opis|
|-----------|-----------------|
|[Edytor obrazów](../designers/image-editor.md)|Opisuje, jak używać edytora obrazów do pracy z teksturami i obrazami.|
|[Przykłady edytora obrazów](../designers/image-editor-examples.md)|Zawiera łącza do tematów, które pokazują, jak używać edytora obrazów do wykonywania typowych zadań przetwarzania obrazów.|
