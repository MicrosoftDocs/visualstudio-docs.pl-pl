---
title: Procent redukcji szumów | Microsoft Docs
description: Dowiedz się więcej o ustawieniu procentowym obniżki szumów i sposobach kontrolowania liczby wpisów, które są wyświetlane w drzewie wywołań.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.filter
helpviewer_keywords:
- Concurrency Visualizer, Noise Reduction Percentage
ms.assetid: 1c10cd4c-2fdd-48c9-b562-a334b3b2df6c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 531ff082197ca1f7e63008aeda1c27e083b569de
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99922426"
---
# <a name="noise-reduction-percentage"></a>Procent redukcji szumu
Domyślnie wartość ustawienia procent redukcji szumu to 2. W drzewie wywołań są wyświetlane tylko wpisy, które mają wartość procentową łącznego czasu, większą lub równą temu ustawieniu. Zmiana ustawienia pozwala kontrolować liczbę wpisów, które są wyświetlane w drzewie wywołań. Na przykład zmiana wartości na 10 spowoduje wyświetlenie tylko wpisów drzewa wywołań, które mają czas włączny o wartości większej lub równej 10%. Zwiększając wartość ustawienia, można skupić się na wpisach, które mają większy wpływ na wydajność procesu.