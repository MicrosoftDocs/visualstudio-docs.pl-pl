---
title: Ustawienia rejestrowania testów obciążenia
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, logging, modifying
ms.assetid: 9649226a-857d-41ef-8ec7-047b6e498033
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 64e65a08910757d564e1fca0d3280770a1a60af9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646655"
---
# <a name="modify-load-test-logging-settings"></a>Modyfikowanie ustawień rejestrowania testu obciążenia

Wynik testu obciążenia dla zakończonego testu obciążenia zawiera próbki liczników wydajności i informacje o błędach, które zostały zebrane w dzienniku okresowo z komputerów poddawanych testom. Duża liczba próbek licznika wydajności może być zbierana w trakcie przebiegu testu obciążenia. Ilość zbieranych danych wydajności zależy od długości przebiegu, interwału próbkowania, liczby komputerów poddawanych testom oraz liczby liczników do zebrania. W przypadku dużego testu obciążenia ilość zbieranych danych wydajności może być łatwo większa niż kilka gigabajtów. w związku z tym można rozważyć modyfikowanie częstotliwości zapisywania danych w dzienniku. Zobacz [kontrolery testów i agenci testowi](configure-test-agents-and-controllers-for-load-tests.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

*Kontroler testów* buforuje wszystkie zebrane dane próbkowania testu obciążenia do dziennika bazy danych, podczas gdy test jest uruchomiony. Dodatkowe dane, takie jak szczegóły czasu i szczegóły błędu, są ładowane do bazy danych po zakończeniu testu.

|Zadanie|Skojarzone tematy|
|-|-----------------------|
|**Zapisz dzienniki w przypadku niepowodzenia testu obciążenia:** Możesz określić, czy chcesz zapisać dziennik testu za każdym razem, gdy test obciążenia zakończy się niepowodzeniem.|-   [instrukcje: Określanie, czy niepowodzenia testu są zapisywane w dziennikach testów](../test/how-to-specify-if-test-failures-are-saved-to-test-logs.md)|
|**Ustaw maksymalny rozmiar pliku dziennika:** Można edytować plik konfiguracyjny XML, który jest skojarzony z usługą kontrolera testów, aby określić maksymalny rozmiar pliku, który ma być używany w pliku dziennika.|Zmodyfikuj `<add key="LogSizeLimitInMegs" value="20"/>` w pliku konfiguracyjnym XML *QTCcontroller. exe. config* .|

## <a name="see-also"></a>Zobacz także

- [Skonfiguruj ustawienia przebiegu testu obciążenia](../test/configure-load-test-run-settings.md)