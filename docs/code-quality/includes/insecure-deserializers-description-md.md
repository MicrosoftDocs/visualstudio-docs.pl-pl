---
author: dotpaul
ms.author: paulming
ms.date: 04/05/2019
ms.topic: include
ms.openlocfilehash: 43327901b2233b9b2818296f9269975d8524438b
ms.sourcegitcommit: 0e22ead8234b2c4467bcd0dc047b4ac5fb39b977
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59367355"
---
Niebezpieczne deserializers są zagrożone, podczas deserializacji niezaufanych danych. Osoba atakująca może zmodyfikować dane serializowane obejmuje dodatkowe typy nieoczekiwany przy użyciu złośliwych efekty uboczne. Ataku na niezabezpieczone Deserializator można, na przykład wykonywać polecenia w podstawowym systemie operacyjnym, komunikują się za pośrednictwem sieci lub usuwania plików.