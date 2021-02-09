---
title: Nawigator wykorzystania | Microsoft Docs
description: Dowiedz się, w jaki sposób można użyć nawigatora użycia w wizualizatorze współbieżności, aby wybrać przedział czasu w śladzie.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.performance.utilizationnavigator
ms.assetid: 522a981a-37ef-4cdd-a04c-f1e7525a2aab
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3d92747bb90cae18a79e81e49689ce8c01b8a9b1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99917572"
---
# <a name="utilization-navigator"></a>Nawigator wykorzystania
Możesz użyć nawigatora użycia w wizualizatorze współbieżności, aby wybrać interwał czasu w śladzie. Wizualizator współbieżności pokazuje wykorzystanie rdzeni procesora CPU przez proces docelowy w czasie. Ułatwia to sprawdzanie wzorców użycia procesora CPU, a także umożliwia porównanie danych użycia i danych w innych widokach. Nawigator wykorzystania pojawia się u góry każdego widoku w wizualizatorze współbieżności. Na poniższej ilustracji przedstawiono Nawigatora wykorzystania.

 ![Nawigator wykorzystania pokazujący wybrany przedział czasu](../profiling/media/cvutilizationnavigator.png "CVUtilizationNavigator") Nawigator wykorzystania i wybrany przedział czasu

 Na ilustracji wybrany interwał jest definiowany przez czerwony prostokąt, znany jako *kciuk*.

 Oto jak można użyć Nawigatora wykorzystania do manipulowania wyświetlanym zakresem czasu:

- Można przesuwać, przeciągając kciuk w lewo lub w prawo. (Klawiatura: Przenieś fokus do kciuka, a następnie naciśnij klawisz Strzałka w lewo lub w prawo).

- Zakres interwału można zmienić, przeciągając jeden z uchwytów. (Klawiatura: przeniesienie fokusu do uchwytu, a następnie naciśnięcie klawisza Strzałka w prawo lub w lewo).

  W przypadku zmiany interwału przy użyciu innej kontrolki powiększenia wizualizatora współbieżności aktualizacje nawigatora są aktualizowane w celu odzwierciedlenia zmiany.