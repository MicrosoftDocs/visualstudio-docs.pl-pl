---
author: dotpaul
ms.author: paulming
ms.date: 05/01/2019
ms.topic: include
ms.openlocfilehash: bc423f10cfbae0b7a0cdaedb72f6891a0e12d228
ms.sourcegitcommit: db30651dc0ce4d0b274479b23a6bd102a5559098
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2019
ms.locfileid: "65135555"
---
- Jeśli to możliwe, Użyj bezpiecznego serializator, i **nie można określić dowolny typ do deserializacji osobie atakującej**. Niektóre bezpieczniejsze serializatory obejmują:
  - <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>
  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>
  - <xref:System.Web.Script.Serialization.JavaScriptSerializer?displayProperty=nameWithType> -Nigdy nie używaj <xref:System.Web.Script.Serialization.SimpleTypeResolver?displayProperty=nameWithType>. Jeśli musisz użyć typu program rozpoznawania nazw, ograniczyć typy po deserializacji do oczekiwanej listy.
  - <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>
  - Newtonsoft Json.NET — Użyj TypeNameHandling.None. Jeśli musisz użyć innej wartości dla TypeNameHandling, ograniczyć po deserializacji typów do oczekiwanej listy przy użyciu niestandardowych ISerializationBinder.
  - Protocol Buffers
- Należy odporne serializowanych danych. Po serializacji podpisać kryptograficznie serializowanych danych. Przed deserializacji należy zweryfikować podpisu kryptograficznego. Ochrona klucza kryptograficznego zostały ujawnione i projektowanie pod kątem wymiany kluczy.