---
title: Ustawianie ustawień przebiegu testu obciążenia z wiersza polecenia
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, command line
- load tests, run settings, selecting
ms.assetid: 175d1d58-f09a-4449-b132-a29a394a7c8e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 760cf18062e607e9f9039c6cc5f4adf409134cb5
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75588996"
---
# <a name="how-to-select-a-load-test-run-setting-to-use-from-the-command-line"></a>Jak: Wybierz ustawienie przebiegu testu obciążenia, którego chcesz użyć z wiersza polecenia

Test obciążenia może zawierać *ustawienia uruchamiania,* które są właściwościami wpływającymi na sposób wykonywania testu obciążenia. Ustawienia uruchamiania są uporządkowane według kategorii w oknie **Właściwości.** Po uruchomieniu testu obciążenia używa ustawienia uruchom, który jest obecnie ustawiony jako aktywny.

Jeśli test obciążenia zawiera tylko jedno ustawienie uruchamiania, jest to zawsze aktywny węzeł. Jeśli test obciążenia zawiera wiele węzłów ustawień uruchamiania, można wybrać ten, który ma być używany po uruchomieniu testu obciążenia z wiersza polecenia. Zobacz [Jak: Dodawanie dodatkowych ustawień uruchamiania do testu obciążenia](../test/how-to-add-additional-run-settings-to-a-load-test.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-change-the-run-setting-from-the-command-line"></a>Aby zmienić ustawienie uruchamiania z wiersza polecenia

1. Jeśli chcesz użyć różnych ustawień uruchamiania z wiersza polecenia, aby skorzystać ze strategii parametrów kontekstu, użyj następującego polecenia:

    `Set Test.UseRunSetting= CorporateStagingWebServer`

2. Uruchom test obciążenia przy użyciu mstest:

    `mstest /testcontainer:loadtest1.loadtest`

## <a name="see-also"></a>Zobacz też

- [Konfigurowanie ustawień przebiegu testu obciążenia](../test/configure-load-test-run-settings.md)
- [Określanie zestawów liczników i reguł progowych dla komputerów w teście obciążenia](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Jak: Dodawanie dodatkowych ustawień uruchamiania do testu obciążenia](../test/how-to-add-additional-run-settings-to-a-load-test.md)
- [Jak: Wybierz ustawienie aktywnego uruchamiania dla testu obciążenia](../test/how-to-select-the-active-run-setting-for-a-load-test.md)
