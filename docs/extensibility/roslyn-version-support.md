---
title: Obsługiwanych mapowań wersji pakietu Roslyn
ms.date: 04/29/2019
ms.topic: reference
helpviewer_keywords:
- roslyn package versions
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3b2dd97b078923cfa3358d56e6316bfff654c4dd
ms.sourcegitcommit: 62f42113ae4dae1ddfff1c4e02445acc09913445
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/29/2019
ms.locfileid: "64878240"
---
# <a name="net-compiler-platform-package-version-reference"></a>Odwołanie do .NET kompilatora platformy wersji pakietu

W poniższej tabeli przedstawiono, które [pakiet (Roslyn) platformy kompilatora .NET](https://www.nuget.org/packages/Microsoft.Net.Compilers/) wersje są obsługiwane dla różnych wersji programu Visual Studio.

Jako przykład aby upewnić się, że Twoje analizatora niestandardowego działa we wszystkich wersjach programu Visual Studio 2017 on powinien dotyczyć Microsoft.Net.Compilers w wersji 2.0.

| Wersja pakietu Roslyn | Minimalna obsługiwana wersja programu Visual Studio |
| - | - |
| 3.x | Visual Studio 2019 |
| 2.10.0 | Visual Studio 2017 w wersji 15.9 |
| 2.9.0 | Visual Studio 2017 w wersji 15.8 |
| 2.8.2 | Visual Studio 2017 w wersji 15.7 |
| 2.7.0 | Visual Studio 2017 wersja 15.6 |
| 2.6.1 | Visual Studio 2017 w wersji 15.5 |
| 2.4.0 | Visual Studio 2017 w wersji 15.4 |
| 2.3.2 | Visual Studio 2017 w wersji 15.3 |
| 2.2.0 | Visual Studio 2017 wersja 15.2 |
| 2.1.0 | Visual Studio 2017 wersja 15.1 |
| 2.0.0 | Visual Studio 2017 RTM |
| 1.3.2 | Visual Studio 2015 update 3 |
| 1.2.2 | Visual Studio 2015 update 2 |
| 1.1.1 | Visual Studio 2015 update 1 |
| 1.0.1 | Visual Studio 2015 RTM |

> [!TIP]
> W przypadku pakietów platformy Roslyn minimalna obsługiwana wersja programu Visual Studio w przypadku wersji programu Visual Studio 2017 wszystkie wersje programu Visual Studio 2019 r również są obsługiwane, ponieważ zaczęli oni później.

## <a name="see-also"></a>Zobacz także

- [Zestaw SDK platformy kompilatora .NET](/dotnet/csharp/roslyn-sdk/)
- [Wprowadzenie do analizatorów Roslyn](getting-started-with-roslyn-analyzers.md)