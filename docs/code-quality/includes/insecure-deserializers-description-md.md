---
author: dotpaul
ms.author: paulming
ms.date: 04/05/2019
ms.topic: include
ms.openlocfilehash: 054198eff46c0983a5610b29dee5e29e5ac67a70
ms.sourcegitcommit: 748d9cd7328a30f8c80ce42198a94a4b5e869f26
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/15/2019
ms.locfileid: "68147096"
---
Niezabezpieczone deserializatory są narażone na deserializacja niezaufanych danych. Osoba atakująca może zmodyfikować serializowane dane w celu uwzględnienia nieoczekiwanych typów, aby wstrzyknąć obiekty ze złośliwymi efektami ubocznymi. Atak na niezabezpieczony Deserializator może na przykład wykonywać polecenia w podstawowym systemie operacyjnym, komunikować się przez sieć lub usuwać pliki.