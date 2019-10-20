---
title: Uruchamianie testu jednostkowego jako procesu 64-bitowego
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- unit tests, creating
- unit tests, running
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
author: jillre
ms.openlocfilehash: 3971fe0513c98cb957d8013cdad932aa0c04bed1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646624"
---
# <a name="run-a-unit-test-as-a-64-bit-process"></a>Uruchamianie testu jednostkowego jako procesu 64-bitowego

Jeśli masz maszynę 64-bitową, możesz uruchomić testy jednostkowe i przechwycić informacje o pokryciu kodu jako proces 64-bitowy.

## <a name="to-run-a-unit-test-as-a-64-bit-process"></a>Aby uruchomić test jednostkowy jako proces 64-bitowy

1. Jeśli kod lub testy zostały skompilowane jako 32-bitowe/x86, ale teraz chcesz je uruchomić jako proces 64-bitowy, skompiluj je ponownie jako **dowolny procesor CPU**lub opcjonalnie jako **64-bitowy**.

    > [!TIP]
    > Aby zapewnić maksymalną elastyczność, skompiluj projekty testowe z dowolną konfiguracją **procesora CPU** . Następnie można uruchomić zarówno na 32-bitowym, jak i 64-bitowym agencie. Nie ma możliwości kompilowania projektów testowych z konfiguracją **64-bitową** .

2. Z menu programu Visual Studio wybierz polecenie **test**, a następnie wybierz pozycję **Ustawienia**, a następnie wybierz pozycję **architektura procesora**. Wybierz pozycję **x64** , aby uruchomić testy jako proces 64-bitowy.

   - oraz

   Określ `<TargetPlatform>x64</TargetPlatform>` w pliku *. runsettings* . Zaletą tej metody jest to, że można określić grupy ustawień w różnych plikach i szybko przełączać się między różnymi ustawieniami. Możesz również kopiować ustawienia między rozwiązaniami. Aby uzyskać więcej informacji, zobacz [Konfigurowanie testów jednostkowych przy użyciu pliku. runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).

## <a name="see-also"></a>Zobacz także

- [Przeprowadzanie testów jednostkowych za pomocą narzędzia Eksplorator testów](../test/run-unit-tests-with-test-explorer.md)
- [Testowanie jednostkowe kodu](../test/unit-test-your-code.md)
