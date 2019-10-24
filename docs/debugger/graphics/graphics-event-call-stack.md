---
title: Stos wywołań zdarzeń grafiki | Microsoft Docs
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
ms.openlocfilehash: c221a572264bf6a6aaed9edbec66fb3c0c3ff4b9
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72735513"
---
# <a name="graphics-event-call-stack"></a>Stos wywołań zdarzeń grafiki
Stos wywołań zdarzeń grafiki w analizator grafiki programu Visual Studio ułatwia Mapowanie relacji między problematycznymi zdarzeniami graficznymi a kodem źródłowym aplikacji.

 To jest okno stosu wywołań zdarzeń:

 ![Stos wywołań poprzedzający zdarzenie DrawIndexed.](media/gfx_diag_demo_graphics_event_call_stack_orientation.png "gfx_diag_demo_graphics_event_call_stack_orientation")

## <a name="understanding-the-graphics-event-call-stack"></a>Zrozumienie stosu wywołań zdarzeń grafiki
 Możesz użyć stosu wywołań zdarzeń, aby zrozumieć przepływ wykonywania, który doprowadził do określonego zdarzenia Direct3D. Jest podobna do okna stosu wywołań programu Visual Studio, z tą różnicą, że zamiast wyświetlania bieżącego stosu wywołań bieżącego wątku w działającej aplikacji jest wyświetlany stos wywołań, który istniał po wystąpieniu wybranego zdarzenia Direct3D. Ze stosu wywołań zdarzeń można przejść do witryny wywołania wybranego zdarzenia Direct3D, aby sprawdzić otaczający kod.

 Korzystając ze stosu wywołań zdarzeń w celu zidentyfikowania ścieżki kodu, z której pochodzi zdarzenie problemu, można użyć swojej bazy danych w celu wywnioskowania potencjalnych źródeł problemu lub dodać punkty przerwania w kodzie źródłowym aplikacji, aby można było użyć tradycyjnego Techniki debugowania w celu sprawdzenia, jak stan aplikacji lub parametrów zdarzenia powodują niezachowanie zdarzenia. Ta analiza może pomóc w znalezieniu problemów w kodzie źródłowym, które są w manifeście tylko jako problemy z renderowaniem.

### <a name="graphics-event-call-stack-information"></a>Informacje o stosie wywołań zdarzeń grafiki
 Stos wywołań zdarzeń nie obsługuje zdarzeń przed ramkami ani zdarzeń zdefiniowanych przez użytkownika. Stos wywołań zdarzeń grafiki jest wyświetlany w formacie tabeli.

|Kolumna|Opis|
|------------|-----------------|
|**Nazwa**|Symbol, który jednoznacznie identyfikuje funkcję, która zawiera lokację wywołania. Symbol debugowania dla funkcji jest wyświetlany, gdy jest dostępny; w przeciwnym razie zostanie wyświetlone przesunięcie funkcji.|
|**Rozszerzeniem**|Nazwa pliku kodu źródłowego lub pliku biblioteki, który zawiera lokację wywołania.|
|**Lokalizacja**|Numer wiersza dla witryny wywołania.|

### <a name="links-to-graphics-objects"></a>Linki do obiektów graficznych
 Aby zrozumieć wybrane zdarzenie grafiki, można potrzebować informacji o obiektach Direct3D, które są z nim skojarzone. Okno **stosu wywołań zdarzeń grafiki** zawiera linki do tych informacji.

## <a name="see-also"></a>Zobacz także
- [Przewodnik: brak obiektów spowodowany cieniowaniem wierzchołków](walkthrough-missing-objects-due-to-vertex-shading.md)