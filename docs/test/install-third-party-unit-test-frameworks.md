---
title: Instalowanie platform testów jednostkowych innych firm
ms.date: 06/07/2018
ms.topic: conceptual
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: bf56749ccf49755fa66d44a3ab535d0b3e7611ce
ms.sourcegitcommit: 4ffb7be5384ad566ce46538032bf8561754c61a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2019
ms.locfileid: "57982925"
---
# <a name="install-unit-test-frameworks"></a>Instalowanie platform testów jednostkowych

Visual Studio Test Explorer można uruchamiać dowolną jednostkę struktury testowej, która opracowała interfejs adapter dla Eksploratora. Program instalacyjny Framework instaluje pliki binarne i dodaje szablony projektu Visual Studio dla obsługiwanych języków. Podczas tworzenia projektu z szablonem, struktura jest zarejestrowany w Eksploratorze testów. Rozwiązania programu Visual Studio może zawierać projektów testów jednostkowych, które korzystają z różnych platform i które są przeznaczone dla różnych języków. Eksplorator testów wykonuje na nich wszystkich.

[MSTest](getting-started-with-unit-testing.md) to struktura testów, dostarczane przez program Visual Studio i jest domyślnie instalowany z programem Visual Studio.

## <a name="acquire-frameworks"></a>Uzyskiwanie struktur

Możesz pobrać i zainstalować platform testów jednostkowych innych firm, korzystając z Menedżera rozszerzeń programu Visual Studio lub [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs). Można również pobrać struktur w innych witrynach, takich jak witryny sieci Web Framework.

### <a name="install-from-visual-studio"></a>Instalowanie za pomocą programu Visual Studio

::: moniker range="vs-2017"

1. Wybierz **narzędzia** > **rozszerzenia i aktualizacje**.

::: moniker-end

::: moniker range=">=vs-2019"

1. Wybierz **rozszerzenia** > **Zarządzaj rozszerzeniami**.

::: moniker-end

2. Rozwiń **Online** > **Visual Studio Marketplace** > **narzędzia**, a następnie wybierz **testowania**.

3. Przeszukaj listę, aby znaleźć platformę.

4. Wybierz platformę i wybierz pozycję **Pobierz**.

Aby uzyskać więcej informacji, zobacz [wyszukiwanie i korzystanie z rozszerzenia programu Visual Studio](../ide/finding-and-using-visual-studio-extensions.md).

### <a name="install-from-the-web"></a>Instalowanie z sieci web

Jeśli znasz framework, który Cię interesuje:

1. Otwórz [witryny Marketplace programu Visual Studio](https://marketplace.visualstudio.com/vs).

2. Wpisz nazwę platformy w **znaleźć** pole.

3. Wybierz platformę, na liście wyników, aby przejść do **Visual Studio Marketplace** strony dla narzędzia.

Aby przeglądać listę struktury oraz inne narzędzia do testowania:

1. Otwórz [witryny Marketplace programu Visual Studio](https://marketplace.visualstudio.com/vs).

2. W **Filtruj według kategorii / kolekcji**, wybierz **holograficznych**.

3. W **kategorii** listy (oznaczone jako **przedstawiający**), rozwiń węzeł **narzędzia** węzeł, a następnie wybierz **testowania**.

4. Wybieranie platformy na liście wyników, aby przejść do **Visual Studio Marketplace** strony dla narzędzia.

## <a name="update-to-the-latest-test-adapters"></a>Zaktualizuj do najnowszej adaptery testowe

Aktualizacja najnowszych adaptera testowego stabilny, aby lepiej testów odkrywania i wykonywania. Aby uzyskać więcej informacji o aktualizacjach MSTest i NUnit, xUnit adapterów testowych, zobacz [blog Visual Studio](https://devblogs.microsoft.com/visualstudio/test-experience-improvements/).

### <a name="to-update-to-the-latest-stable-test-adapter-version"></a>Aby zaktualizować do wersji karty najnowszy stabilny testu

1. Otwórz Menedżera pakietów Nuget dla rozwiązania, przechodząc do **narzędzia** > **Menedżera pakietów NuGet** > **Zarządzaj pakietami NuGet dla rozwiązania**.

2. Kliknij pozycję **aktualizacje** kartę i wyszukaj xUnit, MSTest i NUnit testu kart, które są zainstalowane.

3. Wybierz kartę każdego testu, a następnie wybierz najnowszą stabilną wersję, w menu rozwijanym.

4. Wybierz **zainstalować** przycisku.

   ![Uaktualnianie adaptera testowego](media/install-adapter-upgrade.png)

## <a name="see-also"></a>Zobacz także

- [Kod testu jednostkowego](../test/unit-test-your-code.md)
