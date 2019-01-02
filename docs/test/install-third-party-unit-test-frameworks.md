---
title: Instalowanie platform testów jednostkowych innych firm
ms.date: 06/07/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: f8cdfa96e41e72531cb3f2cdc164af4ed57546e5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53955243"
---
# <a name="install-unit-test-frameworks"></a>Instalowanie platform testów jednostkowych

Visual Studio Test Explorer można uruchamiać dowolną jednostkę struktury testowej, która opracowała interfejs adapter dla Eksploratora. Program instalacyjny Framework instaluje pliki binarne i dodaje szablony projektu Visual Studio dla obsługiwanych języków. Podczas tworzenia projektu z szablonem, struktura jest zarejestrowany w Eksploratorze testów. Rozwiązania programu Visual Studio może zawierać projektów testów jednostkowych, które korzystają z różnych platform i które są przeznaczone dla różnych języków. Eksplorator testów wykonuje na nich wszystkich.

[MSTest](getting-started-with-unit-testing.md) to struktura testów, dostarczane przez program Visual Studio i jest domyślnie instalowany z programem Visual Studio.

## <a name="acquire-frameworks"></a>Uzyskiwanie struktur

Możesz pobrać i zainstalować platform testów jednostkowych innych firm, korzystając z Menedżera rozszerzeń programu Visual Studio lub [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs). Można również pobrać struktur w innych witrynach, takich jak witryny sieci Web Framework.

### <a name="install-from-visual-studio"></a>Instalowanie za pomocą programu Visual Studio

1. Wybierz **narzędzia** w menu standardowym, a następnie wybierz **rozszerzenia i aktualizacje**.

2. Rozwiń **Online** > **programu Visual Studio Marketplace** > **narzędzia**. Wybierz **testowania**.

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

Aktualizacja najnowszych adaptera testowego stabilny, aby lepiej testów odkrywania i wykonywania. Aby uzyskać więcej informacji o aktualizacjach MSTest i NUnit, xUnit adapterów testowych, zobacz [blog Visual Studio](https://blogs.msdn.microsoft.com/visualstudio/2017/11/16/test-experience-improvements/).

### <a name="to-update-to-the-latest-stable-test-adapter-version"></a>Aby zaktualizować do wersji karty najnowszy stabilny testu

1. Otwórz Menedżera pakietów Nuget dla rozwiązania, przechodząc do **narzędzia** > **Menedżera pakietów NuGet** > **Zarządzaj pakietami NuGet dla rozwiązania**.

2. Kliknij pozycję **aktualizacje** kartę i wyszukaj xUnit, MSTest i NUnit testu kart, które są zainstalowane.

3. Wybierz kartę każdego testu, a następnie wybierz najnowszą stabilną wersję, w menu rozwijanym.

4. Wybierz **zainstalować** przycisku.

   ![Uaktualnianie adaptera testowego](media/install-adapter-upgrade.png)

## <a name="see-also"></a>Zobacz także

- [Kod testu jednostkowego](../test/unit-test-your-code.md)
