---
title: Stos wywołań zdarzeń grafiki | Microsoft Docs
description: Przejrzyj stos wywołań zdarzeń grafiki w analizator grafiki programu Visual Studio, aby zmapować relacje między problematycznymi zdarzeniami graficznymi a kodem źródłowym aplikacji.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.graphics.callstack
ms.assetid: 8a30168d-8b39-4de1-b094-c7356ba101a3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 85712f2b8971b2b5284dab89d90eecec9010e9b4
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2020
ms.locfileid: "97727753"
---
# <a name="graphics-event-call-stack"></a>Stos wywołań zdarzeń grafiki
Stos wywołań zdarzeń grafiki w analizator grafiki programu Visual Studio ułatwia Mapowanie relacji między problematycznymi zdarzeniami graficznymi a kodem źródłowym aplikacji.

 To jest okno stosu wywołań zdarzeń:

 ![Stos wywołań poprzedzający zdarzenie DrawIndexed.](media/gfx_diag_demo_graphics_event_call_stack_orientation.png "gfx_diag_demo_graphics_event_call_stack_orientation")

## <a name="understanding-the-graphics-event-call-stack"></a>Zrozumienie stosu wywołań zdarzeń grafiki
 Możesz użyć stosu wywołań zdarzeń, aby zrozumieć przepływ wykonywania, który doprowadził do określonego zdarzenia Direct3D. Jest podobna do okna stosu wywołań programu Visual Studio, z tą różnicą, że zamiast wyświetlania bieżącego stosu wywołań bieżącego wątku w działającej aplikacji jest wyświetlany stos wywołań, który istniał po wystąpieniu wybranego zdarzenia Direct3D. Ze stosu wywołań zdarzeń można przejść do witryny wywołania wybranego zdarzenia Direct3D, aby sprawdzić otaczający kod.

 Przy użyciu stosu wywołań zdarzeń do identyfikowania ścieżki kodu, z której pochodzi zdarzenie problemu, można użyć swojej bazy kodu w celu wywnioskowania potencjalnych źródeł problemu lub dodać punkty przerwania w kodzie źródłowym aplikacji, aby można było użyć tradycyjnych technik debugowania do sprawdzenia, jak stan aplikacji lub parametrów zdarzeń powoduje niezachowanie zdarzenia. Ta analiza może pomóc w znalezieniu problemów w kodzie źródłowym, które są w manifeście tylko jako problemy z renderowaniem.

### <a name="graphics-event-call-stack-information"></a>Informacje o stosie wywołań zdarzeń grafiki
 Stos wywołań zdarzeń nie obsługuje zdarzeń przed ramkami ani zdarzeń zdefiniowanych przez użytkownika. Stos wywołań zdarzeń grafiki jest wyświetlany w formacie tabeli.

|Kolumna|Opis|
|------------|-----------------|
|**Nazwa**|Symbol, który jednoznacznie identyfikuje funkcję, która zawiera lokację wywołania. Symbol debugowania dla funkcji jest wyświetlany, gdy jest dostępny; w przeciwnym razie zostanie wyświetlone przesunięcie funkcji.|
|**Plik**|Nazwa pliku kodu źródłowego lub pliku biblioteki, który zawiera lokację wywołania.|
|**Lokalizacja**|Numer wiersza dla witryny wywołania.|

### <a name="links-to-graphics-objects"></a>Linki do obiektów graficznych
 Aby zrozumieć wybrane zdarzenie grafiki, można potrzebować informacji o obiektach Direct3D, które są z nim skojarzone. Okno **stosu wywołań zdarzeń grafiki** zawiera linki do tych informacji.

## <a name="see-also"></a>Zobacz też
- [Przewodnik: brak obiektów spowodowany cieniowaniem wierzchołków](walkthrough-missing-objects-due-to-vertex-shading.md)