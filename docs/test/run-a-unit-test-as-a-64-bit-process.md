---
title: Uruchamianie testu jednostkowego jako procesu 64-bitowego
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- unit tests, creating
- unit tests, running
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 4ee070adba33328253d7abeb122ec2ca2da145ef
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53062719"
---
# <a name="run-a-unit-test-as-a-64-bit-process"></a>Uruchamianie testu jednostkowego jako procesu 64-bitowego

W przypadku komputera 64-bitowego, można uruchomić testy jednostkowe i przechwytywanie informacji o pokryciu kodu jako procesu 64-bitowego.

## <a name="to-run-a-unit-test-as-a-64-bit-process"></a>Do uruchomienia testu jednostkowego jako procesu 64-bitowego

1. Jeśli kodu lub testy zostały skompilowane dla architektury 32-bitowy/x86, ale chcesz uruchamiać je jako procesu 64-bitowego, należy ponownie skompilować je jako **dowolny Procesor**, lub opcjonalnie **64-bitowych**.

    > [!TIP]
    > Aby zapewnić maksymalną elastyczność, należy skompilować testowane projekty z **dowolny Procesor** konfiguracji. Następnie można uruchomić zarówno 32-bitowych i 64-bitowych agentów. Nie posiada zalet kompilowanie projektów testowych mających **64-bitowych** konfiguracji.

2. Wybierz z menu programu Visual Studio **testu**, następnie wybierz **ustawienia**, a następnie wybierz **architektury procesora**. Wybierz **x64** do uruchamiania testów jako procesu 64-bitowego.

   - lub —

   Określ `<TargetPlatform>x64</TargetPlatform>` w *.runsettings* pliku. Zaletą tej metody jest, że można określić grupy ustawień w różnych plikach i szybkie przełączanie się między różnymi ustawieniami. Ponadto można kopiować ustawienia między rozwiązaniami. Aby uzyskać więcej informacji, zobacz [Konfigurowanie testów jednostkowych przy użyciu pliku runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).

## <a name="see-also"></a>Zobacz także

- [Przeprowadzanie testów jednostkowych za pomocą narzędzia Eksplorator testów](../test/run-unit-tests-with-test-explorer.md)
- [Kod testu jednostkowego](../test/unit-test-your-code.md)
