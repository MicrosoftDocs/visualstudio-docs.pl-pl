---
title: Konfigurowanie opóźnień Start scenariusz do testowania obciążenia
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, scenarios, start delays
ms.assetid: 2f634fba-8dfa-4c7a-a8b9-be867b78d16a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e053ee01d60d1ce3dcae10e044bb642e11f90dd7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62963796"
---
# <a name="configure-scenario-start-delays-in-load-tests"></a>Konfigurowanie opóźnień uruchamiania scenariuszy w testach obciążenia

Określanie opóźnienia, zanim scenariusza w teście obciążenia rozpocznie się za pomocą edytora testu obciążenia i **właściwości** okna.

Na przykład możesz chcieć użyć **opóźnienie uruchamiania** właściwość, jeśli potrzebujesz jeden scenariusz rozpoczął produkcję elementów, które korzysta inny scenariusz. Można opóźnić scenariusz zużycia w celu umożliwienia scenariuszowi wytwarzania pewnych danych.

Innym przykładem jest, że może mieć jeden scenariusz uruchamianą tylko o porze dnia. Tak ma być opóźnienie rozpoczęcia scenariusza, aby zasymulować to.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="specify-the-delay-start-time-of-a-scenario"></a>Określ opóźnienie czasu rozpoczęcia scenariusza

Można określić opóźnienie przed rozpoczęciem scenariusza w teście obciążenia za pomocą edytora testu obciążenia, aby zmienić **opóźnienie uruchamiania** właściwość **właściwości** okna.

> [!NOTE]
> Aby uzyskać pełną listę właściwości scenariusza testów obciążenia wraz z opisami, zobacz [właściwości scenariusza testów obciążenia](../test/load-test-scenario-properties.md).

 Przykładem wystąpienie, jeśli chcesz używać **opóźnienie uruchamiania** właściwość jest, gdy będziesz potrzebować jeden scenariusz rozpoczął produkcję elementów, które korzysta inny scenariusz. Można opóźnić scenariusz zużycia w celu umożliwienia scenariuszowi wytwarzania pewnych danych.

 Innym przykładem jest, że może mieć jeden scenariusz, w którym jest uruchamiany tylko na porze dnia. W związku z tym należy opóźnić uruchomienie scenariusza, aby zasymulować to.

> [!NOTE]
> Aby uzyskać pełną listę właściwości parametrów uruchomieniowych i ich opisów, zobacz [właściwości scenariusza testów obciążenia](../test/load-test-scenario-properties.md).

### <a name="to-specify-the-delay-start-time-for-a-scenario"></a>Aby określić godzinę rozpoczęcia opóźnienia dla scenariusza

1. Otwórz test obciążenia.

     Zostanie wyświetlony Edytor testów obciążenia. Zostanie wyświetlone drzewo testu obciążenia.

2. Obciążenia test drzew **scenariuszy** folderu, wybierz węzeł scenariusz, dla którego chcesz określić godzinę rozpoczęcia opóźnienie.

3. Na **widoku** menu, wybierz opcję **okno właściwości**.

     Kategorie i właściwości scenariusza są wyświetlane w **właściwości** okna.

4. W polu tekstowym dla **opóźnienie uruchamiania** właściwość, należy wpisać wartość czasu, która wskazuje czas oczekiwania po test obciążenia rozpoczyna się przed rozpoczęciem tego scenariusza, po uruchomieniu testu obciążenia.

    > [!NOTE]
    > Jeśli wartość **Wyłącz podczas rozgrzewania** scenariusza zostaje ustalona **True**, a następnie **opóźnienie uruchamiania** wartości właściwości w czasie zostaną zastosowane po rozgrzewania okres. Można kontrolować, scenariuszy, do których mają zostać uwzględnione w rozgrzewania przy użyciu **Wyłącz podczas rozgrzewania** właściwości scenariusza.

5. Po zmianie właściwości wybierz **Zapisz** na **pliku** menu. Następnie można uruchomić testu obciążenia za pomocą nowego **opóźnienie uruchamiania** wartość.

## <a name="enable-and-disable-whether-a-scenario-runs-during-the-warm-up-period"></a>Włączanie i wyłączanie czy scenariusz jest uruchamiany w okresie rozgrzewania

**Wyłącz podczas rozgrzewania** właściwości są ustawiane przy użyciu **właściwości** okna. Edytowanie właściwości scenariusza testu obciążenia jest ustawiany przez Edytor testu obciążenia.

 **Wyłącz podczas rozgrzewania** właściwość jest używana w celu wskazania, czy scenariusz powinna działać, albo nie działać w okresie rozgrzewania, który jest określony w **opóźnienie uruchamiania** właściwości. Aby uzyskać więcej informacji, zapoznaj się z poprzedniej procedury [określić opóźnienie uruchomienie scenariusz](#specify-the-delay-start-time-of-a-scenario).

> [!NOTE]
> Aby uzyskać pełną listę właściwości parametrów uruchomieniowych i ich opisów, zobacz [właściwości scenariusza testów obciążenia](../test/load-test-scenario-properties.md).

### <a name="to-enable-or-disable-the-warm-up-period-for-a-scenario"></a>Aby włączyć lub wyłączyć okres rozgrzewania, dotyczy scenariusza

1. Otwórz test obciążenia.

     **Edytora testu obciążenia** pojawia się. Zostanie wyświetlone drzewo testu obciążenia.

2. Obciążenia test drzew **scenariuszy** folderu, wybierz węzeł scenariusza, który chcesz zmienić zachowanie rozgrzewania.

3. Na **widoku** menu, wybierz opcję **okno właściwości**.

     Kategorie i właściwości tego scenariusza są wyświetlane w **właściwości** okna.

     W **Wyłącz podczas rozgrzewania** właściwości, wybierz opcję **True** lub **wartość False.**

4. Po zakończeniu, zmiana wartości właściwości, wybierz **Zapisz** na **pliku** menu. Następnie możesz uruchomić test obciążenia za pomocą nowego **Wyłącz podczas rozgrzewania** wartość.

## <a name="see-also"></a>Zobacz także

- [Edytowanie scenariuszy testu obciążenia](../test/edit-load-test-scenarios.md)
- [Konfigurowanie agentów testowych i kontrolerów testów obciążenia testów](../test/configure-test-agents-and-controllers-for-load-tests.md)
- [Właściwości scenariusza testów obciążenia](../test/load-test-scenario-properties.md)