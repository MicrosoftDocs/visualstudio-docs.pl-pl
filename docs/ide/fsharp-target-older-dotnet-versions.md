---
title: 'Kierowanie na poprzednie wersje programu .NET Framework dla systemu F #'
description: Dowiedz się więcej o kierowaniu na starszą wersję programu .NET Framework podczas korzystania z języka F# w programie Visual Studio.
ms.date: 07/11/2018
ms.topic: troubleshooting
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
monikerRange: vs-2017
ms.openlocfilehash: 4b5cf62dadc38802e477c7588416b4003304e852
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75584585"
---
# <a name="target-older-versions-of-net-f"></a>Kierowanie na starsze wersje platformy .NET (F#)

Następujący błąd może pojawić się podczas próby kierowania na program .NET Framework 2.0, 3.0 lub 3.5 w projekcie F# po zainstalowaniu programu Visual Studio w systemie Windows 8.1:

**Ten projekt wymaga środowiska wykonawczego 2.0 F#, ale to środowisko uruchomieniowe nie jest zainstalowane.**

Wiadomo, że ten błąd występuje w następujących warunkach:

- Program Visual Studio został zainstalowany w systemie Windows 8.1.

- Nie włączyłeś programu .NET Framework 3.5 przed zainstalowaniem programu Visual Studio.

- Projekt jest przeznaczony dla programu .NET Framework 2.0, 3.0 lub 3.5.

Po zainstalowaniu programu Visual Studio wykryje zainstalowane wersje programu .NET Framework. Program Visual Studio instaluje środowisko uruchomieniowe F# 2.0 tylko wtedy, gdy program .NET Framework 3.5 jest zainstalowany i włączony.

## <a name="resolve-the-error"></a>Rozwiąż błąd

Aby rozwiązać ten błąd, można:

- Kierowanie na nowszą wersję programu .NET Framework.

- Włącz program .NET Framework 3.5 w systemie Windows 8.1, a następnie zainstaluj środowisko wykonawcze F# 2.0, naprawiając instalację programu Visual Studio. Kroki, aby to zrobić, wykonaj następujące czynności.

### <a name="to-enable-the-net-framework-35-on-windows-81"></a>Aby włączyć program .NET Framework 3.5 w systemie Windows 8.1

1. Na ekranie **startowym** wpisz Polecenie **Panel sterowania**.

   Podczas pisania ikona **Panelu sterowania** pojawia się pod nagłówkiem **Aplikacje.**

2. Wybierz ikonę **Panel sterowania,** wybierz ikonę **Programy,** a następnie wybierz łącze **Włącz lub wyłącz funkcje systemu Windows.**

3. Upewnij się, że pole wyboru **.NET Framework 3.5 (w tym .NET 2.0 i 3.0)** jest zaznaczone, a następnie wybierz przycisk **OK.** Nie trzeba zaznaczać pól wyboru dla węzłów podrzędnych dla opcjonalnych składników programu .NET Framework.

   .NET Framework 3.5 jest włączona, jeśli jeszcze go nie było.

### <a name="to-install-the-f-20-runtime"></a>Aby zainstalować środowisko wykonawcze F# 2.0

Wykonaj [kroki, aby naprawić program Visual Studio](../install/repair-visual-studio.md).

## <a name="see-also"></a>Zobacz też

- [F# przewodnik (.NET Framework)](/dotnet/fsharp/)
- [Język F# w programie Visual Studio](fsharp-visual-studio.md)
