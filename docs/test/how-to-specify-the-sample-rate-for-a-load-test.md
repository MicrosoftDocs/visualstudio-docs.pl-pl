---
title: Określ częstotliwość próbkowania dla ustawienia przebiegu testu obciążenia
description: Dowiedz się, jak edytować częstotliwość próbkowania dla wartości ustawienia uruchamiania w okno Właściwości przy użyciu Edytor testu obciążeniowego.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, run settings
ms.assetid: 51cbe7d6-5dfd-4842-bca3-f7f8a665dc84
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c21e38671a43755c55a3f0c37c5b8ab40ae11530
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/30/2020
ms.locfileid: "96329007"
---
# <a name="how-to-specify-the-sample-rate-for-a-load-test-run-setting"></a>Instrukcje: Określanie współczynnika próbkowania dla ustawienia przebiegu testu obciążenia

Po utworzeniu testu obciążenia z **nowym Kreator testu obciążeniowego** można użyć **Edytor testu obciążeniowego** , aby zmienić właściwości, aby spełniały potrzeby testowania i cele.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Za pomocą **Edytor testu obciążeniowego** można edytować wartość właściwości **częstotliwość próbkowania** ustawienia przebiegu w oknie **Właściwości** . Aby uzyskać pełną listę właściwości parametrów uruchomieniowych i ich opisów, zobacz [właściwości ustawień przebiegu testu obciążenia](../test/load-test-run-settings-properties.md).

Wybierz odpowiednią wartość dla właściwości **częstotliwość próbkowania** dla ustawienia przebiegu testu obciążenia na podstawie długości testu obciążenia. Mniejsza częstotliwość próbkowania, taka jak domyślna wartość pięć sekund, wymaga więcej miejsca w bazie danych wyników testu obciążenia. W przypadku dłuższych testów obciążenia zwiększenie szybkości próbkowania zmniejsza ilość zbieranych danych. Aby uzyskać więcej informacji, zobacz [How to: Określanie współczynnika próbkowania dla ustawienia przebiegu testu obciążenia](../test/how-to-specify-the-sample-rate-for-a-load-test.md).

Poniżej przedstawiono niektóre wskazówki dotyczące stawek próbek:

|Czas trwania testu obciążenia|Zalecana częstotliwość próbkowania|
|-|-----------------------------|
|\< 1 godzina|5 sekund|
|1-8 godzin|15 sekund|
|8-24 godzin|30 sekund|
|> 24 godziny|60 sekund|

## <a name="to-specify-performance-counter-sampling-rate-in-a-run-setting"></a>Aby określić częstotliwość próbkowania licznika wydajności w ustawieniu uruchamiania

1. Otwórz test obciążenia.

     Zostanie wyświetlona **Edytor testu obciążeniowego** . Zostanie wyświetlone drzewo testu obciążenia.

2. W drzewie testu obciążenia w folderze **Parametry uruchomieniowe** wybierz ustawienie uruchomieniowe, dla którego chcesz określić częstotliwość próbkowania.

3. W menu **Widok** wybierz polecenie **okno właściwości**.

     Kategorie i właściwości ustawienia przebiegu obciążenia są wyświetlane w oknie **Właściwości** .

4. We właściwości **częstotliwość próbkowania** wprowadź wartość czasu wskazującą częstotliwość, z jaką test obciążenia będzie zbierać dane licznika wydajności.

5. Po zakończeniu zmiany właściwości wybierz pozycję **Zapisz** w menu **plik** . Następnie można uruchomić test obciążenia przy użyciu nowej wartości **współczynnika próbkowania** .

## <a name="see-also"></a>Zobacz też

- [Skonfiguruj ustawienia przebiegu testu obciążenia](../test/configure-load-test-run-settings.md)
- [Właściwości scenariusza testu obciążenia](../test/load-test-scenario-properties.md)
