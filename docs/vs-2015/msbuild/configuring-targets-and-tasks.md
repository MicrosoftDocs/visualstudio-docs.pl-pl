---
title: Konfigurowanie obiektów docelowych i zadań | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
ms.assetid: 9aabe67a-1720-4bbf-80d3-822b3ccf75c0
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 892e9615599a8881e219c00f748a0cc1567d996d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75850034"
---
# <a name="configuring-targets-and-tasks"></a>Konfigurowanie obiektów docelowych i zadań
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można skonfigurować elementy docelowe i zadania programu MSBuild do uruchamiania poza procesem przy użyciu programu MSBuild, aby można było dowiedzieć się, jakie są inne niż te, z których korzystasz. Na przykład można określić 32-bitową .NET Framework 2,0 aplikacji, gdy na komputerze deweloperskim jest uruchomiony system operacyjny 64 .NET Framework 4,5. Można również kierować komputery z systemem z .NET Framework 4 lub wcześniejszym. Kombinacja 32-lub 64-bitową i konkretnej wersji .NET Framework jest znana jako *kontekst docelowy*.  
  
## <a name="installation"></a>Instalacja  
 .NET Framework 4,5 i 4.5.1 zastępują środowisko uruchomieniowe języka wspólnego (CLR), cele, zadania i narzędzia dla .NET Framework 4 bez zmiany ich nazw. .NET Framework 4.5.1 jest instalowany jako część [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] .  
  
 Jeśli chcesz zainstalować program MSBuild niezależnie od programu Visual Studio, możesz pobrać pakiet instalacyjny z programu [MSBuild Download](https://www.microsoft.com/download/details.aspx?id=40760). Należy również zainstalować wersje .NET Framework, których chcesz użyć.  
  
## <a name="targets-and-tasks"></a>Cele i zadania  
 Program MSBuild uruchamia niektóre zadania kompilacji, aby określić większy zestaw kontekstów.  Na przykład 32-bitowy program MSBuild może uruchomić zadanie kompilacji w procesie 64-bitowym, aby wskazać komputer z 64-bitowym. Jest to kontrolowane przez `UsingTask` argumenty i `Task` parametry. Elementy docelowe zainstalowane przez .NET Framework 4,5 ustawiają te argumenty i parametry, a żadne zmiany nie są wymagane do kompilowania aplikacji dla różnych kontekstów docelowych.  
  
 Jeśli chcesz utworzyć własny kontekst docelowy, musisz odpowiednio ustawić te argumenty i parametry. Na przykład zapoznaj się z plikiem .NET Framework 4,5 Microsoft. Common. targets i Microsoft. Common. Tasks.  Aby uzyskać informacje o sposobach tworzenia niestandardowego zadania, które może współdziałać z wieloma kontekstami docelowymi lub jak modyfikować istniejące zadania, zobacz [How to: Configure targets and Tasks](../msbuild/how-to-configure-targets-and-tasks.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wielowersyjności kodu](../msbuild/msbuild-multitargeting-overview.md)
