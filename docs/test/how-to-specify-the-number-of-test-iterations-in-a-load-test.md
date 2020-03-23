---
title: Określ liczbę iteracji testowych w ustawieniu przebiegu testu obciążenia
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, properties
- load tests, run settings
ms.assetid: 45a625db-b3e7-4d64-beda-b9a76248096d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 446da348c1a947e6c59b8ad60d9bd0799d0d4322
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75588944"
---
# <a name="how-to-specify-the-number-of-test-iterations-in-a-load-test-run-setting"></a>Jak: Określ liczbę iteracji testowych w ustawieniu przebiegu testu obciążenia

Po utworzeniu testu obciążenia za pomocą **Kreatora nowego testu obciążenia**można użyć **Edytora testów obciążenia,** aby zmienić właściwości scenariuszy, aby spełnić twoje potrzeby i cele testowania. Aby uzyskać więcej informacji, zobacz [Instruktaż: Tworzenie i uruchamianie testu obciążenia](../test/walkthrough-create-and-run-a-load-test.md).

Za pomocą **Edytora testów obciążenia**można edytować właściwość **Test Iterations** wartości ustawień uruchomienia w oknie **Właściwości.** Właściwość **Test Iterations** określa liczbę iteracji do uruchomienia na wszystkich testach wydajności sieci web i jednostkowych we wszystkich scenariuszach w teście obciążenia przy użyciu **Edytora testów obciążenia**.

> [!NOTE]
> Aby uzyskać pełną listę właściwości ustawień uruchamiania i ich opisy, zobacz [Właściwości ustawień przebiegu testu ładowania](../test/load-test-run-settings-properties.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-specify-the-number-of-test-iterations-in-a-run-setting"></a>Aby określić liczbę iteracji testowych w ustawieniu uruchamiania

1. Otwórz test obciążenia.

     Zostanie wyświetlony **edytor testów obciążenia** i wyświetli drzewo testu obciążenia.

2. W drzewie testu obciążenia w folderze **Uruchom ustawienia** wybierz ustawienie uruchamiania.

3. W menu **Widok** wybierz **okno Właściwości,** aby wyświetlić kategorie i właściwości ustawienia uruchamiania obciążenia.

4. Ustaw **właściwość Użyj iteracji testowych** na **True**.

5. We właściwości **Test Iterations** wprowadź liczbę, która wskazuje liczbę iteracji testowych do uruchomienia podczas testu obciążenia.

6. Po zakończeniu zmiany właściwości wybierz polecenie **Zapisz** w menu **Plik.** Następnie można uruchomić test obciążenia przy użyciu nowej wartości **iteracji testowych.**

## <a name="see-also"></a>Zobacz też

- [Konfigurowanie ustawień przebiegu testu obciążenia](../test/configure-load-test-run-settings.md)
- [Właściwości scenariusza testu obciążenia](../test/load-test-scenario-properties.md)
