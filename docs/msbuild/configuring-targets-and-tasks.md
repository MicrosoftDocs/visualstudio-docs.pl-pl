---
title: Konfigurowanie obiektów docelowych i zadań | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9aabe67a-1720-4bbf-80d3-822b3ccf75c0
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 39a3d6ba3eff6a01c2d0ff68b4132d883eadb90f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634399"
---
# <a name="configure-targets-and-tasks"></a>Konfigurowanie obiektów docelowych i zadań

Można skonfigurować obiekty docelowe i zadania MSBuild do uruchamiania poza procesem za pomocą usługi MSBuild, dzięki czemu można kierować konteksty, które różnią się od tego, na który jest uruchomiona. Na przykład można kierować 32-bitową aplikację .NET Framework 2.0, gdy komputer deweloperski jest uruchomiony na 64-bitowym systemie operacyjnym .NET Framework 4.5. Można również kierować komputery, które są uruchamiane z .NET Framework 4 lub wcześniej. Połączenie 32- lub 64-bitowości i konkretnej wersji programu .NET Framework jest znane jako *kontekst docelowy.*

## <a name="installation"></a>Instalacja

  Jeśli chcesz zainstalować MSBuild oddzielnie od programu Visual Studio, możesz pobrać pakiet instalacyjny z [pliku MSBuild download](https://www.microsoft.com/download/details.aspx?id=40760). Należy również zainstalować wersje programu .NET Framework, których chcesz użyć.

## <a name="targets-and-tasks"></a>Cele i zadania

 MSBuild uruchamia niektóre zadania kompilacji z procesu do kierowania większy zestaw kontekstów.  Na przykład 32-bitowy msbuild może uruchomić zadanie kompilacji w procesie 64-bitowym do docelowego komputera 64-bitowego. Jest to `UsingTask` kontrolowane `Task` przez argumenty i parametry. Obiekty docelowe zainstalowane przez program .NET Framework 4.5 ustawiają te argumenty i parametry i żadne zmiany nie są wymagane do tworzenia aplikacji dla różnych kontekstów docelowych.

 Jeśli chcesz utworzyć własny kontekst docelowy, należy odpowiednio ustawić te argumenty i parametry. Poszukaj w pliku .NET Framework 4.5 *Microsoft.Common.targets* i pliku *Microsoft.Common.Tasks.*  Aby uzyskać informacje dotyczące tworzenia zadania niestandardowego, które może pracować z wieloma kontekstami docelowymi lub sposobu modyfikowania istniejących zadań, zobacz [Jak: Konfigurowanie obiektów docelowych i zadań](../msbuild/how-to-configure-targets-and-tasks.md).

## <a name="see-also"></a>Zobacz też

- [Wielotargowe](../msbuild/msbuild-multitargeting-overview.md)
