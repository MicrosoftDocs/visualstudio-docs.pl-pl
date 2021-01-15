---
title: Instalowanie platform testów jednostkowych innych firm
description: Program Visual Studio Test Explorer może uruchamiać testy z dowolnego środowiska testów jednostkowych, które opracowało interfejs adaptera.
ms.custom: SEO-VS-2020
ms.date: 07/09/2020
ms.topic: how-to
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 9a5fbd9f396dfe0ed92c0590712f9fddb84c27a0
ms.sourcegitcommit: 993fca11dc373a10150751bc2a045a9701a9db2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/15/2021
ms.locfileid: "98240312"
---
# <a name="install-unit-test-frameworks"></a>Zainstaluj platformy testów jednostkowych

Program Visual Studio Test Explorer może uruchamiać testy z dowolnego środowiska testów jednostkowych, które opracowało interfejs adaptera. Zainstalowanie struktury kopiuje pliki binarne i dodaje szablony projektów programu Visual Studio dla obsługiwanych języków. Podczas tworzenia projektu z szablonem, struktura jest zarejestrowana w Eksploratorze testów.

Rozwiązanie programu Visual Studio może zawierać projekty testów jednostkowych, które korzystają z różnych platform i które są przeznaczone dla różnych języków.

::: moniker range=">=vs-2019"
W przypadku platformy .NET, [MSTest, nunit i xUnit](getting-started-with-unit-testing.md) są to platformy testowe zapewniane przez program Visual Studio, które są instalowane domyślnie. Dla języka C++ są udostępniane różne zestawy środowisk testowych, takie jak narzędzia ctest.
::: moniker-end
::: moniker range="vs-2017"
[MSTest](getting-started-with-unit-testing.md) to Platforma testowa dostępna w programie Visual Studio, która jest instalowana domyślnie.
::: moniker-end

## <a name="acquire-frameworks"></a>Platformy pozyskiwania

Zainstaluj platformy testów jednostkowych innych firm przy użyciu **Menedżera pakietów NuGet**.

1. Kliknij prawym przyciskiem myszy projekt, który będzie zawierać kod testu, i wybierz pozycję **Zarządzaj pakietami NuGet**.

2. W **Menedżerze pakietów NuGet** Wyszukaj strukturę testową, którą chcesz zainstalować, a następnie kliknij przycisk **Zainstaluj**.

   ![Menedżer pakietów NuGet w programie Visual Studio](media/vs-2019/nuget-package-manager.png)

## <a name="update-to-the-latest-test-adapters"></a>Aktualizacja do najnowszych kart testowych

Zaktualizuj do najnowszej stabilnej karty testowej, aby ułatwić lepsze odnajdywanie i wykonywanie testów. Aby uzyskać więcej informacji o aktualizacjach MSTest, NUnit i xUnit adapterów testowych, zobacz [Blog programu Visual Studio](https://devblogs.microsoft.com/visualstudio/test-experience-improvements/).

### <a name="to-update-to-the-latest-stable-test-adapter-version"></a>Aby zaktualizować do najnowszej stabilnej wersji karty testowej

1. Otwórz Menedżera pakietów NuGet dla swojego rozwiązania, przechodząc do **Narzędzia**  >  **Menedżer pakietów** NuGet zarządzanie pakietami  >  **NuGet dla rozwiązania**.

2. Kliknij kartę **aktualizacje** i Wyszukaj zainstalowane karty testowe MSTest, nunit lub xUnit.

3. Wybierz każdą kartę testową, a następnie wybierz najnowszą stabilną wersję z menu rozwijanego.

4. Wybierz przycisk **Instaluj** .

   ![Adapter testu uaktualnienia](media/install-adapter-upgrade.png)

## <a name="see-also"></a>Zobacz także

- [Testowanie jednostkowe kodu](../test/unit-test-your-code.md)
