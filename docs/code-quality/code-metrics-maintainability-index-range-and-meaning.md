---
title: Metryki kodu — zakres indeksu utrzymania i znaczenie
ms.date: 1/8/2021
description: Dowiedz się więcej o metryki zakresu indeksu utrzymania dla metryk kodu w programie Visual Studio.
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: aa825b439b75606da136635d5816ac3e19ea8392
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860467"
---
# <a name="code-metrics---maintainability-index-range-and-meaning"></a>Metryki kodu — zakres indeksu utrzymania i znaczenie

Pytanie: indeks utrzymania został zresetowany do wartości z zakresu od 0 do 100. Jak i dlaczego to zrobić?

Pierwotnie obliczono metrykę w następujący sposób: `Maintainability Index = 171 - 5.2 * ln(Halstead Volume) - 0.23 * (Cyclomatic Complexity) - 16.2 * ln(Lines of Code)`

Użycie tej formuły oznaczało, że przedziały od 171 do nieograniczonej liczby ujemnej.  Jako kod o wartości 0, trudno było zachować kod i różnice między kodem w 0, a część ujemna nie była użyteczna.  W wyniku zmniejszenia użyteczności liczb ujemnych i chęci utrzymywania metryki jak najprawdopodobniej jest to możliwe, zalecamy traktowanie wszystkich 0 lub mniej indeksów jako 0, a następnie zmiana bazy 171 lub mniejszej na wartość z zakresu od 0 do 100. Z tego powodu formuła, której używamy, to:

   `Maintainability Index = MAX(0,(171 - 5.2 * ln(Halstead Volume) - 0.23 * (Cyclomatic Complexity) - 16.2 * ln(Lines of Code))*100 / 171)`

Oprócz tego przyjmujemy ostrożność przy progach.  Zachodzi taka konieczność, gdyby indeks był czerwony, a będziemy mieć wysoki stopień pewności, że wystąpił problem z kodem.  Podała nam następujące progi:

W przypadku progów podjęto decyzję o podziale tego 0-100 zakresu 80-20, aby zachować niski poziom szumu i tylko oflagowany kod, który był podejrzany. Użyto następujących progów:

- 0-9 = czerwony
- 10-19 = żółty
- 20-100 = zielony
