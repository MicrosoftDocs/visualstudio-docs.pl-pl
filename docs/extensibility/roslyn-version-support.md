---
title: Obsługiwane mapowania wersji pakietu Roslyn
description: W tym artykule przedstawiono wersje pakietów platformy kompilatora .NET (Roslyn) obsługiwane przez różne wersje programu Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 04/29/2019
ms.topic: reference
helpviewer_keywords:
- roslyn package versions
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f76a8dcdbb644fe456c62fca7de6fb7afe96d556
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99935898"
---
# <a name="net-compiler-platform-package-version-reference"></a>Dokumentacja wersji pakietu platformy kompilatora .NET

W poniższej tabeli przedstawiono wersje [pakietów platformy kompilatora .NET (Roslyn)](https://www.nuget.org/packages/Microsoft.Net.Compilers/) obsługiwane przez różne wersje programu Visual Studio.

Na przykład aby upewnić się, że analizator niestandardowy działa na wszystkich wersjach programu Visual Studio 2017, powinien on być celem wersji 2,0 Microsoft.Net. Kompilators.

| Wersja pakietu Roslyn | Minimalna obsługiwana wersja programu Visual Studio |
| - | - |
| wersji | Visual Studio 2019 |
| 2.10.0 | Visual Studio 2017 w wersji 15,9 |
| 2.9.0 | Visual Studio 2017 w wersji 15,8 |
| 2.8.2 | Visual Studio 2017 w wersji 15.7 |
| 2.7.0 | Visual Studio 2017, wersja 15.6 |
| 2.6.1 | Visual Studio 2017, wersja 15.5 |
| 2.4.0 | Visual Studio 2017, wersja 15.4 |
| 2.3.2 | Visual Studio 2017, wersja 15.3 |
| 2.2.0 | Program Visual Studio 2017 w wersji 15.2 |
| 2.1.0 | Program Visual Studio 2017 w wersji 15.1 |
| 2.0.0 | Visual Studio 2017 RTM |
| 1.3.2 | Visual Studio 2015 Update 3 |
| ppkt | Visual Studio 2015 Update 2 |
| 1.1.1 | Visual Studio 2015 Update 1 |
| 1.0.1 | Visual Studio 2015 RTM |

> [!TIP]
> W przypadku pakietów Roslyn, w których minimalna obsługiwana wersja programu Visual Studio to wersja programu Visual Studio 2017, wszystkie wersje programu Visual Studio 2019 są również obsługiwane, ponieważ zostały one później dołączone.

## <a name="see-also"></a>Zobacz też

- [Zestaw SDK platformy kompilatora .NET](/dotnet/csharp/roslyn-sdk/)
- [Wprowadzenie do analizatorów Roslyn](getting-started-with-roslyn-analyzers.md)
