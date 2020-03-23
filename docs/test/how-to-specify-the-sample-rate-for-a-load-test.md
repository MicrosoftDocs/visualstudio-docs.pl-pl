---
title: 'Porady: określanie wielkości próbki dla ustawień testu obciążenia'
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, run settings
ms.assetid: 51cbe7d6-5dfd-4842-bca3-f7f8a665dc84
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 63b6b9479347b076b7bd9e350e80e4bfa2a36d69
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75594828"
---
# <a name="how-to-specify-the-sample-rate-for-a-load-test-run-setting"></a>Jak: Określ częstotliwość próbkowania dla ustawienia przebiegu testu obciążenia

Po utworzeniu testu obciążenia za pomocą **Kreatora nowego testu obciążenia**można użyć **Edytora testów obciążenia,** aby zmienić właściwości, aby spełnić twoje potrzeby i cele testowania.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Za pomocą **Edytora testów obciążenia**można edytować wartość właściwości **Sample Rate** ustawienia uruchamiania w oknie **Właściwości.** Aby uzyskać pełną listę właściwości ustawień uruchamiania i ich opisy, zobacz [Właściwości ustawień przebiegu testu ładowania](../test/load-test-run-settings-properties.md).

Wybierz odpowiednią wartość dla **sample rate** właściwości dla ustawienia przebiegu testu obciążenia na podstawie długości testu obciążenia. Mniejsza częstotliwość próbkowania, taka jak wartość domyślna wynosząca pięć sekund, wymaga więcej miejsca w bazie danych wyników testu obciążenia. W przypadku dłuższych testów obciążenia zwiększenie częstotliwości próbkowania zmniejsza ilość zbieranych danych. Aby uzyskać więcej informacji, zobacz [Jak: Określanie częstotliwości próbkowania dla ustawienia przebiegu testu obciążenia](../test/how-to-specify-the-sample-rate-for-a-load-test.md).

Oto kilka wskazówek dotyczących przykładowych stawek:

|Czas trwania testu obciążenia|Zalecana częstotliwość próbkowania|
|-|-----------------------------|
|\<1 godz.|5 sekund|
|1 - 8 godzin|15 sekund|
|8 - 24 godziny|30 sekund|
|> 24 godziny|60 sekund|

## <a name="to-specify-performance-counter-sampling-rate-in-a-run-setting"></a>Aby określić częstotliwość próbkowania licznika wydajności w ustawieniu uruchamiania

1. Otwórz test obciążenia.

     Pojawi się **Edytor testów obciążenia.** Zostanie wyświetlone drzewo testu obciążenia.

2. W drzewie testu obciążenia w folderze **Uruchom ustawienia** wybierz ustawienie uruchamiania, dla którego chcesz określić częstotliwość próbkowania.

3. W menu **Widok** wybierz polecenie **Okno Właściwości**.

     Kategorie i właściwości ustawienia uruchamiania obciążenia są wyświetlane w oknie **Właściwości.**

4. We właściwości **Sample Rate** wprowadź wartość czasu, która wskazuje częstotliwość, z jaką test obciążenia będzie zbierał dane licznika wydajności.

5. Po zakończeniu zmiany właściwości wybierz polecenie **Zapisz** w menu **Plik.** Następnie można uruchomić test obciążenia przy użyciu nowej wartości **częstotliwość próbkowania.**

## <a name="see-also"></a>Zobacz też

- [Konfigurowanie ustawień przebiegu testu obciążenia](../test/configure-load-test-run-settings.md)
- [Właściwości scenariusza testu obciążenia](../test/load-test-scenario-properties.md)
