---
title: Ustawienia rejestrowania testu obciążenia
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, logging, modifying
ms.assetid: 9649226a-857d-41ef-8ec7-047b6e498033
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0c0a9967f1248c6dc23c5d70be35788ad9e05eb2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75566309"
---
# <a name="modify-load-test-logging-settings"></a>Modyfikowanie ustawień rejestrowania testu obciążenia

Wynik testu obciążenia dla testu obciążenia zakończonego zawiera próbki licznika wydajności i informacje o błędzie, które zostały zbierane w dzienniku okresowo z komputerów pod-test. Wiele próbek licznika wydajności można zbierać w trakcie przebiegu testu obciążenia. Ilość danych wydajności, które są zbierane zależy od długości uruchomienia, interwał próbkowania, liczba komputerów w fazie testów i liczba liczników do zbierania. W przypadku testu dużego obciążenia ilość danych wydajności, które są zbierane, może być łatwo kilka gigabajtów; w związku z tym można rozważyć zmodyfikowanie, jak często dane są zapisywane w dzienniku. Zobacz [Kontrolery testów i agenci testowi](configure-test-agents-and-controllers-for-load-tests.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

*Kontroler testu* buforuje wszystkie zebrane dane próbki testu obciążenia do dziennika bazy danych, gdy test jest uruchomiony. Dodatkowe dane, takie jak szczegóły chronometrażu i szczegóły błędu, są ładowane do bazy danych po zakończeniu testu.

|Zadanie|Skojarzone tematy|
|-|-----------------------|
|**Zapisz dzienniki, jeśli test obciążenia zakończy się niepowodzeniem:** Można określić, czy chcesz zapisać dziennik testu, gdy test obciążenia zakończy się niepowodzeniem.|-   [Jak: Określ, czy błędy testu są zapisywane w dziennikach testowych](../test/how-to-specify-if-test-failures-are-saved-to-test-logs.md)|
|**Ustaw maksymalny rozmiar pliku dziennika:** Można edytować plik konfiguracyjny XML skojarzony z usługą kontrolera testów, aby określić maksymalny rozmiar pliku, który ma być używany dla pliku dziennika.|Modyfikuj `<add key="LogSizeLimitInMegs" value="20"/>` plik konfiguracyjny *QTCcontroller.exe.config* XML.|

## <a name="see-also"></a>Zobacz też

- [Konfigurowanie ustawień przebiegu testu obciążenia](../test/configure-load-test-run-settings.md)
