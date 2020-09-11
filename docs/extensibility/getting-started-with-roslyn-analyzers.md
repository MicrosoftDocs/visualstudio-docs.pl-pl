---
title: Wprowadzenie z analizatorami Roslyn | Microsoft Docs
ms.date: 04/02/2018
ms.topic: conceptual
ms.assetid: 367c2ec8-3059-46a5-9d1c-57bead0419e7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4d572c49f7d528b9dbb624bf31ad5e28dc3799aa
ms.sourcegitcommit: 4b29efeb3a5f05888422417c4ee236e07197fb94
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2020
ms.locfileid: "90012246"
---
# <a name="get-started-with-roslyn-analyzers"></a>Wprowadzenie do analizatorów Roslyn

Korzystając z na żywo analizatorów kodu opartego na projekcie w programie Visual Studio, autorzy interfejsu API mogą dostarczać analizę kodu specyficzną dla domeny jako część pakietów NuGet. Ponieważ te analizatory są obsługiwane przez .NET Compiler Platform (kod o nazwie "Roslyn"), mogą generować ostrzeżenia w kodzie podczas pisania, nawet przed ukończeniem wiersza (nie trzeba czekać na skompilowanie kodu w celu odnalezienia problemów). Analizatory mogą również nawiązać automatyczne rozwiązywanie problemów z kodem za pomocą monitu o żarówkę programu Visual Studio, aby umożliwić natychmiastowe wyczyszczenie kodu.

## <a name="get-started"></a>Rozpoczęcie pracy

[Omówienie analizatorów Roslyn](../code-quality/roslyn-analyzers-overview.md)

[Samouczek: Napisz pierwszy Analizator i poprawkę kodu](/dotnet/csharp/roslyn-sdk/tutorials/how-to-write-csharp-analyzer-code-fix)

[Dodawanie poprawek kodu Przewodnik: udostępnianie użytkownikom poprawek do problemów analizatora](/archive/msdn-magazine/2015/february/csharp-adding-a-code-fix-to-your-roslyn-analyzer)

[Real World Roslyn Analyzer](../extensibility/roslyn-analyzers-and-code-aware-library-for-immutablearrays.md) , który można także obejrzeć jako [rozmowę](https://channel9.msdn.com/events/Build/2015/3-725)

[Kilka przykładów w witrynie GitHub pogrupowanych na trzy rodzaje analizatorów](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)

## <a name="see-also"></a>Zobacz także

- [Dokumentacja wersji pakietu platformy kompilatora .NET](roslyn-version-support.md)
- [Więcej dokumentów w witrynie usługi GitHub](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)
- [Reguły FxCop zaimplementowane z analizatorami Roslyn](../code-quality/fxcop-rule-port-status.md)