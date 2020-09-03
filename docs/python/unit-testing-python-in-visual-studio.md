---
title: Kod języka Python testów jednostkowych
description: Skonfigurowanie testów jednostkowych dla kodu Python w programie Visual Studio w pełni wykorzystuje funkcje Eksploratora testów do odnajdywania, uruchamiania i debugowania testów.
ms.date: 09/18/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 2a621cd56f980c8a1404ba8855cdf3544e58d39d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85535338"
---
# <a name="set-up-unit-testing-for-python-code"></a>Konfigurowanie testów jednostkowych dla kodu w języku Python

Testy jednostkowe są fragmentami kodu, które testują inne jednostki kodu w aplikacji, zazwyczaj izolowane funkcje, klasy i tak dalej. Gdy aplikacja przejdzie wszystkie testy jednostkowe, można co najmniej ufać, że jej funkcje niskiego poziomu są poprawne.

W języku Python testy jednostkowe są szeroko wykorzystywane do sprawdzania poprawności scenariuszy podczas projektowania programu. Obsługa języka Python w programie Visual Studio obejmuje odnajdywanie, wykonywanie i debugowanie testów jednostkowych w kontekście procesu opracowywania, bez konieczności niezależnego uruchamiania testów.

Ten artykuł zawiera krótkie omówienie możliwości testowania jednostkowego w programie Visual Studio przy użyciu języka Python. Aby uzyskać więcej informacji na temat testów jednostkowych, zobacz [test jednostkowy kodu](../test/unit-test-your-code.md).

::: moniker range="vs-2017"

[!include[Testing Python code](includes/vs-2017/unit-testing-python.md)]

::: moniker-end

::: moniker range=">= vs-2019"

[!include[Testing Python code](includes/vs-2019/unit-testing-python.md)]

::: moniker-end