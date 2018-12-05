---
title: Dodawanie parametrów uruchomieniowych do testu obciążenia w programie Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, run settings, adding
- load tests, run settings
ms.assetid: 257d2a24-d582-4cfe-8b2b-51f51ba9cc84
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: e894bb0b53240795ad2bf7505ba081dbf479989d
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2018
ms.locfileid: "52896617"
---
# <a name="how-to-add-additional-run-settings-to-a-load-test"></a>Porady: Dodawanie dodatkowych ustawień przebiegu testu obciążenia

Parametry uruchomieniowe testu obciążeniowego decydują o różnych innych ustawieniach. Należą do nich ustawienia czasu trwania testu, poziomu szczegółowości zbierania wyników oraz zbiorów liczników, z których dane mają być zbierane podczas przebiegów testowych. Dla każdego testu obciążeniowego można utworzyć i zapisać wiele parametrów uruchomieniowych, a następnie wybrać jedno konkretne ustawienie do użycia podczas wykonywania testu. Początkowy parametr uruchomieniowy dodaje się do testu obciążeniowego podczas tworzenia testu obciążeniowego za pomocą **Kreatora nowego testu obciążeniowego**.

Do testu obciążeniowego można dodać więcej parametrów uruchomieniowych z różnymi ustawieniami właściwości, co pozwoli wykonywać te testy w różnych warunkach. Na przykład można dodać nowe ustawienie testu określające inną częstotliwość próbkowania albo dłuższy czas trwania. W danej sesji można używać tylko jednego parametru uruchomieniowego. Przed rozpoczęciem testu należy go też wskazać jako aktywny.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-add-another-run-setting"></a>Aby dodać kolejny parametr uruchomieniowy

1.  Otwórz test obciążenia.

2.  (Opcjonalnie) Rozwiń **parametrów uruchomieniowych** folderu.

3.  Kliknij prawym przyciskiem myszy **parametrów uruchomieniowych** i wybierz polecenie **Dodaj parametry uruchomieniowe**.

     Nowy parametr uruchomieniowy jest dodawany do **parametrów uruchomieniowych** folderu.

4.  Na **widoku** menu, wybierz **okno właściwości**.

     **Właściwości** zostanie wyświetlone okno z właściwościami, dla wybranego ustawienia uruchamiania.

5.  W **właściwości** okna, użyj pola tekstowego dla **nazwa** właściwości nadaj nowemu Ustawianie nazwy, która opisuje przeznaczenie parametru uruchomieniowego (na przykład **parametr uruchomieniowy: przebieg pięciominutowy** ).

6.  Użyj **właściwości** okna, aby zmienić parametry uruchomieniowe. Na przykład zmienić czas trwania testu na **00:05:00** Aby uruchomić test na pięć minut.

    > [!NOTE]
    > Aby uzyskać pełną listę właściwości parametrów uruchomieniowych i ich opisów, zobacz [właściwości ustawień przebiegu testu obciążenia](../test/load-test-run-settings-properties.md).

     Teraz można określić, że dodany parametr uruchomieniowy ma być używany, ustawiając mu status aktywności. Aby uzyskać więcej informacji, zobacz [jak: Wybierz aktywne ustawienia uruchamiania dla testu obciążeniowego](../test/how-to-select-the-active-run-setting-for-a-load-test.md).

## <a name="see-also"></a>Zobacz także

- [Konfigurowanie ustawień testu obciążenia](../test/configure-load-test-run-settings.md)
- [Określanie zbiorów liczników oraz zasad progu dla komputerów w teście obciążeniowym](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)