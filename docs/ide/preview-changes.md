---
title: Podgląd zmian w kodzie
description: Dowiedz się, jak użyć okna Podgląd zmian, aby przejść do modyfikacji, które mają zostać wprowadzone do projektu przed ich zaakceptowaniem.
ms.custom: SEO-VS-2020
ms.date: 12/16/2016
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jmartens
f1_keywords:
- vs.codefix.previewchanges
ms.workload:
- multiple
ms.openlocfilehash: 55a53e60ffa05892531257871ede89381e7fd4e2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99909011"
---
# <a name="preview-changes-window"></a>Podgląd okna zmian

W przypadku korzystania z różnych *szybkich akcji* lub narzędzi *refaktoryzacji* w programie Visual Studio często istnieje możliwość wyświetlenia podglądu zmian, które mają zostać wprowadzone do projektu przed ich zaakceptowaniem. W tym miejscu zostanie wykonane okno **Podgląd zmian** .  Na przykład poniżej znajduje się okno **Podgląd zmian** pokazujące, co zostanie zmienione podczas refaktoryzacji zmiany nazwy w projekcie C#:

![Podgląd zmian](media/previewchanges.png)

W górnej połowie okna są wyświetlane określone wiersze, które zostaną zmienione, z których każdy ma wartość pola wyboru. Możesz zaznaczyć lub wyczyścić każde pole wyboru, jeśli chcesz selektywnie zastosować refaktoryzację tylko do określonych wierszy.

Dolna połowa okna pokazuje sformatowany kod z projektu, który zostanie zmieniony, z wyróżnionymi obszarami, których dotyczy. Wybranie określonego wiersza w górnej połowie okna spowoduje wyróżnienie odpowiedniego wiersza w dolnej części. Pozwala to na szybkie przechodzenie do odpowiedniego wiersza i wyświetlanie otaczającego kodu.

Po przejrzeniu zmian kliknij przycisk **Zastosuj** , aby zatwierdzić te zmiany, lub kliknij przycisk **Anuluj** , aby pozostawić elementy, które były takie same.

## <a name="see-also"></a>Zobacz też

- [Refaktoryzacja w programie Visual Studio](../ide/refactoring-in-visual-studio.md)
- [Szybkie akcje](../ide/quick-actions.md)
