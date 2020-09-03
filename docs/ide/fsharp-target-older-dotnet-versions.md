---
title: 'Docelowa Poprzednia wersja .NET Framework dla języka F #'
description: 'Dowiedz się więcej na temat określania starszej wersji .NET Framework przy użyciu języka F # w programie Visual Studio.'
ms.date: 07/11/2018
ms.topic: troubleshooting
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
monikerRange: vs-2017
ms.openlocfilehash: 4b5cf62dadc38802e477c7588416b4003304e852
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75584585"
---
# <a name="target-older-versions-of-net-f"></a>Docelowe starsze wersje platformy .NET (F #)

Następujący błąd może się pojawić w przypadku próby przekierowania .NET Framework 2,0, 3,0 lub 3,5 w projekcie F #, gdy program Visual Studio jest zainstalowany na Windows 8.1:

**Ten projekt wymaga środowiska uruchomieniowego F # 2,0, ale środowisko uruchomieniowe nie jest zainstalowane.**

Ten błąd występuje w następującej kombinacji warunków:

- Program Visual Studio został zainstalowany na Windows 8.1.

- Nie włączono .NET Framework 3,5 przed zainstalowaniem programu Visual Studio.

- Projekt jest przeznaczony dla .NET Framework 2,0, 3,0 lub 3,5.

Po zainstalowaniu programu Visual Studio program wykrywa zainstalowane wersje .NET Framework. Program Visual Studio instaluje środowisko uruchomieniowe F # 2,0 tylko wtedy, gdy .NET Framework 3,5 jest zainstalowana i włączona.

## <a name="resolve-the-error"></a>Usuń błąd

Aby rozwiązać ten problem, możesz:

- Docelowa jest nowsza wersja .NET Framework.

- Włącz .NET Framework 3,5 na Windows 8.1, a następnie zainstaluj środowisko uruchomieniowe F # 2,0, naprawiając instalację programu Visual Studio. Wykonaj poniższe czynności.

### <a name="to-enable-the-net-framework-35-on-windows-81"></a>Aby włączyć .NET Framework 3,5 na Windows 8.1

1. Na ekranie **startowym** wpisz **Panel sterowania**.

   Podczas wpisywania ikona **Panelu sterowania** pojawia się pod nagłówkiem **aplikacje** .

2. Wybierz ikonę **Panelu sterowania** , wybierz ikonę **programy** , a następnie wybierz łącze **Włącz lub wyłącz funkcje systemu Windows** .

3. Upewnij się, że pole wyboru **.NET Framework 3,5 (zawiera .net 2,0 i 3,0)** jest zaznaczone, a następnie wybierz przycisk **OK** . Nie musisz zaznaczać pól wyboru dla żadnych węzłów podrzędnych dla opcjonalnych składników .NET Framework.

   .NET Framework 3,5 jest włączona, jeśli nie została jeszcze.

### <a name="to-install-the-f-20-runtime"></a>Aby zainstalować środowisko uruchomieniowe F # 2,0

Postępuj zgodnie z [instrukcjami, aby naprawić program Visual Studio](../install/repair-visual-studio.md).

## <a name="see-also"></a>Zobacz też

- [Przewodnik po języku F # (.NET Framework)](/dotnet/fsharp/)
- [Język F# w programie Visual Studio](fsharp-visual-studio.md)
