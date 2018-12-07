---
title: 'Porady: określanie wielkości próbki dla ustawień testu obciążenia'
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, run settings
ms.assetid: 51cbe7d6-5dfd-4842-bca3-f7f8a665dc84
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: b022b4648931bf0e403df589d37cb086fb2a9c2c
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53053052"
---
# <a name="how-to-specify-the-sample-rate-for-a-load-test-run-setting"></a>Porady: określanie wielkości próbki dla ustawień przebiegu testu obciążeniowego

Po utworzeniu testu obciążenia za pomocą **Kreatora nowego testu obciążeniowego**, możesz użyć **edytora testu obciążenia** można zmienić właściwości w celu spełnienia potrzeb i celów testowania.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Za pomocą **edytora testu obciążenia**, można edytować ustawienia przebiegu **częstotliwość próbkowania** wartości właściwości w **właściwości** okna. Aby uzyskać pełną listę właściwości parametrów uruchomieniowych i ich opisów, zobacz [właściwości ustawień przebiegu testu obciążenia](../test/load-test-run-settings-properties.md).

Wybierz odpowiednią wartość dla **częstotliwość próbkowania** właściwość uruchomieniowych testu obciążeniowego na podstawie długości testu obciążenia. Mniejsza częstotliwość próbkowania, np. wartość domyślna pięć sekund, wymaga więcej miejsca w bazie danych wyników testu obciążenia. Dla dłuższych testów obciążenia zwiększenie częstotliwości próbkowania zmniejsza ilość zbieranych danych. Aby uzyskać więcej informacji, zobacz [porady: określanie wielkości próbki dla ustawień przebiegu testu obciążeniowego](../test/how-to-specify-the-sample-rate-for-a-load-test.md).

Oto niektóre wytyczne dotyczące częstotliwości próbkowania:

|Czas trwania testu obciążenia|Zalecana częstotliwość próbkowania|
|-|-----------------------------|
|\< 1 godzina|5 sekund|
|1 - 8 godzin|15 sekund|
|8 - 24 godziny|30 sekund|
|> 24 godziny|60 sekund|

## <a name="to-specify-performance-counter-sampling-rate-in-a-run-setting"></a>Aby określić częstotliwość próbkowania licznika wydajności w ustawieniach testu

1.  Otwórz test obciążenia.

     **Edytora testu obciążenia** pojawia się. Zostanie wyświetlone drzewo testu obciążenia.

2.  Obciążenia testowanie drzewie w **parametrów uruchomieniowych** folderu, wybierz parametr uruchomieniowy, które chcesz określić częstotliwość próbkowania dla.

3.  Na **widoku** menu, wybierz opcję **okno właściwości**.

     Uruchom ustawienie obciążenia użytkownika kategorii i właściwości są wyświetlane w **właściwości** okna.

4.  W **częstotliwość próbkowania** właściwości wprowadź wartość czasu, która wskazuje częstotliwość, jaką testu obciążeniowego będzie zbierać dane licznika wydajności.

5.  Po zakończeniu, zmiana wartości właściwości, wybierz **Zapisz** na **pliku** menu. Następnie możesz uruchomić test obciążenia za pomocą nowego **częstotliwość próbkowania** wartość.

## <a name="see-also"></a>Zobacz także

- [Konfigurowanie ustawień testu obciążenia](../test/configure-load-test-run-settings.md)
- [Właściwości scenariusza testów obciążenia](../test/load-test-scenario-properties.md)