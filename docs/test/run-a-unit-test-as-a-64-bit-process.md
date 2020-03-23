---
title: Uruchamianie testu jednostkowego jako procesu 64-bitowego
ms.date: 03/10/2020
ms.topic: conceptual
helpviewer_keywords:
- unit tests, creating
- unit tests, running
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: d6c6839f8c4702d88d1022116231c6f22b5dbf21
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79093917"
---
# <a name="run-a-unit-test-as-a-64-bit-process"></a>Uruchamianie testu jednostkowego jako procesu 64-bitowego

Jeśli masz komputer 64-bitowy, możesz uruchomić testy jednostkowe i przechwycić informacje o pokryciu kodu jako proces 64-bitowy.

## <a name="to-run-a-unit-test-as-a-64-bit-process"></a>Aby uruchomić test jednostkowy jako proces 64-bitowy

1. Jeśli kod lub testy zostały skompilowane jako 32-bitowe/x86, ale teraz chcesz uruchomić je jako proces 64-bitowy, ponownie skompiluj je jako **dowolny procesor**.

   ::: moniker range="vs-2017"
   Alternatywnie w programie Visual Studio 2017 można również skompilować projekt jako **64-bitowy.**
   ::: moniker-end

    > [!TIP]
    > Aby uzyskać maksymalną elastyczność, skompiluj projekty testowe za pomocą dowolnej konfiguracji **procesora CPU.** Następnie można uruchomić zarówno na agentach 32-bitowych, jak i 64-bitowych. Nie ma żadnych korzyści do kompilacji projektów testowych z konfiguracją **64-bitową.**

2. Ustaw testy jednostkowe tak, aby działały jako proces 64-bitowy.

   ::: moniker range=">=vs-2019"
   Z menu Visual Studio wybierz polecenie **Testuj**, a następnie wybierz polecenie **Architektura procesora dla projektów AnyCPU**. Wybierz **x64,** aby uruchomić testy jako proces 64-bitowy.
   ::: moniker-end
   ::: moniker range="vs-2017"
   Z menu Visual Studio wybierz polecenie **Testuj**, a następnie wybierz polecenie **Ustawienia testu**, a następnie wybierz polecenie **Architektura procesora**. Wybierz **x64,** aby uruchomić testy jako proces 64-bitowy.
   ::: moniker-end

   \-lub -

   Określ `<TargetPlatform>x64</TargetPlatform>` w pliku *runsettings.* Zaletą tej metody jest to, że można określić grupy ustawień w różnych plikach i szybko przełączać się między różnymi ustawieniami. Można również kopiować ustawienia między rozwiązaniami. Aby uzyskać więcej informacji, zobacz [Konfigurowanie testów jednostkowych przy użyciu pliku runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).

## <a name="see-also"></a>Zobacz też

- [Przeprowadzanie testów jednostkowych za pomocą narzędzia Eksplorator testów](../test/run-unit-tests-with-test-explorer.md)
- [Jednostka przetestować swój kod](../test/unit-test-your-code.md)
