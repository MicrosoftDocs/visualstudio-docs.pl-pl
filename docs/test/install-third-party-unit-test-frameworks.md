---
title: Instalowanie platform testów jednostkowych innych firm
ms.date: 04/01/2019
ms.topic: conceptual
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 9f61b52f72474a8ecd8fac4c30265dcd7cf36a5e
ms.sourcegitcommit: 509fc3a324b7748f96a072d0023572f8a645bffc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58857705"
---
# <a name="install-unit-test-frameworks"></a>Instalowanie platform testów jednostkowych

Visual Studio Test Explorer można uruchomić testy przy użyciu dowolnej jednostki struktury testowej, która opracowała interfejs karta dla niego. Instalowanie programu framework kopiuje pliki binarne i dodaje szablony projektu Visual Studio dla obsługiwanych języków. Podczas tworzenia projektu z szablonem, struktura jest zarejestrowany w Eksploratorze testów.

Rozwiązania programu Visual Studio może zawierać projektów testów jednostkowych, które korzystają z różnych platform i które są przeznaczone dla różnych języków.

[MSTest](getting-started-with-unit-testing.md) to struktura testów, dostarczane przez program Visual Studio i jest instalowany domyślnie.

## <a name="acquire-frameworks"></a>Uzyskiwanie struktur

Instalowanie platform testów jednostkowych innych firm przy użyciu **Menedżera pakietów NuGet**.

1. Kliknij prawym przyciskiem myszy na projekt, który będzie zawierać kod testu, a następnie wybrać **Zarządzaj pakietami NuGet**.

2. W **Menedżera pakietów NuGet**, wyszukaj struktury testowej chcesz zainstalować, a następnie kliknij przycisk **zainstalować**.

   ![Menedżer pakietów NuGet w programie Visual Studio](media/vs-2019/nuget-package-manager.png)

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
