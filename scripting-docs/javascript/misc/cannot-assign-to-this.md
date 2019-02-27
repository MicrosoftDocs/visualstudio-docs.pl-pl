---
title: Nie można przypisać do "this" | Dokumentacja firmy Microsoft
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5000
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ba2b0a2b-f0f8-4698-b335-a4ab6c166671
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f147e591969f803533bb23ff16d73ee9af2c3d27
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2019
ms.locfileid: "56839792"
---
# <a name="cannot-assign-to-this"></a>Nie można przypisać do „tego"
Próba przypisania wartości do **to**. **to** jest [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] — słowo kluczowe, która odwołuje się do albo:

- Obiekt metody, w trakcie wykonywania

- Obiekt globalny, jeśli nie istnieje metoda bieżącego (lub metoda nie należy do żadnego innego obiektu).

Metoda jest [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] funkcję wywoływaną za pomocą obiektu. Wewnątrz metody **to** — słowo kluczowe jest odwołanie do obiektu, metoda została wywołana przy użyciu (które akurat jest obiekt utworzony przez wywołanie konstruktora klasy za pomocą **nowe** operator).

Wewnątrz metody, można użyć **to** do odwoływania się do bieżącego obiektu, ale nie można przypisać nową wartość do **to**.

## <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- Nie należy przypisywać **to**. Aby uzyskać dostęp do właściwości lub metody wystąpień obiektu, należy użyć operatora kropka (np. **circle.radius**).

  > [!NOTE]
  > Nie można nazwać zmienną użytkownik utworzył **to**; jest [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] słowa zarezerwowanego.

## <a name="see-also"></a>Zobacz też

- [this, instrukcja](../../javascript/reference/this-statement-javascript.md)
- [Rozwiązywanie problemów ze skryptami](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)