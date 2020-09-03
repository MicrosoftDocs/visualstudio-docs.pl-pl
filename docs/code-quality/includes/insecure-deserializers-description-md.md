---
author: dotpaul
ms.author: paulming
ms.date: 04/05/2019
ms.topic: include
ms.openlocfilehash: 054198eff46c0983a5610b29dee5e29e5ac67a70
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "89325926"
---
Niezabezpieczone deserializatory są narażone na deserializacja niezaufanych danych. Osoba atakująca może zmodyfikować serializowane dane w celu uwzględnienia nieoczekiwanych typów, aby wstrzyknąć obiekty ze złośliwymi efektami ubocznymi. Atak na niezabezpieczony Deserializator może na przykład wykonywać polecenia w podstawowym systemie operacyjnym, komunikować się przez sieć lub usuwać pliki.