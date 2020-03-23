---
title: Instalowanie platform testów jednostkowych innych firm
ms.date: 04/01/2019
ms.topic: conceptual
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: b70e26adc7c0c9a8dc409d9b4b971b233418b8e1
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75594282"
---
# <a name="install-unit-test-frameworks"></a>Instalowanie struktur testowych jednostek

Visual Studio Test Explorer można uruchomić testy z dowolnej struktury testów jednostkowych, który opracował interfejs karty dla niego. Instalowanie struktury kopiuje pliki binarne i dodaje szablony projektu programu Visual Studio dla języków, które obsługuje. Podczas tworzenia projektu z szablonem, struktura jest zarejestrowana w Eksploratorze testów.

Rozwiązanie programu Visual Studio może zawierać projekty testów jednostkowych, które używają różnych struktur i które są przeznaczone dla różnych języków.

[MSTest](getting-started-with-unit-testing.md) jest platformą testową dostarczoną przez program Visual Studio i jest instalowana domyślnie.

## <a name="acquire-frameworks"></a>Nabywanie struktur

Zainstaluj struktury testów jednostkowych innych firm przy użyciu **Menedżera pakietów NuGet**.

1. Kliknij prawym przyciskiem myszy projekt, który będzie zawierał kod testu i wybierz pozycję **Zarządzaj pakietami NuGet**.

2. W **Menedżerze pakietów NuGet**wyszukaj strukturę testów, którą chcesz zainstalować, a następnie kliknij przycisk **Zainstaluj**.

   ![Menedżer pakietów NuGet w programie Visual Studio](media/vs-2019/nuget-package-manager.png)

## <a name="update-to-the-latest-test-adapters"></a>Aktualizacja do najnowszych kart testowych

Aktualizacja do najnowszej stabilnej karty testowej, aby uzyskać lepsze wykrywanie i wykonywanie testów. Aby uzyskać więcej informacji na temat aktualizacji kart testowych MSTest, NUnit i xUnit, zobacz [blog programu Visual Studio](https://devblogs.microsoft.com/visualstudio/test-experience-improvements/).

### <a name="to-update-to-the-latest-stable-test-adapter-version"></a>Aby zaktualizować do najnowszej stabilnej wersji karty testowej

1. Otwórz Menedżera pakietów Nuget dla rozwiązania, przechodząc do Menedżera**pakietów** >  **Narzędzia** > NuGet Manage**NuGet Packages for Solution**.

2. Kliknij kartę **Aktualizacje** i wyszukaj karty testowe MSTest, NUnit lub xUnit, które są zainstalowane.

3. Wybierz każdą kartę testową, a następnie wybierz najnowszą stabilną wersję w menu rozwijanym.

4. Wybierz przycisk **Zainstaluj.**

   ![Adapter testu uaktualnienia](media/install-adapter-upgrade.png)

## <a name="see-also"></a>Zobacz też

- [Jednostka przetestować swój kod](../test/unit-test-your-code.md)
