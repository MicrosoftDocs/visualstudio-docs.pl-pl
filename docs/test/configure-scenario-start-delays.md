---
title: Skonfiguruj opóźnienia uruchamiania scenariusza na potrzeby testowania obciążenia
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, scenarios, start delays
ms.assetid: 2f634fba-8dfa-4c7a-a8b9-be867b78d16a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 83e3086aa8181156a9d35a906a9d3a7e60575cd2
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68918442"
---
# <a name="configure-scenario-start-delays-in-load-tests"></a>Konfiguruj opóźnienia uruchamiania scenariusza w testach obciążenia

Określ opóźnienie przed rozpoczęciem scenariusza w teście obciążenia przy użyciu Edytor testu obciążeniowego i okna **Właściwości** .

Na przykład możesz chcieć użyć właściwości **czas rozpoczęcia opóźnienia** , jeśli potrzebujesz jednego scenariusza, aby rozpocząć produkowanie elementów, które są używane przez inny scenariusz. Można opóźnić scenariusz zużywający, aby umożliwić tworzenie w scenariuszu tworzenia danych.

Innym przykładem jest to, że może istnieć jeden scenariusz, który jest uruchamiany tylko w określonym czasie dnia. Dlatego chcesz opóźnić początek scenariusza, aby symulować ten scenariusz.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="specify-the-delay-start-time-of-a-scenario"></a>Określ czas rozpoczęcia opóźnienia scenariusza

Możesz określić opóźnienie przed początkiem scenariusza w teście obciążenia, używając Edytor testu obciążeniowego, aby zmienić właściwość **czas rozpoczęcia opóźnienia** w oknie **Właściwości** .

> [!NOTE]
> Aby uzyskać pełną listę właściwości scenariusza testów obciążenia wraz z opisami, zobacz [właściwości scenariusza testów obciążenia](../test/load-test-scenario-properties.md).

Przykładem wystąpienia, gdy możesz chcieć użyć właściwości **czas rozpoczęcia opóźnienia** , gdy potrzebujesz jednego scenariusza, aby rozpocząć tworzenie elementów, które są używane przez inny scenariusz. Można opóźnić scenariusz zużywający, aby umożliwić tworzenie w scenariuszu tworzenia danych.

Innym przykładem jest to, że może istnieć jeden scenariusz, który jest uruchamiany tylko w określonym dniu. W związku z tym chcesz opóźnić początek scenariusza, aby symulować ten scenariusz.

> [!NOTE]
> Aby uzyskać pełną listę właściwości parametrów uruchomieniowych i ich opisów, zobacz [właściwości scenariusza testu obciążenia](../test/load-test-scenario-properties.md).

### <a name="to-specify-the-delay-start-time-for-a-scenario"></a>Aby określić czas rozpoczęcia opóźnienia dla scenariusza

1. Otwórz test obciążenia.

     Zostanie wyświetlony Edytor testów obciążenia. Zostanie wyświetlone drzewo testu obciążenia.

2. W folderze **scenariuszy** drzew testów obciążenia wybierz węzeł scenariusza, dla którego chcesz określić czas rozpoczęcia opóźnienia.

3. Na **widoku** menu, wybierz opcję **okno właściwości**.

     Kategorie i właściwości scenariusza są wyświetlane w **właściwości** okna.

4. W polu tekstowym dla właściwości **czas rozpoczęcia opóźnienia** wpisz wartość czasu, która wskazuje czas oczekiwania po uruchomieniu testu obciążenia przed rozpoczęciem pracy w trakcie testu obciążenia.

    > [!NOTE]
    > Jeśli wartość właściwości Disable ( **Wyłącz** ) dla scenariusza jest ustawiona na **wartość true**, po okresie rozgrzewania zostanie zastosowana wartość właściwości czas **rozpoczęcia opóźnienia** . Można kontrolować, które scenariusze są uwzględniane w rozgrzewaniu, przy użyciu właściwości scenariusz **Wyłącz podczas rozgrzewania** .

5. Po zmianie właściwości wybierz **Zapisz** na **pliku** menu. Następnie można uruchomić test obciążenia przy użyciu nowej wartości **czasu rozpoczęcia opóźnienia** .

## <a name="enable-and-disable-whether-a-scenario-runs-during-the-warm-up-period"></a>Włącz i Wyłącz, czy scenariusz jest uruchamiany w okresie rozgrzewania

Właściwość **disable in rozgrzewania** jest ustawiana za pomocą okna **Właściwości** . Edytowanie właściwości scenariusza testu obciążenia jest ustawiane przez Edytor testu obciążeniowego.

Właściwość **disable in rozgrzewania** służy do wskazywania, czy scenariusz ma być uruchamiany czy nie uruchamiany w okresie rozgrzewania określonym w właściwości **czas rozpoczęcia opóźnienia** . Aby uzyskać więcej informacji, zapoznaj się z poprzednią procedurą [Określ czas rozpoczęcia opóźnienia scenariusza](#specify-the-delay-start-time-of-a-scenario).

> [!NOTE]
> Aby uzyskać pełną listę właściwości parametrów uruchomieniowych i ich opisów, zobacz [właściwości scenariusza testu obciążenia](../test/load-test-scenario-properties.md).

### <a name="to-enable-or-disable-the-warm-up-period-for-a-scenario"></a>Aby włączyć lub wyłączyć okres rozgrzewania dla scenariusza

1. Otwórz test obciążenia.

     **Edytora testu obciążenia** pojawia się. Zostanie wyświetlone drzewo testu obciążenia.

2. W folderze **scenariuszy** drzew testów obciążenia wybierz węzeł scenariusza, dla którego chcesz zmienić zachowanie rozgrzewania.

3. Na **widoku** menu, wybierz opcję **okno właściwości**.

     Kategorie i właściwości tego scenariusza są wyświetlane w **właściwości** okna.

     W właściwości **Wyłącz podczas rozgrzewania** wybierz wartość **prawda** lub **Fałsz.**

4. Po zakończeniu, zmiana wartości właściwości, wybierz **Zapisz** na **pliku** menu. Następnie można uruchomić test obciążenia przy użyciu nowej wartości **disable podczas rozgrzewania** .

## <a name="see-also"></a>Zobacz także

- [Edytowanie scenariuszy testu obciążenia](../test/edit-load-test-scenarios.md)
- [Konfigurowanie agentów testowych i kontrolerów testów obciążenia testów](../test/configure-test-agents-and-controllers-for-load-tests.md)
- [Właściwości scenariusza testów obciążenia](../test/load-test-scenario-properties.md)