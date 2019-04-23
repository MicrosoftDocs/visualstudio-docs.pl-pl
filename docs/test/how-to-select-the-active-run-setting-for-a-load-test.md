---
title: Wybieranie ustawienia przebiegu testu obciążeniowego
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, run settings, active
ms.assetid: ed6ff546-acfa-4dd8-b3a2-6e7455930ca4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 12582aa4c1aa41aa0a38f652cf4841ba1f9953e1
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60042029"
---
# <a name="how-to-select-the-active-run-setting-for-a-load-test"></a>Instrukcje: Wybierz aktywne ustawienia uruchamiania dla testu obciążenia

Po utworzeniu testu obciążenia za pomocą **Kreatora nowego testu obciążeniowego**, możesz użyć **edytora testu obciążenia** można zmienić właściwości scenariuszy do spełnienia potrzeb i celów testowania.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Test obciążenia może zawierać jeden lub więcej *parametrów uruchomieniowych* które są zestawem właściwości wpływającym na sposób wykonywania testu obciążeniowego. Ustawienia uruchamiania są zorganizowane według kategorii w **właściwości** okna. Po uruchomieniu testu obciążenia używa uruchomieniowy, który jest aktualnie ustawiona jako aktywna.

> [!NOTE]
> Aby uzyskać pełną listę właściwości parametrów uruchomieniowych i ich opisów, zobacz [właściwości ustawień przebiegu testu obciążenia](../test/load-test-run-settings-properties.md).

Jeśli test obciążeniowy zawiera tylko jeden węzeł ustawień w obszarze **parametrów uruchomieniowych** folderu, w tym węźle jest zawsze aktywny węzeł. Jeśli test obciążeniowy zawiera wiele węzłów parametrów uruchomieniowych, możesz wybrać jeden do użycia podczas uruchamiania testu obciążenia. Zobacz [jak: Dodawanie dodatkowych parametrów uruchomieniowych do testu obciążeniowego](../test/how-to-add-additional-run-settings-to-a-load-test.md).

W **edytora testu obciążenia**, aktywnego ustawienia uruchamiania jest identyfikowane za pomocą sufiksu "[aktywny]".

## <a name="select-the-active-run-setting"></a>Wybierz aktywnego ustawienia uruchamiania

1. Otwórz test obciążenia.

2. Rozwiń **parametrów uruchomieniowych** folderu.

3. Kliknij prawym przyciskiem myszy węzeł parametrów uruchomieniowych, który ma być aktywnym węźle, a następnie kliknij **Ustaw jako aktywny**.

     W **Edito testu obciążenia**r, węzeł dotyczy uruchomieniowy jest aktualizowany wraz z sufiksem "[aktywny]".

     Parametr uruchomieniowy wybrane stanie się aktywny, a pozostaje aktywne, dopóki nie wybierzesz innej uruchomieniowy jako aktywny.

> [!NOTE]
> Można zastąpić Uruchom aktywne ustawienie ustawiając zmienną środowiskową o nazwie `Test.UseRunSetting=<run setting name>`. Jest to przydatne, po uruchomieniu testu obciążenia z wiersza polecenia lub pliku wsadowego. Dzięki temu można określić różne ustawienia uruchamiania bez konieczności otwierania testu obciążenia.

## <a name="specify-the-run-setting-to-use-from-the-command-line"></a>Określenie parametru uruchomieniowego do użycia z poziomu wiersza polecenia

Można zastąpić domyślnych parametrów uruchomieniowych w teście obciążenia, ustawiając zmienną środowiskową z wiersza polecenia:

**Ustaw Test.UseRunSetting=PreProdEnvironment**

I uruchom test:

**mstest /testcontainer:loadtest1.loadtest**

## <a name="see-also"></a>Zobacz także

- [Konfigurowanie ustawień testu obciążenia](../test/configure-load-test-run-settings.md)
- [Określanie zbiorów liczników oraz zasad progu dla komputerów w teście obciążeniowym](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Instrukcje: Dodawanie dodatkowych ustawień przebiegu testu obciążenia](../test/how-to-add-additional-run-settings-to-a-load-test.md)