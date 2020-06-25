---
title: Uruchamianie testu jednostkowego jako procesu 64-bitowego
ms.date: 03/10/2020
ms.topic: how-to
helpviewer_keywords:
- unit tests, creating
- unit tests, running
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 04895e3dd72a7cb4f0373c970db0f12582506ef9
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85285559"
---
# <a name="run-a-unit-test-as-a-64-bit-process"></a>Uruchamianie testu jednostkowego jako procesu 64-bitowego

Jeśli masz maszynę 64-bitową, możesz uruchomić testy jednostkowe i przechwycić informacje o pokryciu kodu jako proces 64-bitowy.

## <a name="to-run-a-unit-test-as-a-64-bit-process"></a>Aby uruchomić test jednostkowy jako proces 64-bitowy

1. Jeśli kod lub testy zostały skompilowane jako 32-bitowe/x86, ale teraz chcesz je uruchomić jako proces 64-bitowy, skompiluj je ponownie jako **dowolny procesor**.

   ::: moniker range="vs-2017"
   Alternatywnie, w programie Visual Studio 2017, można także skompilować projekt jako **64-bitowy**.
   ::: moniker-end

    > [!TIP]
    > Aby zapewnić maksymalną elastyczność, skompiluj projekty testowe z dowolną konfiguracją **procesora CPU** . Następnie można uruchomić zarówno na 32-bitowym, jak i 64-bitowym agencie. Nie ma możliwości kompilowania projektów testowych z konfiguracją **64-bitową** .

2. Ustaw testy jednostkowe do uruchomienia jako proces 64-bitowy.

   ::: moniker range=">=vs-2019"
   Z menu programu Visual Studio wybierz polecenie **test**, a następnie wybierz pozycję **architektura procesora dla projektów AnyCPU**. Wybierz pozycję **x64** , aby uruchomić testy jako proces 64-bitowy.
   ::: moniker-end
   ::: moniker range="vs-2017"
   Z menu programu Visual Studio wybierz polecenie **test**, a następnie wybierz pozycję **Ustawienia testu**, a następnie wybierz pozycję **architektura procesora**. Wybierz pozycję **x64** , aby uruchomić testy jako proces 64-bitowy.
   ::: moniker-end

   \-oraz

   Określ `<TargetPlatform>x64</TargetPlatform>` w pliku *. runsettings* . Zaletą tej metody jest to, że można określić grupy ustawień w różnych plikach i szybko przełączać się między różnymi ustawieniami. Możesz również kopiować ustawienia między rozwiązaniami. Aby uzyskać więcej informacji, zobacz [Konfigurowanie testów jednostkowych przy użyciu pliku. runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).

## <a name="see-also"></a>Zobacz też

- [Przeprowadzanie testów jednostkowych za pomocą narzędzia Eksplorator testów](../test/run-unit-tests-with-test-explorer.md)
- [Testowanie jednostkowe kodu](../test/unit-test-your-code.md)
