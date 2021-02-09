---
title: Kod języka Python testów jednostkowych
description: Skonfigurowanie testów jednostkowych dla kodu Python w programie Visual Studio w pełni wykorzystuje funkcje Eksploratora testów do odnajdywania, uruchamiania i debugowania testów.
ms.date: 09/18/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: aec13b3b35c75ecaad938cd3200f3af2a87d2441
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99920680"
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