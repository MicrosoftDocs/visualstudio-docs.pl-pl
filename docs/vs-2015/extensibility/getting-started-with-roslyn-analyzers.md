---
title: Pierwsze kroki z Analizatorami Roslyn | Dokumenty firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 367c2ec8-3059-46a5-9d1c-57bead0419e7
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a712697bafefcf115ce10d110c0ef3a4270c6acd
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81444986"
---
# <a name="getting-started-with-roslyn-analyzers"></a>Wprowadzenie do analizatorów Roslyn
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Za pomocą analizatorów kodu na żywo, opartych na projekcie w programie Visual Studio, autorzy interfejsu API mogą wysyłać analizę kodu specyficzne dla domeny w ramach swoich pakietów NuGet.  Ponieważ te analizatory są obsługiwane przez platformę kompilatora .NET (o nazwie kodowej "Roslyn"), mogą one powodować ostrzeżenia w kodzie podczas pisania, nawet przed zakończeniem wiersza (nie więcej czeka na tworzenie kodu w celu wykrycia problemów).  Analizatory mogą również wyświetlać automatyczną poprawkę kodu za pomocą monitu o żarówkę programu Visual Studio, aby umożliwić natychmiastowe oczyszczenie kodu

## <a name="getting-started"></a>Getting Started
[Roslyn Live Code Analyzers Wprowadzenie i przewodnik](https://msdn.microsoft.com/magazine/dn879356.aspx)

[Dodawanie poprawki kodu Przewodnik: Podaj użytkownikom poprawki dla problemów z analizatorem](https://msdn.microsoft.com/magazine/dn904670.aspx)

[Wprowadzenie i przewodnik z Rzeczywistym Świecie Analizator Dyskusja](https://channel9.msdn.com/events/Build/2015/3-725)

[Real World Roslyn Analyzer,](../extensibility/roslyn-analyzers-and-code-aware-library-for-immutablearrays.md) które można również oglądać jako [rozmowę](https://channel9.msdn.com/events/Build/2015/3-725)

[Kilka przykładów na GitHub, pogrupowane w trzy rodzaje analizatorów](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)

[Wprowadzenie i zwiedzanie kilku analizatorów Dyskusja](https://channel9.msdn.com/Events/dotnetConf/2015/NET-Compiler-Platform-Roslyn-Analyzers-and-the-Rise-of-Code-Aware-Libraries)

## <a name="other-resources"></a>Inne zasoby
[Więcej dokumentów w witrynie gitHub OSS](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)

[Reguły FxCop zaimplementowane za pomocą analizatorów Roslyn na GitHub](https://github.com/dotnet/roslyn/tree/master/src/Features/Core/Portable/Diagnostics/Analyzers)
