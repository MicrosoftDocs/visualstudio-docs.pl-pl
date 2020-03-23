---
title: Wybierz ustawienie uruchamiania dla testu obciążenia
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, run settings, active
ms.assetid: ed6ff546-acfa-4dd8-b3a2-6e7455930ca4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 91ac811c1f55fdb9a662db679ebd2d038ecdd5dd
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75588983"
---
# <a name="how-to-select-the-active-run-setting-for-a-load-test"></a>Jak: Wybierz ustawienie aktywnego uruchamiania dla testu obciążenia

Po utworzeniu testu obciążenia za pomocą **Kreatora nowego testu obciążenia**można użyć **Edytora testów obciążenia,** aby zmienić właściwości scenariuszy, aby spełnić twoje potrzeby i cele testowania.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Test obciążenia może zawierać co najmniej jedno *ustawienie uruchamiania,* które są zestawem właściwości, które wpływają na sposób uruchamiania testu obciążenia. Ustawienia uruchamiania są uporządkowane według kategorii w oknie **Właściwości.** Po uruchomieniu testu obciążenia używa ustawienia uruchom, który jest obecnie ustawiony jako aktywny.

> [!NOTE]
> Aby uzyskać pełną listę właściwości ustawień uruchamiania i ich opisy, zobacz [Właściwości ustawień przebiegu testu ładowania](../test/load-test-run-settings-properties.md).

Jeśli test obciążenia zawiera tylko jeden węzeł ustawień uruchamiania w folderze **Uruchom ustawienia,** ten węzeł jest zawsze aktywnym węzłem. Jeśli test obciążenia zawiera wiele węzłów ustawień uruchamiania, można wybrać ten, który ma być używany po uruchomieniu testu obciążenia. Zobacz [Jak: Dodawanie dodatkowych ustawień uruchamiania do testu obciążenia](../test/how-to-add-additional-run-settings-to-a-load-test.md).

W **Edytorze testów obciążenia**aktywne ustawienie uruchamiania jest identyfikowane przez sufiks "[Aktywny]".

## <a name="select-the-active-run-setting"></a>Wybierz aktywne ustawienie uruchamiania

1. Otwórz test obciążenia.

2. Rozwiń folder **Uruchom ustawienia.**

3. Kliknij prawym przyciskiem myszy węzeł ustawień uruchamiania, który ma być aktywnym węzłem, a następnie wybierz polecenie **Ustaw jako aktywny**.

     W **teście obciążenia Edito**r węzeł ustawień przebiegu, którego dotyczy problem, jest aktualizowany za pomocą sufiksu "[Aktywny]".

     Wybrane ustawienie uruchamiania staje się aktywne i pozostaje aktywne, dopóki nie wybierzesz innego ustawienia uruchamiania, które ma być aktywne.

> [!NOTE]
> Aktywne ustawienie uruchamiania można zastąpić, ustawiając `Test.UseRunSetting=<run setting name>`zmienną środowiskową o nazwie . Jest to przydatne po uruchomieniu testu obciążenia z wiersza polecenia lub pliku wsadowego. Dzięki temu można wybrać różne ustawienia uruchamiania bez otwierania testu obciążenia.

## <a name="specify-the-run-setting-to-use-from-the-command-line"></a>Określanie ustawienia uruchamiania używanego z wiersza polecenia

Domyślne ustawienia uruchamiania w teście obciążenia można zastąpić, ustawiając zmienną środowiskową z wiersza polecenia:

**Ustaw test.UseRunSetting=PreProdEnvironment**

I uruchomić test:

**mstest /testcontainer:loadtest1.loadtest**

## <a name="see-also"></a>Zobacz też

- [Konfigurowanie ustawień przebiegu testu obciążenia](../test/configure-load-test-run-settings.md)
- [Określanie zestawów liczników i reguł progowych dla komputerów w teście obciążenia](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Jak: Dodawanie dodatkowych ustawień uruchamiania do testu obciążenia](../test/how-to-add-additional-run-settings-to-a-load-test.md)
