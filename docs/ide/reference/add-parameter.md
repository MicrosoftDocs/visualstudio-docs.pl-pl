---
title: Dodawanie parametru do szybkiej akcji metody
description: Dowiedz się, jak używać szybkiej akcji do automatycznego dodawania i deklarowania parametru, na podstawie użycia, do metody.
ms.custom: SEO-VS-2020
ms.date: 09/28/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: c1e623bea0eab4b45aec3d331864db49a2787f8c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99846351"
---
# <a name="add-a-parameter-to-a-method-using-a-quick-action"></a>Dodawanie parametru do metody przy użyciu szybkiej akcji

Ta generacja kodu ma zastosowanie do:

- C#

- Visual Basic

**Co:** Umożliwia automatyczne dodanie parametru do metody na podstawie użycia.

**Kiedy:** Musisz dodać parametr do metody i chcieć prawidłowo zadeklarować ją automatycznie.

**Dlaczego:** Można dodać parametr do deklaracji metody przed wywołaniem, jednak ta funkcja automatycznie dodaje ją na podstawie wywołania metody.

## <a name="how-to-use-it"></a>Sposób użycia

1. Dodaj dodatkowy argument do wywołania metody.

   Czerwona zygzakowata pojawia się pod nazwą metody, w której jest wywoływana.

2. Umieść wskaźnik myszy na czerwono, aby pojawiło się menu szybkie akcje. Wybierz **strzałkę w dół** w menu szybkie akcje, a następnie wybierz polecenie **Dodaj parametr do [Metoda]**.

   ![Dodawanie parametru do szybkiej akcji metody w programie Visual Studio](media/add-parameter-to-method.png)

   > [!TIP]
   > Możesz również uzyskać dostęp do menu szybkie akcje, umieszczając kursor w wierszu wywołania metody, a następnie naciskając klawisz **Ctrl** + **.** (kropka) lub wybierz ikonę żarówki w marginesie pliku.

   Program Visual Studio dodaje nowy parametr do deklaracji metody.

> [!NOTE]
> Jeśli masz inne wywołania metody, mogą one generować błędy po użyciu tej szybkiej akcji, ponieważ nie określają argumentu dla nowo dodanego parametru.

## <a name="see-also"></a>Zobacz też

- [Dodaj parametr do konstruktora](generate-constructor.md#addparameter)
