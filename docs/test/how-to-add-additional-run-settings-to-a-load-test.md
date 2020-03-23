---
title: Dodawanie ustawień uruchamiania do testu obciążenia
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, run settings, adding
- load tests, run settings
ms.assetid: 257d2a24-d582-4cfe-8b2b-51f51ba9cc84
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: adcb50d2c6800c5ce64ab2b7cf16ce9d2a25aaaa
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75584507"
---
# <a name="how-to-add-additional-run-settings-to-a-load-test"></a>Jak: Dodawanie dodatkowych ustawień uruchamiania do testu obciążenia

Parametry uruchomieniowe testu obciążeniowego decydują o różnych innych ustawieniach. Należą do nich ustawienia czasu trwania testu, poziomu szczegółowości zbierania wyników oraz zbiorów liczników, z których dane mają być zbierane podczas przebiegów testowych. Dla każdego testu obciążeniowego można utworzyć i zapisać wiele parametrów uruchomieniowych, a następnie wybrać jedno konkretne ustawienie do użycia podczas wykonywania testu. Ustawienie początkowego uruchomienia jest dodawane do testu obciążenia podczas tworzenia testu obciążenia za pomocą **Kreatora nowego testu obciążenia**.

Do testu obciążeniowego można dodać więcej parametrów uruchomieniowych z różnymi ustawieniami właściwości, co pozwoli wykonywać te testy w różnych warunkach. Na przykład można dodać nowe ustawienie testu określające inną częstotliwość próbkowania albo dłuższy czas trwania. W danej sesji można używać tylko jednego parametru uruchomieniowego. Przed rozpoczęciem testu należy go też wskazać jako aktywny.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-add-another-run-setting"></a>Aby dodać kolejny parametr uruchomieniowy

1. Otwórz test obciążenia.

2. (Opcjonalnie) Rozwiń folder **Uruchom ustawienia.**

3. Kliknij prawym przyciskiem myszy folder **Uruchom ustawienia** i wybierz polecenie Dodaj **ustawienia uruchamiania**.

     Nowe ustawienie uruchamiania zostanie dodane do folderu **Uruchom ustawienia.**

4. W menu **Widok** wybierz polecenie **Okno Właściwości**.

     Okno **Właściwości** jest wyświetlane z właściwościami dla wybranego ustawienia przebiegu.

5. W oknie **Właściwości** użyj pola tekstowego właściwości **Name,** aby nadać nowemu ustawieniu uruchamiania nazwę opisującą intencję ustawienia uruchomienia (na przykład **Uruchom ustawienie: Bieg na pięć minut**).

6. Okno **Właściwości** służy do zmiany ustawień uruchamiania. Na przykład zmień czas trwania uruchomienia na **00:05:00,** aby uruchomić test przez pięć minut.

    > [!NOTE]
    > Aby uzyskać pełną listę właściwości ustawień uruchamiania i ich opisy, zobacz [Właściwości ustawień przebiegu testu ładowania](../test/load-test-run-settings-properties.md).

     Teraz można określić, że dodany parametr uruchomieniowy ma być używany, ustawiając mu status aktywności. Aby uzyskać więcej informacji, zobacz [Jak: Wybierz ustawienie aktywnego uruchamiania dla testu obciążenia](../test/how-to-select-the-active-run-setting-for-a-load-test.md).

## <a name="see-also"></a>Zobacz też

- [Konfigurowanie ustawień przebiegu testu obciążenia](../test/configure-load-test-run-settings.md)
- [Określanie zestawów liczników i reguł progowych dla komputerów w teście obciążenia](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
