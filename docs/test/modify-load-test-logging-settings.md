---
title: Test obciążeniowy ustawienia rejestrowania
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, logging, modifying
ms.assetid: 9649226a-857d-41ef-8ec7-047b6e498033
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9751ce3b08a0ac963cccdf091ccb99001c6f2c9f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62785776"
---
# <a name="modify-load-test-logging-settings"></a>Modyfikowanie ustawień rejestrowania testu obciążeniowego

Wynik testu obciążenia dla ukończonego testu obciążenia zawiera próbki liczników wydajności i informacje o błędach, które zostały zebrane w dzienniku okresowo z komputerów objętych testami. Duża liczba próbek liczników wydajności może być zbierana w trakcie przebiegu testu obciążeniowego. Dane wydajności, które są zbierane zależy od długości przebiegu, interwał próbkowania, liczby komputerów w ramach testu i liczbę liczników do zbierania. Na dużym teście obciążenia ilość zebranych danych wydajności może łatwo wynieść kilka gigabajtów; w związku z tym, należy rozważyć zmodyfikowanie jak często dane są zapisywane w dzienniku. Zobacz [kontrolerów testów i agentów testowych](configure-test-agents-and-controllers-for-load-tests.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

*Kontrolera testów* buforuje wszystkie zebrane obciążenia testu przykładowe dane do dziennika bazy danych, gdy uruchomiony jest test. Dodatkowe dane, takie jak szczegółowych informacji o czasie i szczegóły błędu są ładowane do bazy danych, po zakończeniu testu.

|Zadanie|Skojarzone tematy|
|-|-----------------------|
|**Zapisywanie dzienników, w przypadku niepowodzenia testu obciążeniowego:** Można określić, jeśli chcesz zapisać dziennik testu, zawsze wtedy, gdy test obciążenia kończy się niepowodzeniem.|-   [Jak: Określ, czy niepowodzenia testu są zapisywane do testowania dzienników](../test/how-to-specify-if-test-failures-are-saved-to-test-logs.md)|
|**Ustaw maksymalny rozmiar pliku dla pliku dziennika:** Można edytować plik konfiguracyjny XML, który jest skojarzony z usługą kontrolera testu, aby określić maksymalny rozmiar pliku do pliku dziennika.|Modyfikowanie `<add key="LogSizeLimitInMegs" value="20"/>` w *QTCcontroller.exe.config* plik konfiguracyjny XML.|

## <a name="see-also"></a>Zobacz także

- [Konfigurowanie ustawień testu obciążenia](../test/configure-load-test-run-settings.md)