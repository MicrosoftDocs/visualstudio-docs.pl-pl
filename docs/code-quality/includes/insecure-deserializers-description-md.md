---
author: dotpaul
ms.author: paulming
ms.date: 04/05/2019
ms.topic: include
ms.openlocfilehash: 43327901b2233b9b2818296f9269975d8524438b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62541565"
---
Niebezpieczne deserializers są zagrożone, podczas deserializacji niezaufanych danych. Osoba atakująca może zmodyfikować dane serializowane obejmuje dodatkowe typy nieoczekiwany przy użyciu złośliwych efekty uboczne. Ataku na niezabezpieczone Deserializator można, na przykład wykonywać polecenia w podstawowym systemie operacyjnym, komunikują się za pośrednictwem sieci lub usuwania plików.