---
title: Pierwsze kroki z Analizatorami Roslyn | Dokumenty firmy Microsoft
ms.date: 04/02/2018
ms.topic: conceptual
ms.assetid: 367c2ec8-3059-46a5-9d1c-57bead0419e7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bc975ff4f142b85297c20f16ac399fce588c093b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711270"
---
# <a name="get-started-with-roslyn-analyzers"></a>Wprowadzenie do analizatorów Roslyn

Za pomocą analizatorów kodu na żywo, opartych na projekcie w programie Visual Studio, autorzy interfejsu API mogą wysyłać analizę kodu specyficzne dla domeny w ramach swoich pakietów NuGet. Ponieważ te analizatory są obsługiwane przez platformę kompilatora .NET (o nazwie kodowej "Roslyn"), mogą one powodować ostrzeżenia w kodzie podczas pisania, nawet przed zakończeniem wiersza (nie więcej czeka na tworzenie kodu w celu wykrycia problemów). Analizatory można również powierzchni automatyczną poprawkę kodu za pośrednictwem monitu żarówki programu Visual Studio, aby umożliwić natychmiastowe oczyszczenie kodu.

## <a name="get-started"></a>Wprowadzenie

[Przegląd analizatorów Roslyn](../code-quality/roslyn-analyzers-overview.md)

[Samouczek: Napisz swój pierwszy analizator i poprawkę kodu](/dotnet/csharp/roslyn-sdk/tutorials/how-to-write-csharp-analyzer-code-fix)

[Dodaj poprawki kodu Przewodnik: Podaj użytkownikom poprawki problemów z analizatorem](https://msdn.microsoft.com/magazine/dn904670.aspx)

[Prawdziwy analizator Roslyn świata,](../extensibility/roslyn-analyzers-and-code-aware-library-for-immutablearrays.md) który można również oglądać jako [rozmowę](https://channel9.msdn.com/events/Build/2015/3-725)

[Kilka przykładów na GitHub, pogrupowane w trzy rodzaje analizatorów](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)

## <a name="see-also"></a>Zobacz też

- [Odwołanie do wersji pakietu platformy kompilatora .NET](roslyn-version-support.md)
- [Więcej dokumentów w witrynie gitHub OSS](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)
- [Reguły FxCop zaimplementowane za pomocą analizatorów Roslyn](../code-quality/fxcop-rule-port-status.md)
