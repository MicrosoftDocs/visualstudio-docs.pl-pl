---
title: Kod Pythona testu jednostkowego
description: Konfigurowanie testowania jednostkowego dla kodu języka Python w programie Visual Studio w pełni wykorzystuje funkcje Eksploratora testów do odnajdowania, uruchamiania i debugowania testów.
ms.date: 09/18/2019
ms.topic: include
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 09c67ace9db36cb8ee3d94296d339b62849e3c94
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "71254197"
---
# <a name="set-up-unit-testing-for-python-code"></a>Konfigurowanie testowania jednostkowego dla kodu języka Python

Testy jednostkowe są części kodu, które testują inne jednostki kodu w aplikacji, zazwyczaj izolowane funkcje, klasy i tak dalej. Gdy aplikacja pomyślniech testów jednostkowych, można przynajmniej ufać, że jego funkcje niskiego poziomu jest poprawna.

Python intensywnie używa testów jednostkowych do sprawdzania poprawności scenariuszy podczas projektowania programu. Obsługa języka Python w programie Visual Studio obejmuje odnajdowanie, wykonywanie i debugowanie testów jednostkowych w kontekście procesu tworzenia, bez konieczności uruchamiania testów oddzielnie.

Ten artykuł zawiera krótki zarys możliwości testowania jednostkowego w programie Visual Studio w języku Python. Aby uzyskać więcej informacji na temat testowania jednostkowego w ogóle, zobacz [Jednostka przetestować kod](../test/unit-test-your-code.md).

::: moniker range="vs-2017"

[!include[Testing Python code](includes/vs-2017/unit-testing-python.md)]

::: moniker-end

::: moniker range=">= vs-2019"

[!include[Testing Python code](includes/vs-2019/unit-testing-python.md)]

::: moniker-end