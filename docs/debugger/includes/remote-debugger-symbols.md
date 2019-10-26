---
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.openlocfilehash: 5033580f253a5eb42cbc64656e8c4661a2e246c1
ms.sourcegitcommit: 257fc60eb01fefafa9185fca28727ded81b8bca9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2019
ms.locfileid: "72912855"
---
Powinno być możliwe debugowanie kodu przy użyciu symboli generowanych na komputerze z programem Visual Studio. Wydajność zdalnego debugera jest znacznie lepsza w przypadku używania symboli lokalnych.  Jeśli musisz użyć symboli zdalnych, musisz poinformować Monitor debugowania zdalnego, aby szukać symboli na maszynie zdalnej.  

Począwszy od Visual Studio 2013 Update 2, można użyć następującego przełącznika wiersza polecenia msvsmon, aby użyć symboli zdalnych dla kodu zarządzanego: `Msvsmon /FallbackLoadRemoteManagedPdbs`  

Aby uzyskać więcej informacji, zobacz Pomoc dotyczącą debugowania zdalnego (naciśnij klawisz **F1** w oknie debugera zdalnego lub kliknij pozycję **Pomoc > Użycie**). Więcej informacji można znaleźć w temacie [zdalne ładowanie symboli .NET w programie Visual Studio 2012 i 2013](https://devblogs.microsoft.com/devops/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013/)
