---
title: Tworzenie wycinków metody badania jednostkowego
ms.date: 04/01/2019
ms.topic: conceptual
helpviewer_keywords:
- unit testing, create unit tests
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3eb001d2022bb57981f21fd99c051c54aeb08301
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75844317"
---
# <a name="create-unit-test-method-stubs-with-the-create-unit-tests-command"></a>Tworzenie wycinków metody badania jednostkowego za pomocą polecenia Utwórz testy jednostkowe

Polecenie **Utwórz testy jednostkowe** tworzy wycinki metody badania jednostkowego. Ta funkcja umożliwia łatwą konfigurację projektu testowego, klasy testu i metody testowej w nim.

::: moniker range="vs-2017"
> [!NOTE]
> Polecenie Menu **Utwórz testy jednostkowe** jest dostępne tylko dla kodu zarządzanego przeznaczonego dla programu .NET Framework (ale nie dla programu .NET Core).
::: moniker-end
::: moniker range=">=vs-2019"
> [!NOTE]
> Polecenie Menu **Utwórz testy jednostkowe** jest dostępne tylko dla kodu zarządzanego.
::: moniker-end

Polecenie Menu **Utwórz testy jednostkowe** jest rozszerzalne i może służyć do generowania testów dla MSTest, MSTest V2, NUnit i xUnit.

## <a name="get-started"></a>Wprowadzenie

Aby rozpocząć, wybierz metodę, typ lub obszar nazw w edytorze kodu w projekcie, który chcesz przetestować, kliknij prawym przyciskiem myszy, a następnie wybierz polecenie **Utwórz testy jednostkowe**. Zostanie otwarte okno dialogowe **Tworzenie testów jednostkowych,** w którym można skonfigurować sposób tworzenia testów.

![Korzystanie z polecenia Utwórz testy jednostkowe](media/createunittestcommand.png)

## <a name="set-unit-test-traits"></a>Ustawianie cech testowych jednostki

Jeśli planujesz uruchomić te testy w ramach procesu automatyzacji testów, można rozważyć utworzenie testu w innym projekcie testowym (druga opcja w oknie dialogowym powyżej) i ustawienie cech testu jednostkowego dla testu jednostkowego. Dzięki temu można łatwiej dołączyć lub wykluczyć te konkretne testy w ramach ciągłej integracji lub ciągłego potoku wdrażania. Cechy są ustawiane przez dodanie metadanych do testu jednostkowego bezpośrednio, jak pokazano poniżej.

![Ustawianie cech testowych jednostki](media/createunittest.png)

## <a name="use-third-party-unit-test-frameworks"></a>Korzystanie z struktur testów jednostkowych innych firm

Aby automatycznie wygenerować testy jednostkowe dla jednostki NUnit lub xUnit, zainstaluj jedno z tych rozszerzeń struktury testów z programu Visual Studio Marketplace:

* [Rozszerzenie NUnit dla generatorów testowych](https://marketplace.visualstudio.com/items?itemName=NUnitDevelopers.TestGeneratorNUnitextension)
* [xUnit.net rozszerzenie generatorów testowych](https://marketplace.visualstudio.com/items?itemName=BradWilson.xUnitnetTestExtensions)

## <a name="when-should-i-use-this-feature"></a>Kiedy należy korzystać z tej funkcji?

Użyj tej funkcji, gdy trzeba utworzyć testy jednostkowe, ale w szczególności podczas testowania istniejącego kodu, który ma niewielki lub żaden zakres testu i bez dokumentacji. Innymi słowy, gdy istnieje ograniczona lub nieistniejąca specyfikacja kodu. Skutecznie implementuje podejście podobne do [inteligentnych testów jednostkowych,](https://devblogs.microsoft.com/devops/introducing-smart-unit-tests/) które charakteryzuje obserwowane zachowanie kodu.

Jednak ta funkcja jest równie stosowana, gdy deweloper rozpoczyna pisanie kodu, a następnie używa go do testów jednostkowych bootstrap. W ramach przepływu kodowania deweloper może chcieć szybko utworzyć skrót metody badania jednostkowego (z odpowiednią klasą testu i odpowiednim projektem testowym) dla określonego fragmentu kodu.

## <a name="see-also"></a>Zobacz też

- [Tworzenie wycinków metody badania jednostkowego za pomocą "Tworzenie testów jednostkowych"](https://devblogs.microsoft.com/devops/creating-unit-test-method-stubs-with-create-unit-tests/)
- [Wpisy w blogu testów jednostkowych](https://devblogs.microsoft.com/devops/?s=unit+testing)
