---
title: Konfigurowanie obiektów docelowych i zadań | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9aabe67a-1720-4bbf-80d3-822b3ccf75c0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d3dedf051bf9b9d60f659d8b8ad22535a4eccb4c
ms.sourcegitcommit: 257fc60eb01fefafa9185fca28727ded81b8bca9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2019
ms.locfileid: "72912094"
---
# <a name="configure-targets-and-tasks"></a>Konfigurowanie obiektów docelowych i zadań
Można skonfigurować elementy docelowe i zadania programu MSBuild do uruchamiania poza procesem przy użyciu programu MSBuild, aby można było dowiedzieć się, jakie są inne niż te, z których korzystasz. Na przykład można określić 32-bitową .NET Framework 2,0 aplikacji, gdy na komputerze deweloperskim jest uruchomiony system operacyjny 64 .NET Framework 4,5. Można również kierować komputery z systemem z .NET Framework 4 lub wcześniejszym. Kombinacja 32-lub 64-bitową i konkretnej wersji .NET Framework jest znana jako *kontekst docelowy*.

## <a name="installation"></a>Instalacja
 .NET Framework 4,5 i 4.5.1 zastępują środowisko uruchomieniowe języka wspólnego (CLR), cele, zadania i narzędzia dla .NET Framework 4 bez zmiany ich nazw. .NET Framework 4.5.1 jest instalowany jako część [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)].

 Jeśli chcesz zainstalować program MSBuild niezależnie od programu Visual Studio, możesz pobrać pakiet instalacyjny z programu [MSBuild Download](https://www.microsoft.com/download/details.aspx?id=40760). Należy również zainstalować wersje .NET Framework, których chcesz użyć.

## <a name="targets-and-tasks"></a>Cele i zadania
 Program MSBuild uruchamia niektóre zadania kompilacji, aby określić większy zestaw kontekstów.  Na przykład 32-bitowy program MSBuild może uruchomić zadanie kompilacji w procesie 64-bitowym, aby wskazać komputer z 64-bitowym. Jest to kontrolowane przez `UsingTask` argumenty i `Task` parametrów. Elementy docelowe zainstalowane przez .NET Framework 4,5 ustawiają te argumenty i parametry, a żadne zmiany nie są wymagane do kompilowania aplikacji dla różnych kontekstów docelowych.

 Jeśli chcesz utworzyć własny kontekst docelowy, musisz odpowiednio ustawić te argumenty i parametry. Na przykład zapoznaj się z plikiem .NET Framework 4,5 *Microsoft. Common. targets* i *Microsoft. Common. Tasks* .  Aby uzyskać informacje o sposobach tworzenia niestandardowego zadania, które może współdziałać z wieloma kontekstami docelowymi lub jak modyfikować istniejące zadania, zobacz [How to: Configure targets and Tasks](../msbuild/how-to-configure-targets-and-tasks.md).

## <a name="see-also"></a>Zobacz także
- [Wielowersyjność kodu](../msbuild/msbuild-multitargeting-overview.md)