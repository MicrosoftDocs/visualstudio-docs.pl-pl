---
title: Testy jednostkowe kodu w języku Python
description: Konfigurowanie testów jednostkowych dla kodu w języku Python w programie Visual Studio ma pełne wykorzystanie funkcji Eksploratora testów, aby odkryć, uruchamiania i debugowania testów.
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
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "71254197"
---
# <a name="set-up-unit-testing-for-python-code"></a>Konfigurowanie testów jednostkowych dla kodu w języku Python

Testy jednostkowe są fragmenty kodu, które testują inne jednostki kodu w aplikacji, zwykle izolowane funkcje, klasy i tak dalej. Gdy aplikacja przekazuje wszystkich testów jednostkowych, mogą co najmniej ufać, że jego niskiego poziomu funkcjonalności jest poprawna.

Python często używa testów jednostkowych do weryfikacji scenariuszy podczas projektowania programu. Obsługa języka Python w programie Visual Studio zawiera odnajdywanie, wykonywanie i debugowanie testów jednostkowych w kontekście swojego procesu programistycznego, bez konieczności uruchomić testy oddzielnie.

Ten artykuł zawiera krótkie konspektu testów jednostkowych funkcji w programie Visual Studio za pomocą języka Python. Aby uzyskać więcej informacji na ogół testów jednostkowych, zobacz [kodu testu jednostkowego](../test/unit-test-your-code.md).

::: moniker range="vs-2017"

[!include[Testing Python code](includes/vs-2017/unit-testing-python.md)]

::: moniker-end

::: moniker range=">= vs-2019"

[!include[Testing Python code](includes/vs-2019/unit-testing-python.md)]

::: moniker-end