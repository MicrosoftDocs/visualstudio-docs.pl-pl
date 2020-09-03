---
title: Wprowadzenie z analizatorami Roslyn | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 367c2ec8-3059-46a5-9d1c-57bead0419e7
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a712697bafefcf115ce10d110c0ef3a4270c6acd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "81444986"
---
# <a name="getting-started-with-roslyn-analyzers"></a>Wprowadzenie do analizatorów Roslyn
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Korzystając z na żywo analizatorów kodu opartego na projekcie w programie Visual Studio, autorzy interfejsu API mogą dostarczać analizę kodu specyficzną dla domeny jako część pakietów NuGet.  Ponieważ te analizatory są obsługiwane przez .NET Compiler Platform (kod o nazwie "Roslyn"), mogą generować ostrzeżenia w kodzie podczas pisania, nawet przed ukończeniem wiersza (nie trzeba czekać na skompilowanie kodu w celu odnalezienia problemów).  Analizatory mogą również nawiązać automatyczne rozwiązywanie problemów z kodem za pomocą monitu programu Visual Studio Light żarówki, aby umożliwić natychmiastowe wyczyszczenie kodu

## <a name="getting-started"></a>Getting Started
[Roslyn analizatory kodu na żywo — wprowadzenie i Instruktaż](https://msdn.microsoft.com/magazine/dn879356.aspx)

[Dodawanie poprawek do kodu — Przewodnik: zapewnianie poprawek dla użytkowników w przypadku problemów z analizatorem](https://msdn.microsoft.com/magazine/dn904670.aspx)

[Wprowadzenie i przewodnik po rozmowie w świecie rzeczywistym](https://channel9.msdn.com/events/Build/2015/3-725)

[Real World Roslyn Analyzer](../extensibility/roslyn-analyzers-and-code-aware-library-for-immutablearrays.md) , który można także obejrzeć jako [rozmowę](https://channel9.msdn.com/events/Build/2015/3-725)

[Kilka przykładów w witrynie GitHub pogrupowanych na trzy rodzaje analizatorów](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)

[Wprowadzenie i samouczek dotyczący kilku analizatorów](https://channel9.msdn.com/Events/dotnetConf/2015/NET-Compiler-Platform-Roslyn-Analyzers-and-the-Rise-of-Code-Aware-Libraries)

## <a name="other-resources"></a>Inne zasoby
[Więcej dokumentów w witrynie usługi GitHub](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)

[Reguły FxCop zaimplementowane przy użyciu analizatorów Roslyn w witrynie GitHub](https://github.com/dotnet/roslyn/tree/master/src/Features/Core/Portable/Diagnostics/Analyzers)
