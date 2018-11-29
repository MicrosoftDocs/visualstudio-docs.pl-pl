---
title: Ustawienia rejestrowania w programie Visual Studio Test obciążeniowy
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, logging, modifying
ms.assetid: 9649226a-857d-41ef-8ec7-047b6e498033
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 867e586b5a50dee47a86d8a57a978f51ee0d0c3b
ms.sourcegitcommit: a811f6a194ccd40d844e74e618d847df87c85c16
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/29/2018
ms.locfileid: "52621370"
---
# <a name="modify-load-test-logging-settings"></a>Modyfikowanie ustawień rejestrowania testu obciążeniowego

Wynik testu obciążenia dla ukończonego testu obciążenia zawiera próbki liczników wydajności i informacje o błędach, które zostały zebrane w dzienniku okresowo z komputerów objętych testami. Duża liczba próbek liczników wydajności może być zbierana w trakcie przebiegu testu obciążeniowego. Dane wydajności, które są zbierane zależy od długości przebiegu, interwał próbkowania, liczby komputerów w ramach testu i liczbę liczników do zbierania. Na dużym teście obciążenia ilość zebranych danych wydajności może łatwo wynieść kilka gigabajtów; w związku z tym, należy rozważyć zmodyfikowanie jak często dane są zapisywane w dzienniku. Zobacz [kontrolerów testów i agentów testowych](configure-test-agents-and-controllers-for-load-tests.md).

*Kontrolera testów* buforuje wszystkie zebrane obciążenia testu przykładowe dane do dziennika bazy danych, gdy uruchomiony jest test. Dodatkowe dane, takie jak szczegółowych informacji o czasie i szczegóły błędu są ładowane do bazy danych, po zakończeniu testu.

|Zadanie|Skojarzone tematy|
|-|-----------------------|
|**Zapisywanie dzienników, w przypadku niepowodzenia testu obciążeniowego:** można określić, jeśli chcesz zapisać dziennik testu, zawsze wtedy, gdy test obciążenia kończy się niepowodzeniem.|-   [Porady: Określanie, czy niepowodzenia testu są zapisywane do testowania dzienników](../test/how-to-specify-if-test-failures-are-saved-to-test-logs.md)|
|**Ustaw maksymalny rozmiar pliku dla pliku dziennika:** można edytować plik konfiguracji XML, który jest skojarzony z usługi kontrolera testów, aby określić maksymalny rozmiar pliku chcesz użyć dla pliku dziennika.|[Porady: określanie maksymalnego rozmiaru pliku dziennika](../test/how-to-specify-the-maximum-size-for-the-log-file.md)|

## <a name="see-also"></a>Zobacz także

- [Konfigurowanie ustawień testu obciążenia](../test/configure-load-test-run-settings.md)