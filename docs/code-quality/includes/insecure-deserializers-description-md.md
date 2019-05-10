---
author: dotpaul
ms.author: paulming
ms.date: 04/05/2019
ms.topic: include
ms.openlocfilehash: 054198eff46c0983a5610b29dee5e29e5ac67a70
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/09/2019
ms.locfileid: "65461825"
---
Niebezpieczne deserializers są zagrożone, podczas deserializacji niezaufanych danych. Osoba atakująca może zmodyfikować dane serializowane obejmuje dodatkowe typy nieoczekiwany iniekcję obiektów przy użyciu złośliwych efekty uboczne. Ataku na niezabezpieczone Deserializator można, na przykład wykonywać polecenia w podstawowym systemie operacyjnym, komunikują się za pośrednictwem sieci lub usuwania plików.