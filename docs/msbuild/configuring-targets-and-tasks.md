---
title: Konfigurowanie obiektów docelowych i zadań | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9aabe67a-1720-4bbf-80d3-822b3ccf75c0
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 39a3d6ba3eff6a01c2d0ff68b4132d883eadb90f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "77634399"
---
# <a name="configure-targets-and-tasks"></a>Konfigurowanie obiektów docelowych i zadań

Można skonfigurować elementy docelowe i zadania programu MSBuild do uruchamiania poza procesem przy użyciu programu MSBuild, aby można było dowiedzieć się, jakie są inne niż te, z których korzystasz. Na przykład można określić 32-bitową .NET Framework 2,0 aplikacji, gdy na komputerze deweloperskim jest uruchomiony system operacyjny 64 .NET Framework 4,5. Można również kierować komputery z systemem z .NET Framework 4 lub wcześniejszym. Kombinacja 32-lub 64-bitową i konkretnej wersji .NET Framework jest znana jako *kontekst docelowy*.

## <a name="installation"></a>Instalacja

  Jeśli chcesz zainstalować program MSBuild niezależnie od programu Visual Studio, możesz pobrać pakiet instalacyjny z programu [MSBuild Download](https://www.microsoft.com/download/details.aspx?id=40760). Należy również zainstalować wersje .NET Framework, których chcesz użyć.

## <a name="targets-and-tasks"></a>Cele i zadania

 Program MSBuild uruchamia niektóre zadania kompilacji, aby określić większy zestaw kontekstów.  Na przykład 32-bitowy program MSBuild może uruchomić zadanie kompilacji w procesie 64-bitowym, aby wskazać komputer z 64-bitowym. Jest to kontrolowane przez `UsingTask` argumenty i `Task` parametry. Elementy docelowe zainstalowane przez .NET Framework 4,5 ustawiają te argumenty i parametry, a żadne zmiany nie są wymagane do kompilowania aplikacji dla różnych kontekstów docelowych.

 Jeśli chcesz utworzyć własny kontekst docelowy, musisz odpowiednio ustawić te argumenty i parametry. Na przykład zapoznaj się z plikiem .NET Framework 4,5 *Microsoft. Common. targets* i *Microsoft. Common. Tasks* .  Aby uzyskać informacje o sposobach tworzenia niestandardowego zadania, które może współdziałać z wieloma kontekstami docelowymi lub jak modyfikować istniejące zadania, zobacz [How to: Configure targets and Tasks](../msbuild/how-to-configure-targets-and-tasks.md).

## <a name="see-also"></a>Zobacz też

- [Wielowersyjności kodu](../msbuild/msbuild-multitargeting-overview.md)
